# HerPlex — Agent Instructions

> Этот файл читается Hermes автоматически при каждой сессии.
> Не удалять. Не сокращать без ревью.

## Project
Пайплайн разработки: Hermes пишет код, Perplexity думает.

## Stack
- Runtime: Node.js 22 / TypeScript strict
- Framework: Express
- DB: Postgres + Drizzle ORM
- Validation: Zod
- Tests: vitest
- Style: tabs, ESM imports, no semicolons

## Behavior rules
- Если задача требует более 10 tool calls — ОСТАНОВИСЬ и задай уточняющий вопрос
- Если файл или значение не найдено за 3 попытки — сообщи об этом и остановись
- Никогда не устанавливай новые зависимости без явного разрешения
- Никогда не изменяй файлы вне scope задачи
- Предпочитай уточняющий вопрос предположению
- На простые вопросы отвечай напрямую — без tool calls
- Перед сложной задачей (>5 файлов) — напиши план и жди подтверждения

## Code rules
- Функции максимум 40 строк — если длиннее, разбить
- Запрещено `any` и `as`-casting без комментария с объяснением причины
- Validation: Zod-схемы только в `src/schemas/`
- DB queries: только через `src/db/queries/`
- Error handling: typed throws, не возвращать null
- Нет try/catch в handlers — есть global error middleware

## Comments policy
- Комментарий = ПОЧЕМУ, не ЧТО
- Хаки и workaround: обязательный комментарий с причиной
- TODO формат: `TODO(2026-06): описание`
- Без JSDoc на очевидные функции

## Do NOT (global)
- Не рефакторить код вне scope задачи
- Не добавлять логирование без явного запроса
- Не создавать абстракции, не запрошенные в задаче
- Не трогать файлы `AGENTS.md`, `PERPLEXITY.md` без явной команды
