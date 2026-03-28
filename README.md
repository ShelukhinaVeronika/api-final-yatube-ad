# Yatube API

API для социальной сети Yatube. Позволяет создавать посты, оставлять комментарии, подписываться на авторов.

## Описание

Проект представляет собой REST API для социальной сети Yatube. API позволяет:
- Создавать, редактировать и удалять посты
- Добавлять комментарии к постам
- Подписываться на других авторов
- Просматривать ленту постов

Документация API доступна после запуска проекта по адресу `/redoc/`.

## Установка

### Клонировать репозиторий и перейти в него в командной строке:
git clone https://github.com/ShelukhinaVeronika/api-final-yatube-ad.git

text
cd api-final-yatube-ad

text

### Создать и активировать виртуальное окружение:

Для Windows:
python -m venv venv

text
venv\Scripts\activate

text

Для Linux/macOS:
python3 -m venv venv

text
source venv/bin/activate

text

### Установить зависимости из файла requirements.txt:
python -m pip install --upgrade pip

text
pip install -r requirements.txt

text

### Выполнить миграции:
python manage.py migrate

text

### Создать суперпользователя (для доступа в админ-панель):
python manage.py createsuperuser

text

### Запустить проект:
python manage.py runserver

text

После запуска проекта документация будет доступна по адресу:
http://127.0.0.1:8000/redoc/

text

## Примеры запросов к API

### Получение JWT токена

POST `/api/token/`

```json
{
    "username": "your_username",
    "password": "your_password"
}
Ответ:

json
{
    "access": "eyJhbGciOiJIUzI1NiIs...",
    "refresh": "eyJhbGciOiJIUzI1NiIs..."
}
Получение списка постов
GET /api/posts/

Authorization: Bearer your_access_token

Создание поста
POST /api/posts/

Authorization: Bearer your_access_token

json
{
    "text": "Текст нового поста"
}
Получение списка комментариев к посту
GET /api/posts/{post_id}/comments/

Создание комментария
POST /api/posts/{post_id}/comments/

Authorization: Bearer your_access_token

json
{
    "text": "Текст комментария"
}
Подписка на автора
POST /api/follow/

Authorization: Bearer your_access_token

json
{
    "following": "author_username"
}
Получение списка подписок
GET /api/follow/

Authorization: Bearer your_access_token