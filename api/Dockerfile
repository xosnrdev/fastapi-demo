FROM python:3.10.15-slim-bookworm AS build

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY main.py .

FROM python:3.10.15-slim-bookworm AS production

WORKDIR /app

COPY --from=build /usr/local/lib/python3.10/site-packages /usr/local/lib/python3.10/site-packages

COPY --from=build /app/main.py .

ENTRYPOINT ["python", "main.py"]