# 01 Spec

Пример: первый реальный feature cycle HerPlex — `templates/review.md`.

## Goal

Сделать шаблон review полезным для Perplexity: Hermes должен получать понятную структуру для блокирующих проблем, предупреждений, предложений и проверенных фактов.

## Modify

- `templates/review.md`

## Read for context

- `PERPLEXITY.md`
- `CONTEXT.md`, раздел «Требования к комментариям»

## Acceptance criteria

- [ ] Файл содержит 5 явных блоков: Blocking issues, Warnings, Suggestions, Verified, Not verified
- [ ] Каждый блок содержит placeholder-пример заполнения
- [ ] В шапке есть поля: Коммит (URL), Дата, PR/Task
- [ ] Файл не больше 50 строк
- [ ] Не добавлены лишние разделы

## Do NOT

- Не трогать другие файлы
- Не менять роли Hermes / Perplexity / владельца
- Не расширять pipeline

## Stop after

`templates/review.md` обновлён и запушен в `main`.
