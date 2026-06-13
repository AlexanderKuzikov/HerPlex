# Review Template

Используй этот шаблон для review от Perplexity или Hermes.

```md
# Review: [task / commit / PR]

## Context

Что проверяем.

## Verdict

- [ ] Accept
- [ ] Accept with minor changes
- [ ] Request changes
- [ ] Blocked

## Correctness

Что работает / что не работает.

## Edge cases

Непроверенные или рискованные сценарии.

## Security

- [ ] Нет секретов
- [ ] Нет path traversal
- [ ] Нет unsafe input handling
- [ ] Нет опасных side effects

## Architecture fit

Соответствие текущей архитектуре и ограничениям.

## Testing

Что покрыто и чего не хватает.

## Blocking issues

Критичные проблемы.

## Warnings

Проблемы, которые желательно исправить до merge/accept.

## Suggestions

Неблокирующие улучшения.

## Verified

Что было проверено явно.

## Not verified

Что не проверялось.

## Decision

Принятое решение и следующий шаг.
```
