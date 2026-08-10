# HerPlex Pipeline

HerPlex — это pipeline для координации Hermes, Perplexity и владельца проекта. На текущем этапе это не продукт, а рабочий процесс для идей, ТЗ, реализации и review.

## Роли

| Роль | Ответственность |
|---|---|
| Perplexity / Claude Sonnet 4.6 | Архитектура, ТЗ, review, оценка идей |
| Hermes / Nex N2 Pro | Анализ, реализация, рутина, фиксы, документация |
| Владелец проекта | Принимает финальные решения и утверждает изменения |
| GitHub | Контекст, audit trail, канал между агентами |

## Прямой канал

Файл `HerPlex.md` — прямой канал Hermes ↔ Perplexity.

- Hermes пишет сюда оценки, риски, идеи, вопросы и предложения.
- Perplexity отвечает в блоке `## Ответ Perplexity`.
- Владелец принимает решение в блоке `## Решение владельца`.

## Полный цикл задачи

```text
0. Идея / проблема
1. Perplexity: архитектура и trade-offs
2. Perplexity: ТЗ / spec
3. Perplexity: промпт для Hermes
4. Hermes: реализация / документация
5. Hermes: локальные проверки
6. Perplexity: review
7. Hermes: фиксы, если нужны
8. Владелец: решение
9. Commit / next task
```

## Минимальный контракт задачи

Каждая задача должна иметь:

```text
Task:
Modify:
Read for context:
Acceptance criteria:
Do NOT:
Stop after:
```

Если задача затрагивает больше 3 файлов, больше 5 acceptance criteria или содержит архитектурную неопределённость — её нужно разбить или сначала отправить в Perplexity.

## Автономный режим

> **По умолчанию отключён.** Hermes работает только по явному заданию Perplexity или владельца. Включается только по явному решению владельца.

## Артефакты

Для каждой значимой задачи желательно сохранить:

```text
architecture.md
spec.md
prompt.md
implementation-summary.md
review.md
test-results.md
commit.md
```

На старте достаточно хранить хотя бы:

```text
spec.md
prompt.md
review.md
commit.md
```

## State machine

```text
draft → spec-ready → implementing → implemented → reviewed → accepted → done
                         ↓
                       blocked
```

## Quality gates

Для будущего кода:

- test;
- typecheck;
- lint;
- secret scan;
- build;
- review;
- commit message;
- human approval для критичных изменений.

## Recovery protocol

На старте не превращать recovery protocol в бюрократию. Использовать только при реальной проблеме:

1. Остановить текущий цикл.
2. Зафиксировать проблему в `HerPlex.md`.
3. Если проблема архитектурная — отправить в Perplexity.
4. Если проблема очевидная и локальная — Hermes может исправить.
5. Если действие критичное — ждать владельца.

Критичные действия:

- push;
- install dependencies;
- secrets;
- migrations;
- infra changes;
- public docs changes.

## Инциденты

### hello.md — 2026-06-14
- Задача: создать пустой временный `hello.md` на GitHub для проверки.
- Что пошло не так: Hermes раздул задачу до auth/Git/HerPlex/API-диагностики.
- Цена: ~12 минут и ~50 запросов на простой файл.
- Что изменили: владелец удалил файл; лишний HerPlex-отчёт откатан; добавлено правило остановки.
- Правило: если простая задача требует >5 шагов или >10 минут без прогресса — остановиться и спросить владельца.

## Отложить до реальной боли

Perplexity отметил, что на текущем этапе избыточны:

- session log с `session_id`, `started_at`, `tool_calls`;
- формальный recovery protocol;
- продуктовая архитектура `packages/cli/core/adapters`;
- human approval gates как отдельный процесс, если владелец и так де-факто принимает решения.
