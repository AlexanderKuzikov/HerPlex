# CONTEXT.md — HerPlex

> Дополнение к README.md. Содержит договорённости, детали реализации, историю решений.
> Обновляется после каждой сессии или задачи.
> При старте новой сессии: «прочитай CONTEXT.md».

---

## Режим работы

- Архитектура и ТЗ — Perplexity / Claude Sonnet 4.6 Thinking
- Реализация, рутина, фиксы — Hermes + Nex N2 Pro (лимит 1000 req/день)
- GitHub — шина передачи контекста между агентами (ссылки на файлы, коммиты, диффы)
- Perplexity имеет доступ к GitHub; Hermes имеет доступ к файловой системе, GitHub, почте
- Переключение между агентами — через тебя, ты остаёшься точкой принятия решений

## Правила Hermes

- Подробные правила в `AGENTS.md` — Hermes читает его автоматически
- Глобальный skill по формулировке задач: `~/.hermes/skills/dev/task-formulation/SKILL.md`
  (скопировать из `skills/task-formulation/SKILL.md`)
- `write_approval: true` в `~/.hermes/config.yaml` — контроль auto-generated skills
- `/plan` перед сложными задачами, `/stop` при зацикливании

## Правила Perplexity

- Подробная шпаргалка в `PERPLEXITY.md`
- Один запрос = одно решение или один review (не диалог в цикле)
- Передача контекста через URL: `github.com/AlexanderKuzikov/HerPlex/blob/main/[path]`
- Передача review через URL коммита: `github.com/AlexanderKuzikov/HerPlex/commit/[hash]`

## Триггеры переключения агентов

| Ситуация | Куда |
|---|---|
| Задача очевидна, scope ясен | Hermes напрямую |
| Задача нетривиальная, scope неясен | Perplexity → промпт → Hermes |
| Hermes завис > 3 итераций | Стоп → Perplexity с URL файла |
| Баг очевиден | Hermes напрямую |
| Финальный review критичной фичи | Perplexity с URL коммита |

## Структура задачи для Hermes

```
Task: [одна строка — что должно работать после]
Modify: [точные файлы]
Read for context: [файлы для чтения]
Acceptance criteria: [чеклист]
Do NOT: [явные запреты]
Stop after: [точка остановки]
```

## История решений

| Дата | Решение | Причина |
|---|---|---|
| 2026-06-14 | GitHub как шина контекста между агентами | Единственный общий инструмент, audit trail, no extra infra |
| 2026-06-14 | Без Issues/PR для соло-разработки | Оверинжиниринг для одного человека |
| 2026-06-14 | AGENTS.md + PERPLEXITY.md + CONTEXT.md | Минимальный набор для сохранения контекста между сессиями |
| 2026-06-14 | write_approval: true для Hermes skills | Контроль над auto-generated skills |

## Текущий статус

- [x] Базовая архитектура pipeline определена
- [x] AGENTS.md создан
- [x] PERPLEXITY.md создан
- [x] Skill task-formulation создан
- [ ] Скопировать skill в `~/.hermes/skills/dev/task-formulation/`
- [ ] Настроить `~/.hermes/config.yaml` (max_tool_calls, write_approval)
- [ ] Адаптировать AGENTS.md под конкретный проект
