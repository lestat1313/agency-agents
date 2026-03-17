# CLAUDE.md

Этот файл содержит инструкции для Claude Code при работе с данным репозиторием.

## Общие правила

- Всегда общаемся на русском языке
- Все файлы документации, предназначенные для пользователя, пишем на русском языке

## Обзор проекта

**The Agency** — коллекция 147+ специализированных AI-агентов, определённых как Markdown-файлы с YAML frontmatter. Агенты организованы по дивизионам (engineering, design, marketing, sales, product, testing, specialized, game-development и др.) и предназначены для использования с Claude Code, GitHub Copilot, Cursor, Windsurf и другими AI-инструментами.

Это контентный репозиторий, а не кодовая база — здесь нет рантайма, бэкенда или компилируемого кода.

## Структура репозитория

- `engineering/`, `design/`, `marketing/`, `sales/`, `product/`, `project-management/`, `testing/`, `support/`, `spatial-computing/`, `specialized/`, `game-development/`, `academic/`, `paid-media/` — файлы определений агентов (`.md`)
- `strategy/` — стратегические документы и плейбуки
- `examples/` — примеры мультиагентных воркфлоу
- `integrations/` — конфигурации интеграций с инструментами (claude-code, cursor, windsurf, aider и др.)
- `scripts/` — bash-скрипты для автоматизации
- `.github/workflows/lint-agents.yml` — CI-пайплайн

## Формат файлов агентов

Каждый агент — это Markdown-файл с обязательным YAML frontmatter:

```yaml
---
name: Agent Name
description: Short description
color: hex_color
---
```

Рекомендуемые секции в теле файла: **Identity**, **Core Mission**, **Critical Rules**. Минимальный объём: 50 слов.

## Линтер

Валидация структуры всех файлов агентов:

```bash
./scripts/lint-agents.sh
```

Проверяет:
- Наличие YAML frontmatter и обязательных полей (`name`, `description`, `color`)
- Рекомендуемые секции (Identity, Core Mission, Critical Rules) — только предупреждения
- Минимальную длину контента (50 слов)

CI автоматически запускает линтер при PR, изменяющих файлы агентов (`.github/workflows/lint-agents.yml`).

## Соглашения

- Имена файлов агентов: `division-role-name.md` (например, `engineering-frontend-developer.md`)
- Каждый агент — самодостаточный файл, без зависимостей между файлами
- Правила контрибуции описаны в `CONTRIBUTING.md`
- Сгенерированные файлы интеграций (в `integrations/`) находятся в `.gitignore` — не коммитить вручную
- Лицензия: MIT
