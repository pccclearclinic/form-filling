
FROM python:3.11.4-slim-bookworm

RUN apt-get update \
    && apt-get install -y libpq-dev gcc \
    && apt-get clean

ENV PYTHONUNBUFFERED True

WORKDIR /app

COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

COPY . /app
CMD exec gunicorn --bind :$PORT --workers 1 --threads 8 --timeout 0 --reload formfillservice.flask_app:app
