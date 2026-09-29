FROM python:3.10-alpine3.17

ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /app

COPY Pipfile Pipfile.lock ./

RUN apk add --no-cache \
    gcc \
    musl-dev \
    linux-headers \
    && pip install --no-cache-dir pipenv \
    && pipenv install --system --deploy \
    && apk del gcc musl-dev linux-headers

COPY . .

EXPOSE 5000

CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]
