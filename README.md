# Телеграм бот с использованием Claude 3.7 Sonnet

Телеграм бот с системой кредитов, обработкой документов и поддержкой Claude 3.7 Sonnet API.

## Функциональность

- Общение с Claude 3.7 Sonnet API
- Система кредитов и их автоматическое восстановление
- Поддержка загрузки документов и изображений
- Административный интерфейс для управления пользователями
- Сохранение истории сообщений

## Требования

- Python 3.9+
- Установленные пакеты из requirements.txt

## Запуск бота в режиме 24/7 бесплатно на Render

1. Создайте аккаунт на [Render](https://render.com)
2. Создайте новый репозиторий на GitHub и загрузите туда код бота
3. В интерфейсе Render нажмите "New" и выберите "Web Service"
4. Свяжите репозиторий GitHub с Render
5. Настройте следующие параметры:
   - Name: `telegram-bot` (или любое другое имя)
   - Environment: `Python 3`
   - Build Command: `pip install -r requirements.txt`
   - Start Command: `python main.py`
   
6. В разделе "Environment Variables" добавьте:
   - `USE_WEBHOOK`: `true`
   - `APP_URL`: URL вашего сервиса (будет создан автоматически после деплоя)
   - `PORT`: `10000` (или любой другой порт, который предоставляет Render)

7. Нажмите "Create Web Service"

После первого деплоя вам нужно будет:
1. Скопировать URL вашего сервиса (например, `https://your-bot-name.onrender.com`)
2. Вернитесь в "Environment Variables" и обновите переменную `APP_URL` с этим URL
3. Нажмите "Manual Deploy" > "Clear build cache & deploy"

## Локальный запуск

1. Клонируйте репозиторий
2. Установите зависимости: `pip install -r requirements.txt`
3. Запустите бота: `python main.py`

## Административные команды

- `/start` - Начать взаимодействие с ботом
- "💰 Баланс" - Проверить текущий баланс кредитов
- "🔄 Сбросить историю" - Очистить историю сообщений
- "ℹ️ Помощь" - Показать справочную информацию
- "📊 Список пользователей" - (админ) Список всех пользователей
- "➕ Добавить кредиты" - (админ) Добавить кредиты пользователю
- "➖ Снять кредиты" - (админ) Снять кредиты с пользователя
- "🌟 Дать безлимит" - (админ) Дать безлимитный доступ пользователю
- "⭐ Убрать безлимит" - (админ) Убрать безлимитный доступ

## Особенности

- Общение с Claude 3.7 Sonnet
- Система кредитов для пользователей
- Анализ изображений
- Улучшенная обработка файлов (PDF, DOCX, TXT)
- Сохранение истории диалога (последние 10 сообщений)
- Разбивка больших сообщений на части для удобного чтения
- Административные функции (управление кредитами пользователей)
- Безлимитный режим для избранных пользователей
- Уведомления пользователей о действиях администратора
- Многопользовательская работа (обработка запросов от нескольких пользователей одновременно)

## Функции бота

### Разбивка длинных сообщений
Бот автоматически определяет запросы на большие тексты (рефераты, эссе, статьи) и разбивает ответы на удобные для чтения части.

### Обработка файлов
- Поддерживаемые форматы: PDF, DOCX, TXT
- Максимальный размер файла: 20 МБ
- Возможность добавления комментария к файлу в подписи
- Улучшенное определение типа файла (через несколько методов)
- Подробная обработка ошибок для работы с файлами
- Поддержка файлов без расширения (определение типа по содержимому)

### Система кредитов
- Новые пользователи получают 10 кредитов при регистрации
- Администратор может выдавать дополнительные кредиты или предоставлять безлимитный доступ

### Уведомления
Пользователи получают уведомления когда администратор:
- Добавляет кредиты
- Снимает кредиты
- Предоставляет или отменяет безлимитный доступ

## Известные ограничения
- **Автоматическое обновление кредитов** временно отключено из-за несовместимости с текущей версией библиотеки
- Для обновления кредитов пользователей администратор должен использовать команду `/add_credits`

## Решение проблем

### Windows
При возникновении ошибок с обработкой файлов в Windows:
- Убедитесь, что установлены библиотеки `python-magic-bin` и `filetype`
- Если проблемы с определением типа файла остаются, используйте файлы с корректным расширением (.pdf, .docx, .txt)

## Лицензия

MIT 