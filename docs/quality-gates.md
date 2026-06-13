# Quality Gates

Лёгкие проверки перед принятием изменения. Не превращать в бюрократию: если проект остаётся соло и без кода, достаточно README/CONTEXT/TODO/HerPlex.md согласованности.

## Для документации

- [ ] README/CONTEXT/TODO согласованы
- [ ] Нет broken links
- [ ] Нет секретов
- [ ] Commit message описывает изменение

## Для кода

Если появится код:

- [ ] tests
- [ ] typecheck
- [ ] lint
- [ ] build
- [ ] secret scan
- [ ] review

## Для критичных изменений

Требуют явного решения владельца:

- push;
- install dependencies;
- secrets;
- migrations;
- infra changes;
- public docs changes.

## Результат

Каждое изменение должно завершаться одним из статусов:

```text
accepted
rejected
blocked
needs-fix
```

## Отложить до реальной боли

- Формальный session log.
- Формальный recovery protocol.
- Продуктовая архитектура packages/cli/core/adapters.
