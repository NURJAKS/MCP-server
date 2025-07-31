# NIA MCP Server

![NIA MCP Server](/public/banner.png)

<div align="center">
  <strong>Intelligent Code Indexing, Search, and Research Platform</strong><br />
  <a href="https://twitter.com/kregenrek">
    <img src="https://img.shields.io/twitter/follow/kregenrek?style=social" alt="Follow @kregenrek on Twitter">
  </a>
</div>

**NIA MCP Server** - это интеллектуальная платформа для индексации, поиска и анализа кодовых баз и документации с использованием AI. Аналог Nia MCP сервера с полным набором инструментов для работы с репозиториями, документацией и веб-исследованиями.

---

<a href="https://glama.ai/mcp/servers/@your-org/nia-mcp-server">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@your-org/nia-mcp-server/badge" alt="NIA MCP server" />
</a>

## 🚀 Features

### 📂 **Repository Management**
- **`index_repository`** - Индексация GitHub репозиториев для интеллектуального поиска
- **`list_repositories`** - Список всех индексированных репозиториев со статусом
- **`check_repository_status`** - Мониторинг прогресса индексации
- **`delete_repository`** - Удаление индексированных репозиториев
- **`rename_repository`** - Переименование репозиториев для лучшей организации
- **`search_codebase`** - Поиск по коду с использованием естественного языка

### 📚 **Documentation Management**
- **`index_documentation`** - Индексация веб-сайтов и документации
- **`list_documentation`** - Список всех индексированных источников документации
- **`check_documentation_status`** - Мониторинг индексации документации
- **`delete_documentation`** - Удаление индексированной документации
- **`rename_documentation`** - Переименование источников документации
- **`search_documentation`** - Поиск по документации с использованием естественного языка

### 🔍 **Web Search & Research**
- **`nia_web_search`** - AI-поиск репозиториев, документации и контента
- **`nia_deep_research_agent`** - Глубокое многоэтапное исследование и анализ

### ⚙️ **Project Initialization**
- **`initialize_project`** - Настройка NIA-совместимых проектов с IDE-конфигурациями
- Поддержка Cursor, VS Code, Claude, Windsurf, Cline и других IDE
- Автоматическое создание IDE-специфичных правил и конфигураций

## 🏗️ Architecture

```
🧠 Core (Ядро)
├── 📂 src/core/indexer.ts - Индексация репозиториев и документации
├── 🔍 src/core/search.ts - Поисковая система
└── 🧬 src/core/embeddings.ts - Работа с эмбеддингами (планируется)

🧩 MCP Server
├── 📡 src/server.ts - Управление командами и API
├── 🛠️ src/tools/ - Все MCP инструменты
└── 🔧 src/index.ts - CLI интерфейс

🛢️ Storage (Хранилища)
├── 📊 src/storage/vector.ts - Векторная БД (планируется)
└── 💾 src/storage/cache.ts - Кэширование (планируется)

🕸️ Web Tools
├── 🌐 src/tools/web-search.ts - Веб-поиск и исследования
└── 🤖 src/agents/research.ts - Исследовательские агенты (планируется)
```

## 🛠️ Available Tools

### Repository Management Tools

#### `index_repository`
Индексация GitHub репозитория для интеллектуального поиска кода.

**Параметры:**
- `repo_url` (str): GitHub repository URL (например, https://github.com/owner/repo)
- `branch` (str, optional): Ветка для индексации (по умолчанию main)

**Использование:** После начала индексации используйте `check_repository_status` для мониторинга прогресса.

#### `list_repositories`
Список всех индексированных репозиториев со статусом.

**Параметры:** Нет

**Возвращает:** Список репозиториев со статусом, веткой и информацией об индексации.

#### `check_repository_status`
Проверка статуса индексации репозитория.

**Параметры:**
- `repository` (str): Репозиторий в формате owner/repo

**Возвращает:** Текущий статус, прогресс и детали индексации.

#### `delete_repository`
Удаление индексированного репозитория.

**Параметры:**
- `repository` (str): Репозиторий в формате owner/repo

**Возвращает:** Подтверждение удаления.

#### `rename_repository`
Переименование индексированного репозитория для лучшей организации.

**Параметры:**
- `repository` (str): Репозиторий в формате owner/repo
- `new_name` (str): Новое отображаемое имя (1-100 символов)

**Возвращает:** Подтверждение операции переименования.

#### `search_codebase`
Поиск по индексированным репозиториям с использованием естественного языка.

**Параметры:**
- `query` (str): Запрос поиска на естественном языке
- `repositories` (List[str], optional): Список репозиториев для поиска
- `include_sources` (bool, default=True): Включать ли исходный код в результаты

**Возвращает:** Результаты поиска с соответствующими фрагментами кода и объяснениями.

### Documentation Management Tools

#### `index_documentation`
Индексация документации или веб-сайта для интеллектуального поиска.

**Параметры:**
- `url` (str): URL документационного сайта для индексации
- `url_patterns` (List[str], optional): URL паттерны для включения в краулинг
- `max_age` (int, optional): Максимальный возраст кэшированного контента в секундах
- `only_main_content` (bool, default=True): Извлекать только основной контент

#### `list_documentation`
Список всех индексированных источников документации.

**Параметры:** Нет

**Возвращает:** Список источников документации со статусом и метаданными.

#### `check_documentation_status`
Проверка статуса индексации источника документации.

**Параметры:**
- `source_id` (str): ID источника документации

**Возвращает:** Текущий статус, прогресс и детали индексации.

#### `delete_documentation`
Удаление индексированного источника документации.

**Параметры:**
- `source_id` (str): ID источника документации для удаления

**Возвращает:** Подтверждение удаления.

#### `rename_documentation`
Переименование источника документации для лучшей организации.

**Параметры:**
- `source_id` (str): ID источника документации
- `new_name` (str): Новое отображаемое имя (1-100 символов)

**Возвращает:** Подтверждение операции переименования.

#### `search_documentation`
Поиск по индексированной документации с использованием естественного языка.

**Параметры:**
- `query` (str): Запрос поиска на естественном языке
- `sources` (List[str], optional): Список ID источников документации для поиска
- `include_sources` (bool, default=True): Включать ли ссылки на источники в результаты

**Возвращает:** Результаты поиска с соответствующими выдержками документации.

### Web Search & Research Tools

#### `nia_web_search`
Поиск репозиториев, документации и другого контента с использованием AI-поиска.

**Случаи использования:**
- Поиск конкретных репозиториев/документации/контента
- Поиск примеров или реализаций
- Поиск доступного контента по теме
- Простые, прямые поиски, требующие быстрых результатов
- Поиск похожего контента по известному URL

**Параметры:**
- `query` (str): Запрос поиска на естественном языке
- `num_results` (int, default=5): Количество результатов для возврата (макс: 10)
- `category` (str, optional): Фильтр по категории ("github", "company", "research paper", "news", "tweet", "pdf")
- `days_back` (int, optional): Показывать только результаты за последние N дней
- `find_similar_to` (str, optional): URL для поиска похожего контента

**Возвращает:** Результаты поиска с действенными следующими шагами.

#### `nia_deep_research_agent`
Выполнение глубокого, многоэтапного исследования темы с использованием продвинутых AI-возможностей исследования.

**Случаи использования:**
- Сравнение нескольких вариантов ("сравнить X vs Y vs Z")
- Анализ плюсов и минусов
- Вопросы с "лучший", "топ", "что лучше"
- Необходимость структурированного анализа или синтеза
- Сложные вопросы, требующие множественных источников
- Вопросы о трендах, паттернах или разработках
- Запросы на комплексные обзоры

**Параметры:**
- `query` (str): Исследовательский вопрос
- `output_format` (str, optional): Подсказка структуры (например, "comparison table", "pros and cons list")

**Возвращает:** Комплексные результаты исследования с цитированием.

### Project Initialization Tools

#### `initialize_project`
Инициализация NIA-совместимого проекта с IDE-специфичными правилами и конфигурациями.

**Параметры:**
- `project_root` (str): Абсолютный путь к корневой директории проекта
- `profiles` (List[str], optional): Список IDE профилей для настройки (по умолчанию: ["cursor"])

**Поддерживаемые профили:** cursor, vscode, claude, windsurf, cline, codex, zed, jetbrains, neovim, sublime

**Примеры:**
- Базовый: `initialize_project("/path/to/project")`
- Множественные IDE: `initialize_project("/path/to/project", profiles=["cursor", "vscode"])`
- Специфичная IDE: `initialize_project("/path/to/project", profiles=["windsurf"])`

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (>=18.0.0)
- MCP-совместимый клиент (например, [Cursor](https://cursor.com/))

### Installation

```bash
# Клонировать репозиторий
git clone https://github.com/your-org/nia-mcp-server.git
cd nia-mcp-server

# Установить зависимости
npm install

# Собрать проект
npm run build
```

### Usage

#### Local Development

```bash
# Запуск с stdio транспортом
npm run dev-stdio

# Запуск с HTTP транспортом
npm run dev-http

# Запуск с SSE транспортом (устаревший)
npm run dev-sse
```

#### Cursor Configuration

Добавьте в `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "nia-mcp-server": {
      "command": "node",
      "args": ["./bin/cli.mjs", "--stdio"]
    }
  }
}
```

#### Published Package

```bash
# Установить глобально
npm install -g @your-org/nia-mcp-server

# Запустить
nia-mcp-server --stdio
```

## 🔧 Development

### Project Structure

```
src/
├── core/           # Ядро системы
│   ├── indexer.ts  # Индексация репозиториев/документации
│   └── search.ts   # Поисковая система
├── tools/          # MCP инструменты
│   ├── repository.ts # Управление репозиториями
│   ├── documentation.ts # Управление документацией
│   ├── web-search.ts # Веб-поиск
│   └── project.ts  # Инициализация проектов
├── server.ts       # MCP сервер
├── index.ts        # CLI интерфейс
└── types.ts        # TypeScript типы
```

### Available Scripts

```bash
npm run build          # Собрать проект
npm run dev            # Разработка с nodemon
npm run dev-stdio      # Разработка с stdio транспортом
npm run dev-http       # Разработка с HTTP транспортом
npm run inspect        # Запустить MCP Inspector
npm run test           # Запустить тесты
npm run lint           # Проверить код
npm run lint:fix       # Исправить проблемы с кодом
```

## 📋 Tool Selection Guide

### Используйте `nia_web_search` для:
- "Найти RAG библиотеки" → Простой поиск
- "Что трендится в Rust?" → Быстрое обнаружение
- "Показать репозитории как LangChain" → Поиск по сходству

### Используйте `nia_deep_research_agent` для:
- "Сравнить RAG vs GraphRAG подходы" → Сравнительный анализ
- "Какие лучшие векторные БД для продакшена?" → Требуется оценка
- "Проанализировать плюсы и минусы разных LLM фреймворков" → Структурированный анализ

## 🤝 Contributing

1. Fork репозиторий
2. Создайте feature branch (`git checkout -b feature/amazing-feature`)
3. Commit изменения (`git commit -m 'Add amazing feature'`)
4. Push в branch (`git push origin feature/amazing-feature`)
5. Откройте Pull Request

## 📄 License

Этот проект лицензирован под MIT License - см. файл [LICENSE](LICENSE) для деталей.

---

## 🎓 Courses
- Learn to build software with AI: [instructa.ai](https://www.instructa.ai)
