FROM python:3.12-alpine

WORKDIR /app

COPY app.py .

EXPOSE 8080

RUN adduser -D appuser

USER appuser

CMD ["python", "app.py"]