FROM python:3.12-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app.py .

FROM python:3.12-alpine AS runtime
WORKDIR /app
RUN pip install --no-cache-dir flask==3.0.0 numpy==1.26.0
COPY --from=builder /app/app.py .
EXPOSE 8080
CMD ["python", "app.py"]