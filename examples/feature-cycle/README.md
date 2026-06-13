# Example Feature Cycle

Это пример минимального feature cycle для HerPlex.

## Цель

Показать, как одна идея проходит через pipeline от spec до review.

## Файлы

```text
examples/feature-cycle/
├── README.md
├── 01-spec.md
├── 02-prompt.md
├── 03-review.md
├── 04-implementation-summary.md
└── 05-commit.md
```

## Статус

Сейчас это placeholder. Его можно заполнить первым реальным примером после того, как Perplexity оценит `HerPlex.md`.

## Как использовать

1. Скопировать структуру.
2. Заполнить `architecture.md` и `spec.md`.
3. Передать `hermes-prompt.md` в Hermes.
4. После выполнения добавить `implementation-summary.md`.
5. Отправить `review.md` в Perplexity.
6. Зафиксировать решение владельца в `commit.md` или в `HerPlex.md`.
