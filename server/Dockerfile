# Используем базовый образ Python 3.11
FROM python:3.11 AS server-base

# Виртуальное 
ENV PYTHONUNBUFFERED 1

# Обновим систему
RUN apt-get update -y

# Устанавливаем рабочую директорию внутри контейнера
WORKDIR /srv/server/

# Открываем порт, на котором будет работать приложение
EXPOSE 8000

# Копируем requirements 
COPY requirements.txt /srv/server/requirements.txt

# Устанавливаем зависимости
RUN pip install --no-cache-dir -r requirements.txt

# Копируем остальной код приложения
COPY . /srv/server/

FROM server-base AS server

# Определяем переменную окружения для Flask
ENV FLASK_APP=main.py

# Запускаем приложение
CMD ["flask", "run", "--host=0.0.0.0", "--port=8000"]