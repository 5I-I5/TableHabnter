# Telegram-бот для бронирования столов 📅🍽️

Этот проект — Telegram-бот для бронирования столиков в ресторане **Binary Bites**[^1].

## 🎥 Видео-демонстрация
<!--- 
Скачать видео с RuTube
https://video-saver.ru/

Конвертировать mp4 → gif 
https://ezgif.com/video-to-gif/
--->
[Смотреть на RuTube](https://rutube.ru/play/embed/12fae430858cc269c76f0faf00218106/)  
![FastAPI_Aiogram_Dialog_FastStream__RabbitMQ_-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/ab825def-85f8-4bc8-8414-6a8b8b17b3e9)


## 🚀 Возможности

- 📌 Выбор количества мест и конкретного стола
- 📆 Выбор даты и времени бронирования
- ✅ Подтверждение брони
- 📜 Просмотр и отмена бронирований
- ℹ️ Получение информации о ресторане
- 🔑 Админ-панель для управления бронированиями
- 📩 Отправка напоминаний и промокодов по расписанию

## 🏗️ Технологии

- **Aiogram 3**: лучший фреймворк для разработки телеграм-ботов на Python
- **Aiogram dialog 2.3**: фреймворк, который очень сильно упрощает работу с FSM в Aiogram 3
- **SQLAlchemy 2**: фреймворк для работы с табличными базами данных (демонстрацию покажу на примере SQLite, но можно будет легко переключить на любую другую табличную базу данных)
- **FastStream 0.5.3**: python-фреймворк для работы с брокерами сообщений (многие нарекают его «убийцей Celery»)
- **APScheduler 3.1**: фреймворк, который позволит удобно работать с отложенными задачами и задачами по расписанию
- **FastAPI**: фреймворк, который позволит всех этих ребят: телеграм-бота, APScheduler, FastStream и так далее объединить в рамках одного приложения (одной экосистемы)
- **Alembic**: для миграций базы данных
- **Uvicorn**: для запуска веб-сервера

## 🔧 Развертывание

> [!CAUTION]
> Инструкция сырая. Можте чего-нибудь еще нужно сделать. Миграции, например...

1. Создайте файл `.env` и запишите в него необходимые переменные
   ```.env
   BOT_TOKEN=bot_token # Получить у @BotFatherBot
   ADMIN_IDS=[admin_id1, admin_id2] # Вставьте свои id. Получить можно скинув себе в личку вот это  @get_id_bot
   INIT_DB=0
   BASE_URL=https://ngrok_url # Получить в NGROK или вставить свой
   RABBITMQ_USERNAME=admin
   RABBITMQ_PASSWORD=password
   RABBITMQ_HOST=127.0.0.1
   RABBITMQ_PORT=5672
   VHOST=myapp_vhost
   ```
   **BOT_TOKEN** – токен вашего Telegram-бота  
   **ADMIN_IDS** – список ID администраторов, имеющих доступ к управлению ботом.  
   **INIT_DB** – флаг для инициализации базы данных (далее подробнее разберем зачем он нужен).  
   **BASE_URL** – URL для работы Telegram Webhook. Можете сгенерить ssh тунель в ngrok или где-то еще. (Не забудьте его запустить)  
   **RABBITMQ_USERNAME / RABBITMQ_PASSWORD** – учетные данные для подключения к RabbitMQ.  
   **RABBITMQ_HOST / RABBITMQ_PORT** – параметры подключения к брокеру сообщений.  
   **VHOST** – виртуальный хост, используемый в RabbitMQ для изоляции задач.  

2. Запустите RabbitMQ. Например, с помощью Docker или через Amvera  
   Команды для запуска RabbitMQ через Docker  
   ```bash
   docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 \
      -e RABBITMQ_DEFAULT_USER=admin \
      -e RABBITMQ_DEFAULT_PASS=password \
      -e RABBITMQ_DEFAULT_VHOST=myapp_vhost \
      rabbitmq:3-management
   ```
3. Установите зависимости:
   ```bash
   pip install -r requirements.txt
   ```
4. Запуск миграций 
 
   Создаем миграцию:
   ```bash
   alembic revision --autogenerate -m "Initial revision"
   ```
   
   Применяем миграцию
   ```bash
   alembic upgrade head
   ```
5. Запустите приложение 
   ```bash
   uvicorn app.main:app --reload
   ``` 

> [!TIP]
> Совет — развертывайте через Amvera.
> 1. Сервис дает бонусом HTTPS доменное имя, которое так нужно для бота на webhook.
> 2. А еще на Amvera значительно проще развернуть проект, чем на локальной машине 


## ✅ Полезные ссылки 

🤙 Телеграм канал для обратной связи [«Легкий путь в Python»](https://t.me/PythonPathMaster/297)

🤖 Telegram-бот: [@tableHanterBot](https://t.me/tableHanterBot)

📖 О том, как разрабатывался этот бот, написана подробная статья:  [Читать на Хабре](https://habr.com/ru/companies/amvera/articles/882878/)

---

[^1]: **Binary Bites** - вымышленный ресторан.
