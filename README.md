# HerPlex

Пайплайн разработки: Hermes пишет код, Perplexity думает.

## Структура

```
HerPlex/
├── AGENTS.md              ← правила для Hermes (читается автоматически)
├── PERPLEXITY.md          ← шпаргалка по работе с Perplexity
├── TODO.md                ← таск-лист
└── skills/
    └── task-formulation/
        └── SKILL.md       ← как формулировать задачи для Hermes
```

## Агенты

| Агент | Роль |
|---|---|
| Perplexity / Claude Sonnet 4.6 | Архитектура, ТЗ, code review |
| Hermes + Nex N2 Pro | Реализация, рутина, фиксы |

## Pipeline

```
1. [Perplexity] Архитектура + ТЗ
2. [Perplexity] Промпт для Hermes
3. [Hermes]     Реализация
4. [Ты]         Тесты
5a. Баг очевиден → [Hermes] фикс
5b. Архитектурные сомнения → [Perplexity] review → [Hermes] фикс
6. Финал
```
