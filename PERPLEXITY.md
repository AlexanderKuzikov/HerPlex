# HerPlex — Perplexity Cheatsheet

> Шпаргалка: когда и как использовать Perplexity в pipeline.
> Прямой канал Hermes ↔ Perplexity: [HerPlex.md](./HerPlex.md).

## Когда идти в Perplexity
- Архитектурное решение с trade-offs
- Задача нетривиальная и scope непонятен
- Hermes завис или зациклился (>3 итераций)
- Финальный review перед мержем критичной фичи
- Нужна актуальная информация (API, библиотеки, баги)

## Когда НЕ идти в Perplexity
- Задача очевидна и scope ясен → сразу Hermes
- Мелкий баг с понятным фиксом → сразу Hermes
- Boilerplate по существующему паттерну → сразу Hermes

## Формат запроса: архитектура
```
Контекст: [ссылка github.com/AlexanderKuzikov/HerPlex/blob/main/src/...]
Задача: что нужно реализовать
Constraints: что нельзя трогать
Вопрос: какой подход / какие trade-offs
```

## Формат запроса: review
```
[ссылка на коммит: github.com/AlexanderKuzikov/HerPlex/commit/HASH]
Review: correctness, edge cases, соответствие стеку
→ consolidated список замечаний одним ответом
```

## Прямой канал Hermes ↔ Perplexity

- Для живых оценок, вопросов и ответов использовать `HerPlex.md`.
- Hermes пишет в файл свои наблюдения и запросы.
- Perplexity отвечает в блоке `## Ответ Perplexity`.
- Финальные решения фиксирует владелец в блоке `## Решение владельца`.

## Формат запроса: промпт для Hermes
```
Задача: [что нужно сделать]
Файлы: [какие файлы затронуты]
Constraints: [что нельзя]
→ Perplexity выдаёт готовый промпт со stopping criteria
```

## Правило одного запроса
Perplexity используется для КОНСОЛИДИРОВАННОГО ответа, не для диалога.
Один запрос = одно решение или один review.
Не гоняй Perplexity в цикле — это роль Hermes.

## Ссылки для передачи контекста
```
Файл:    github.com/AlexanderKuzikov/HerPlex/blob/main/[path]
Коммит:  github.com/AlexanderKuzikov/HerPlex/commit/[hash]
Дифф:    github.com/AlexanderKuzikov/HerPlex/compare/[hash1]..[hash2]
Канал:   github.com/AlexanderKuzikov/HerPlex/blob/main/HerPlex.md
```
