# HerPlex

![Pipeline](https://img.shields.io/badge/pipeline-spec--driven-blue?style=flat-square)
![Hermes](https://img.shields.io/badge/agent-Hermes%20%2B%20Nex%20N2%20Pro-orange?style=flat-square)
![Perplexity](https://img.shields.io/badge/review-Claude%20Sonnet%204.6-8A2BE2?style=flat-square)
![Stack](https://img.shields.io/badge/stack-Node.js%20%7C%20TypeScript%20%7C%20PHP%20%7C%20Python-3178C6?style=flat-square)
![License](https://img.shields.io/github/license/AlexanderKuzikov/HerPlex?style=flat-square)

Пайплайн разработки: Hermes пишет код, Perplexity думает.

См. подробности: [CONTEXT.md](./CONTEXT.md)  
Прямой канал Hermes ↔ Perplexity: [HerPlex.md](./HerPlex.md)

## Агенты

| Агент | Роль |
|---|---|
| Perplexity / Claude Sonnet 4.6 | Архитектура, ТЗ, code review |
| Hermes + Nex N2 Pro | Реализация, рутина, фиксы |

## Pipeline

```
0. [HerPlex.md]  Прямой канал Hermes ↔ Perplexity для оценок, вопросов и решений
1. [Perplexity] Архитектура + ТЗ
2. [Perplexity] Промпт для Hermes
3. [Hermes]     Реализация
4. [Ты]         Тесты
5a. Баг очевиден → [Hermes] фикс
5b. Архитектурные сомнения → [Perplexity] review → [Hermes] фикс
6. Финал
```

## Структура репо

```
HerPlex/
├── HerPlex.md             ← прямой канал Hermes ↔ Perplexity
├── AGENTS.md              ← правила для Hermes (читается автоматически)
├── PERPLEXITY.md          ← шпаргалка по работе с Perplexity
├── CONTEXT.md             ← договорённости, история решений, детали
├── TODO.md                ← таск-лист
└── skills/
    └── task-formulation/
        └── SKILL.md       ← как формулировать задачи для Hermes
```
