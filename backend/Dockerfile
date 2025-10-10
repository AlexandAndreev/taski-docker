FROM python:3.10

WORKDIR /app

# системные/внешние зависимости до копирования кода
RUN pip install gunicorn==23.0.0

# зависимости приложения
COPY requirements.txt .
RUN pip install -r requirements.txt --no-cache-dir

# сам проект
COPY . .

# gunicorn слушает 0.0.0.0:8000 и грузит WSGI-приложение из backend.wsgi
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]