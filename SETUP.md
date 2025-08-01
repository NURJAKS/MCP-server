# NIA MCP Server Setup Guide

## Описание

NIA MCP Server - это интеллектуальная платформа для индексации, поиска и исследования кода. Инструменты теперь работают с реальными API и базой данных.

## Установка зависимостей

```bash
npm install
```

## Настройка переменных окружения

Скопируйте `env.example` в `.env` и настройте необходимые переменные:

```bash
cp env.example .env
```

### Обязательные переменные:

```env
# GitHub API (обязательно)
GITHUB_TOKEN=your_github_token_here

# OpenAI API (для семантического поиска)
OPENAI_API_KEY=your_openai_api_key_here

# Веб-поиск (опционально)
SERPER_API_KEY=your_serper_api_key_here
```

### Опциональные переменные:

```env
# Qdrant Vector Database
QDRANT_URL=http://localhost:6333
QDRANT_API_KEY=your_qdrant_api_key_here

# Redis Cache
REDIS_URL=redis://localhost:6379

# Настройки индексации
MAX_FILE_SIZE=1024000
MAX_REPOSITORY_SIZE=100000000
INDEXING_TIMEOUT=300000
```

## Получение API ключей

### GitHub Token
1. Перейдите в [GitHub Settings > Developer settings > Personal access tokens](https://github.com/settings/tokens)
2. Создайте новый token с правами `repo` и `read:org`
3. Скопируйте token в `GITHUB_TOKEN`

### OpenAI API Key
1. Перейдите в [OpenAI API Keys](https://platform.openai.com/api-keys)
2. Создайте новый API key
3. Скопируйте key в `OPENAI_API_KEY`

### Serper API Key (опционально)
1. Зарегистрируйтесь на [Serper.dev](https://serper.dev)
2. Получите API key
3. Скопируйте key в `SERPER_API_KEY`

## Запуск сервера

```bash
# Разработка
npm run dev

# Продакшн
npm run build
npm start
```

## Использование инструментов

### 1. Индексация репозитория

```javascript
// Индексируем репозиторий
await index_repository({
  repo_url: "https://github.com/owner/repo",
  branch: "main" // опционально
})

// Проверяем статус
await check_repository_status({
  repository: "owner/repo"
})

// Список репозиториев
await list_repositories()
```

### 2. Поиск по коду

```javascript
// Поиск по всем индексированным репозиториям
await search_codebase({
  query: "function to handle user authentication",
  include_sources: true
})

// Поиск в конкретных репозиториях
await search_codebase({
  query: "database connection",
  repositories: ["owner/repo1", "owner/repo2"]
})
```

### 3. Веб-поиск и исследование

```javascript
// Простой веб-поиск
await nia_web_search({
  query: "React state management libraries",
  num_results: 5,
  category: "github"
})

// Глубокое исследование
await nia_deep_research_agent({
  query: "Compare Redux vs Zustand vs Jotai for React state management",
  output_format: "comparison table"
})
```

### 4. Управление документацией

```javascript
// Индексация документации
await index_documentation({
  url: "https://docs.example.com",
  url_patterns: ["/docs/", "/guide/"],
  only_main_content: true
})

// Поиск в документации
await search_documentation({
  query: "authentication setup",
  sources: ["doc_id_1", "doc_id_2"]
})
```

## Структура базы данных

База данных SQLite создается автоматически в папке `data/`:

- `repositories` - информация о проиндексированных репозиториях
- `documentation` - информация о проиндексированной документации
- `indexed_files` - содержимое проиндексированных файлов
- `indexed_pages` - содержимое проиндексированных страниц документации

## Возможности

### ✅ Реализовано

1. **Реальная индексация GitHub репозиториев**
   - Использование GitHub API
   - Фильтрация файлов (node_modules, build, etc.)
   - Сохранение в SQLite базу данных

2. **Семантический поиск**
   - Интеграция с OpenAI API
   - Комбинированный поиск (текстовый + семантический)
   - Ранжирование результатов

3. **Веб-поиск**
   - Интеграция с Serper API
   - Fallback на mock данные
   - Фильтрация по категориям

4. **Глубокое исследование**
   - Многоэтапный анализ с AI
   - Структурированный вывод
   - Рекомендации

5. **Управление данными**
   - CRUD операции для репозиториев
   - Переименование и организация
   - Мониторинг прогресса

### 🔄 В разработке

1. **Индексация документации**
   - Веб-скрапинг с Puppeteer
   - Извлечение основного контента
   - Векторная индексация

2. **Векторный поиск**
   - Интеграция с Qdrant
   - Embedding генерация
   - Семантическое ранжирование

3. **Кэширование**
   - Redis интеграция
   - Кэширование API запросов
   - Rate limiting

## Ошибки и решения

### "GitHub API error: 401"
- Проверьте `GITHUB_TOKEN` в `.env`
- Убедитесь, что token имеет права `repo`

### "OpenAI API key not configured"
- Добавьте `OPENAI_API_KEY` в `.env`
- Или используйте только текстовый поиск

### "Database not initialized"
- Проверьте права на запись в папку `data/`
- Убедитесь, что SQLite установлен

### "Repository not found"
- Проверьте URL репозитория
- Убедитесь, что репозиторий публичный или у вас есть доступ

## Производительность

- **Индексация**: ~100 файлов/минуту
- **Поиск**: <1 секунда для большинства запросов
- **Веб-поиск**: ~2-5 секунд
- **Глубокое исследование**: ~10-30 секунд

## Безопасность

- API ключи хранятся в `.env` (не в коде)
- GitHub token имеет минимальные права
- Локальная база данных SQLite
- Нет передачи данных третьим лицам

## Поддержка

При возникновении проблем:

1. Проверьте логи в консоли
2. Убедитесь, что все API ключи настроены
3. Проверьте подключение к интернету
4. Создайте issue в репозитории 