# 🌐 Django Blog Platform 🚀

## 📝 Описание

`Django Blog Platform` — это современная блог-платформа, объединяющая мощь Django на бэкенде и Vue.js на фронтенде. Проект использует кеширование через Redis, поиск по контенту с помощью Elasticsearch, и настроен для мониторинга с Grafana + Prometheus. Всё это собрано и управляется через Docker Compose. 🐳

## 🔧 Основные технологии

- **Django + DRF** — бэкенд фреймворк 🐍
- **Vue.js** — фронтенд на JavaScript 🎨
- **Redis** — кеширование данных для ускорения работы ⚡️
- **Elasticsearch** — мощный поиск 🔍
- **Grafana + Prometheus** — мониторинг и метрики 📊
- **PostgreSQL** — база данных 🗄️
- **Docker Compose** — контейнеризация и управление сервисами 🐋

## ⚙️ Функциональные возможности

- 📝 **Посты** — создание, редактирование и удаление блог-постов
- 💬 **Комментарии** — система комментариев к постам
- 🏷️ **Теги и категории** — удобная категоризация и тегирование контента
- 🔍 **Поиск** — полнотекстовый поиск по контенту на базе Elasticsearch
- 📦 **Кеширование** — ускорение приложения с помощью Redis
- 📊 **Мониторинг** — реальное время наблюдения за приложением с помощью Grafana и Prometheus

## 🚀 Быстрый старт

1. Клонируй репозиторий:

```bash
git clone https://github.com/light-hat/blog_platform.git
```

2. Собери и запусти проект через Docker Compose:

```bash
docker-compose up -d --build
```

3. Открой браузер и перейди на `http://localhost:8000/` 🎉

## 🗂️ Django админка

Проект включает `Django Admin`, который позволяет удобно управлять контентом (постами, комментариями, тегами и категориями) через встроенную административную панель.

- **Адрес админки**: `http://localhost:8000/admin`

- **Создание суперпользователя**: При развёртывании системы автоматически создаётся суперпользователь с учётными данными:

  + Логин: `admin`
  + Пароль: `admin`

> ⚠️ **Важно! Настоятельно рекомендуется сменить пароль суперпользователя сразу после запуска системы для обеспечения безопасности.**

- Основные возможности админки:

  + Управление блог-постами и их содержанием
  + Управление категориями и тегами
  + Модерация комментариев пользователей
  + Полный CRUD-интерфейс для всех сущностей проекта

## 📝 Требования к коду для бэкенда

Для поддержания качества и читаемости кода в этом проекте используются следующие требования:

**Стиль кода**

- 📜 **Соблюдение стиля Django**: Следуйте стилю кода, рекомендуемому в официальной документации Django.
- 🔍 **Flake8**: Настройте IDE для использования flake8 для проверки кода на соответствие стандартам.

  + Для ручной проверки кода используйте:
  
  ```bash
  cd src && flake8
  ```
  
- 🌍 **Английский язык**: Используйте английский язык в комментариях и сообщениях коммитов.
- 🔗 **Сообщения коммитов**: Сообщения коммитов должны содержать уникальный ID задачи, к которой они относятся (например, refs #100500).
- 📄 **Docstrings**: Каждая модель и метод модели должны иметь docstring для описания их назначения и использования.

**Организация кода**

- 💡 **KISS и DRY**: Придерживайтесь принципов Keep It Simple, Stupid и Don't Repeat Yourself.
- 📚 **Лучшие практики Django**: Используйте лучшие практики Django для структурирования кода.
- 🛠️ **Сервисы для бизнес-логики**: Если нужно реализовать бизнес-логику, создайте отдельный сервис для этого. Примеры: UserCreator, OrderCreator.

> Бизнес-логика не должна находиться в представлениях или шаблонах — только в сервисах и моделях.

- 📋 **Типы данных**: Используйте подсказки типов PEP-484 при написании кода (например, -> str, -> None).
- 👥 **Manager методы**: Предпочитайте методы менеджера (Manager) вместо статических методов.
- 🚫 **Signals**: Не используйте сигналы для бизнес-логики. Они подходят только для уведомлений.
- 🌐 **Локализация**: Локализация должна выполняться через Django, не используйте l10n в коде Python.

## 📚 Документация API

API доступно по адресу `/swagger/` и автоматически генерируется с помощью **Swagger**. Используй это для тестирования и интеграции с фронтэндом. 📖

## 📈 Мониторинг

Мониторинг настроен через **Grafana** и **Prometheus**. После запуска Docker контейнеров, ты сможешь отслеживать метрики приложения через Grafana по адресу `http://localhost:3000`. 🎯

## 🛠️ Разработка

- Фронтенд расположен в директории `frontend/` и разработан на **Vue.js**.
- Бэкенд построен на **Django + DRF** и поддерживает API для работы с постами, комментариями и категориями.
- Вся система интегрирована через **Docker Compose**, что упрощает развертывание и управление зависимостями.

## 🤝 Вклад

Буду рад любому вкладу! Открывай issues, делай pull requests, обсуждай и предлагай идеи. 🙌

## 📝 Лицензия

Проект доступен под лицензией MIT. Разработчики и контрибьюторы приветствуются! 😄
