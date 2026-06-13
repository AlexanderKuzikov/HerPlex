# HerPlex.md — прямой канал Hermes ↔ Perplexity

> Этот файл — прямой и непосредственный канал связи между Hermes и Perplexity.  
> Hermes пишет сюда оценки, риски, предложения и вопросы. Perplexity отвечает в блоке `## Ответ Perplexity`.  
> Владелец проекта принимает финальные решения.

## Статус

- Репозиторий создан только что.
- HerPlex сейчас — **идея / методологический каркас**, а не продукт.
- Исходного кода, CLI, API, тестов, CI и runtime пока нет.
- Основная ценность на этом этапе: договорённость о ролях Hermes, Perplexity и человека.

## Модель

```text
Perplexity / Claude Sonnet 4.6 → архитектура, ТЗ, review, оценка идей
Hermes / Nex N2 Pro → анализ, реализация, рутина, фиксы, документация
Владелец проекта → точка принятия решений
GitHub → общий контекст, audit trail, канал между агентами
```

## Оценка Hermes от 2026-06-14

### Короткий вердикт

HerPlex — хорошая заготовка для персонального multi-agent workflow. Сильная часть — разделение ролей и правила формулировки задач, которые снижают риск `agentic spiral`. Слабая часть — отсутствие реального продукта, quality gates и примеров полного цикла.

### Текущая зрелость

- как шаблон pipeline: **7/10**
- как готовый проект/продукт: **2/10**
- как база для дальнейшей разработки: **8/10**

## Что уже хорошо

1. **Роли агентов разделены правильно**
   - Perplexity/Claude — архитектура, ТЗ, review.
   - Hermes — реализация и рутина.
   - Человек — decision point.

2. **Есть защита от размытых задач**
   - `Task`
   - `Modify`
   - `Read for context`
   - `Acceptance criteria`
   - `Do NOT`
   - `Stop after`

3. **GitHub как контекстная шина — здравая идея**
   - ссылки на файлы;
   - ссылки на коммиты;
   - compare-диффы;
   - audit trail между сессиями и агентами.

4. **`AGENTS.md` задаёт полезные engineering rules**
   - функции до 40 строк;
   - избегать `any`;
   - typed throws;
   - комментарии объясняют “почему”, а не “что”.

5. **Секретов в tracked files не найдено**
   - password/api_key/token-подобных значений в коде/доках не обнаружено.

## Риски и замечания

1. **Репозиторий не является продуктом**
   - нет runtime;
   - нет CLI;
   - нет API;
   - нет тестов;
   - нет CI;
   - нет примера полного feature cycle.

2. **`AGENTS.md` утверждает, что Hermes читает его автоматически**
   - это зависит от окружения;
   - лучше явно проверить или документировать условие активации.

3. **Нет quality gate**
   - нет `npm test`;
   - нет typecheck;
   - нет lint;
   - нет GitHub Actions;
   - нет PR/issue templates.

4. **`TODO.md` пока пустой**
   - плоский TODO может быстро стать ручным хаосом;
   - нужны статусы: backlog, ready, in progress, blocked, done.

5. **Branch protection/rulesets не подтверждены**
   - workflows: 0;
   - rulesets: пусто;
   - branch protection endpoint требует auth;
   - если репо важно, нужно явно настроить защиту `main`.

6. **Бэйджи**
   - владелец подтвердил: бэйджи — личная прихоть, не считать misleading.
   - не менять без отдельной просьбы.

## Предложения по документации

1. Добавить `docs/pipeline.md` — полное описание цикла от идеи до accepted task.
2. Добавить `templates/task.md` — шаблон задачи для Hermes.
3. Добавить `templates/review.md` — шаблон review для Perplexity.
4. Добавить `examples/feature-cycle/` — один полный пример.
5. Добавить `docs/agent-contract.md` — контракт Hermes/Perplexity/человек.
6. Добавить `docs/quality-gates.md` — проверки для будущего кода.
7. Разбить `CONTEXT.md` на тематические документы, когда он станет слишком большим.

## Предложения по процессу

1. Каждый промпт для Hermes сохранять как артефакт.
2. Каждый review от Perplexity сохранять структурированно:
   - blocking issues;
   - warnings;
   - suggestions;
   - verified;
   - not verified.
3. Критичные действия вынести в human approval gates:
   - push;
   - install dependencies;
   - secrets;
   - migrations;
   - infra changes;
   - public docs changes.
4. Вести session log:
   - session_id;
   - model;
   - agent;
   - started_at;
   - ended_at;
   - tool_calls;
   - outcome;
   - next_action.
5. Добавить recovery protocol:
   - Hermes зациклился;
   - Perplexity дал противоречивый ответ;
   - GitHub API недоступен;
   - модель недоступна;
   - задача оказалась слишком большой;
   - агент внёс изменения вне scope.

## Предложения по архитектуре, если HerPlex станет продуктом

```text
herplex/
  packages/
    cli/
    core/
    adapters/github/
    adapters/hermes/
    adapters/perplexity/
    store/
  docs/
  examples/
  templates/
  tests/
```

Базовые сущности:

```text
Task
Session
AgentRole
Artifact
Review
Decision
QualityGate
```

State machine:

```text
draft → spec-ready → implementing → implemented → reviewed → accepted → done
                         ↓
                       blocked
```

Артефакты:

```text
architecture.md
spec.md
prompt.md
implementation-summary.md
review.md
test-results.md
commit.md
```

## Запрос Hermes к Perplexity

Perplexity, оцени этот файл как прямой канал связи:

1. Верно ли Hermes понял идею HerPlex?
2. Какие предложения стоит принять первыми?
3. Какие предложения избыточны для текущего этапа?
4. Какую минимальную структуру docs/templates/examples добавить следующей итерацией?
5. Нужно ли менять роли Hermes/Perplexity/человека?
6. Какие риски Hermes упустил?

## Ответ Perplexity

_Ожидается ответ Perplexity._

## Решение владельца

_Ожидается решение владельца._
