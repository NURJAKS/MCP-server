# 🚀 Установка NIA MCP Server

## 📦 Быстрая установка (рекомендуемый)

### **1. Установите глобально:**
```bash
npm install -g @your-org/nia-mcp-server
```

### **2. Настройте автоматически:**
```bash
# Без API ключа (для начала работы)
nia-mcp setup

# С API ключом (для расширенного функционала)
nia-mcp setup YOUR_API_KEY
```

**Готово!** MCP сервер автоматически настроен для Cursor.

### **3. Проверьте установку:**
```bash
nia-mcp status
```

---

## 🎯 Что делает setup команда

Автоматически создает:

✅ **Глобальную конфигурацию** - `~/.cursor/mcp.json`
✅ **Локальную конфигурацию** - `.cursor/mcp.json`
✅ **Обновляет .gitignore** - защищает конфигурации
✅ **Создает NIA_SETUP.md** - руководство по использованию
✅ **Настраивает API ключи** - если предоставлены

---

## 🚀 Использование

После установки попробуйте в Cursor Chat:

```bash
# Индексация репозитория
index_repository(repo_url: "https://github.com/NURJAKS/Todo-list")

# Поиск в коде
search_codebase(query: "authentication logic")

# Веб-поиск
nia_web_search(query: "React hooks best practices")
```

---

## 🔧 Команды

```bash
# Настройка (без API ключа)
nia-mcp setup

# Настройка (с API ключом)
nia-mcp setup YOUR_API_KEY

# Проверка статуса
nia-mcp status

# Справка
nia-mcp --help

# Запуск сервера
nia-mcp
```

---

## 🆚 Сравнение с оригинальным Nia

| Аспект | Оригинальный Nia | Наш NIA MCP Server |
|--------|------------------|-------------------|
| **Установка** | `pipx install nia-mcp-server` | `npm install -g @your-org/nia-mcp-server` |
| **Команда** | `nia-mcp-server` | `nia-mcp` |
| **Настройка** | `pipx run nia-mcp-server setup KEY` | `nia-mcp setup [KEY]` |
| **API ключ** | Обязательный | Опциональный |
| **Проверка** | Ручная | `nia-mcp status` |
| **Автоматизация** | ✅ | ✅ |
| **Документация** | Ручная | Автоматическая |
| **Простота** | Отличная | Отличная |

**Наш подход еще проще для пользователей!** 🚀
