---
name: task-formulation
description: Как формулировать эффективные промпты для Hermes чтобы избежать agentic spirals
metadata:
  hermes:
    tags: [workflow, prompting, efficiency]
    category: dev
---

# Task Formulation Rules

## Структура хорошего промпта

```
1. ONE конкретная цель (не "разберись с X")
2. Точные файлы для изменения
3. Точные файлы для чтения как контекст
4. Acceptance criteria чеклистом
5. Явный раздел Do NOT
6. Stopping criteria
```

## Шаблон

```
Task: [одна строка — что должно работать после]

Modify:
- src/api/[file].ts — [что изменить]

Read for context:
- src/db/schema.ts

Acceptance criteria:
- [ ] [конкретное поведение]
- [ ] [edge case]

Do NOT:
- Не менять [интерфейс/схему/другой файл]
- Не добавлять [зависимость/логирование]

Stop after: [точная точка остановки]
```

## Простые вопросы — без tool calls

```
✓ "Read .env, return PORT value"
✓ "What does getProducts() return? src/db/queries/products.ts line 12"
✗ "Найди порт сервера"           ← слишком размыто, запускает поиск
✗ "Разберись с ошибкой"          ← нет scope, нет файла
```

## Правило размера задачи

Одна задача = одно логическое изменение = один коммит.

Разбить если:
- Затрагивает более 3 файлов
- Более 5 acceptance criteria
- Есть архитектурная неопределённость

## Stopping criteria (всегда для сложных задач)

```
"Stop after completing X, do not proceed to Y"
"If you cannot find Z in 3 attempts — report and stop"
"Do not modify any file not listed above"
```

## Если Hermes зациклился

```
/stop                              # немедленная остановка
/plan                              # покажи план ДО выполнения
"Wait. Answer only, no tool calls needed."
"Stop. Report what you found so far."
```
