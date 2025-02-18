# Telegram-бот для бронирования столов 📅🍽️

Этот проект — Telegram-бот для бронирования столиков в ресторане **Binary Bites**.

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

- **Python 3**
- **Aiogram 3** — фреймворк для разработки Telegram-ботов
- **Aiogram Dialog 2.3** — фрэймворк для удобной работы с Aiogram FSM
- **FastAPI** — для backend API
- **RabbitMQ + FastStream** — для обработки сообщений
- **SQLAlchemy 2** — для работы с базой данных
- **APScheduler** — для задач по расписанию

## 🔧 Развертывание

1. Установите зависимости:
   ```bash
   pip install -r requirements.txt
   ```

2. Запуск бота:
   ```bash
   python -m bot.main
   ```

> [!Note]  
> **Binary Bites** - вымышленный ресторан для программистов, любящих свое дело.

## ✅ Полезные ссылки 

🤙 Телеграм канал для обратной связи [«Легкий путь в Python»](https://t.me/PythonPathMaster/297)

🤖 Telegram-бот: [@tableHanterBot](https://t.me/tableHanterBot)

📖 О том, как разрабатывался этот бот, написана подробная статья:  [Читать на Хабре](https://habr.com/ru/companies/amvera/articles/882878/)
