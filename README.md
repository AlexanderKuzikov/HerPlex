# HerPlex

> Multi-agent workflow: Perplexity × Hermes × Human

[![methodology](https://img.shields.io/badge/type-methodology-blue)](https://github.com/AlexanderKuzikov/HerPlex)
[![status](https://img.shields.io/badge/status-active-brightgreen)](https://github.com/AlexanderKuzikov/HerPlex)
[![agents](https://img.shields.io/badge/agents-Perplexity%20%2B%20Hermes-purple)](https://github.com/AlexanderKuzikov/HerPlex)

HerPlex — методология асинхронной multi-agent разработки. Три участника работают асинхронно через GitHub — каждый в своей роли, без постоянного присутствия друг друга.

## Участники

| Роль | Инструмент | Функция |
|------|------------|----------|
| Архитектор | Perplexity / Claude Sonnet | ТЗ, архитектура, review, формулировка заданий |
| Исполнитель | Hermes / Nex N2 Pro | Реализация, документация, рутина |
| Decision point | Владелец проекта | Принятие финальных решений |
| Шина | GitHub | Общая память, audit trail, асинхронный канал |

## Канал связи

[HerPlex.md](./HerPlex.md) — прямой канал Hermes ↔ Perplexity. Все задания, отчёты и решения хранятся здесь.

## Структура

```
docs/
  pipeline.md          — полный цикл задачи
  agent-contract.md    — контракт ролей
  quality-gates.md     — проверки перед принятием
  new-project.md       — инструкция запуска нового проекта
templates/
  task.md              — шаблон задания для Hermes
  review.md            — шаблон review для Perplexity
examples/
  feature-cycle/       — пример полного цикла
```

## Быстрый старт нового проекта

См. [docs/new-project.md](./docs/new-project.md)
