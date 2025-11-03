# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Принципы работы

- Делать ТОЛЬКО то, что просит пользователь
- Не добавлять лишний текст, примечания, дополнительные разделы
- Не создавать тонны ненужного контента
- Минимализм и только по запросу

## О проекте

Это проект документации для Formula Student Electric - подробная смета и спецификации для разработки электрического гоночного болида. Документация создана с использованием Sphinx и написана на reStructuredText (.rst).

## Структура проекта

```
source/              # Исходники документации в формате .rst
├── index.rst        # Главная страница
├── conf.py          # Конфигурация Sphinx
├── safety/          # Документация по безопасности (BSPD, IMD, shutdown circuit, TSAL)
├── charger/         # Документация по зарядным устройствам
├── tools/           # Документация по инструментам
└── useful_links.rst # Полезные ссылки

build/html/          # Собранная HTML документация (не в git)
```

## Команды для работы

### Сборка документации
```bash
make html
```
Собирает HTML документацию в `build/html/`. Автоматически создает `.nojekyll` файл для GitHub Pages.

### Просмотр документации
```bash
open build/html/index.html
```

### Очистка собранной документации
```bash
make clean
```

### Другие форматы сборки
```bash
make help           # Показать все доступные команды Sphinx
make latexpdf       # PDF через LaTeX
make epub           # EPUB формат
```

## Архитектура документации

### Sphinx конфигурация (source/conf.py)
- Проект: Formula Student Documentation
- Тема: sphinx_rtd_theme (Read the Docs)
- Включенные расширения: autodoc, viewcode, todo
- Язык: английский (интерфейс), русский (контент)

### Формат reStructuredText
Все документы используют .rst формат. Основные элементы:

```rst
Заголовок первого уровня
========================

Заголовок второго уровня
------------------------

.. note::
   Заметка

.. warning::
   Предупреждение

.. list-table:: Таблица
   :header-rows: 1
   :widths: 25 25 25 25

   * - Колонка 1
     - Колонка 2
```

### Структура разделов безопасности
- `safety/bspd/` - Brake System Plausibility Device
- `safety/imd/` - Insulation Monitoring Device
- `safety/shutdown_circuit/` - Цепи аварийного отключения
- `safety/tsal/` - Tractive System Active Light

Каждый раздел содержит `.rst` файлы с документацией, подпапки `images/` для изображений и `datasheets/` для технических спецификаций.

## CI/CD

GitHub Actions автоматически собирает и деплоит документацию при пуше в `main`:
- Устанавливает Python 3.11
- Устанавливает sphinx и sphinx-rtd-theme
- Собирает HTML с помощью `make html`
- Деплоит в ветку `gh-pages`

Документация доступна через GitHub Pages.

## Зависимости

- Python 3.11+
- sphinx >= 8.0
- sphinx-rtd-theme

Установка:
```bash
pip install sphinx sphinx-rtd-theme
```
