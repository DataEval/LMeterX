FROM python:3.12-slim
WORKDIR /app

RUN apt-get update && apt-get install -y curl && apt-get clean

COPY requirements.txt .
RUN pip config set global.index-url https://pypi.org/simple && \
    pip install --no-cache-dir --default-timeout=300 -r requirements.txt

COPY . .

CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "5001", "--workers", "2", "--timeout-keep-alive", "600"]
