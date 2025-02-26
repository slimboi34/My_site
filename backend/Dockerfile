FROM python:3.11

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .

EXPOSE 8000

CMD ["sh", "-c", "echo 'Waiting for PostgreSQL...';while ! nc -z postgres_db 5432; do sleep 1; done;echo 'PostgreSQL started!'python manage.py migrate &&gunicorn myproject.wsgi:application --bind 0.0.0.0:8000"]