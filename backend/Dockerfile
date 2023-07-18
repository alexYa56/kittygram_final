FROM python:3.9
RUN apt-get clean && apt-get update && apt-get install -y \
    python3-venv
WORKDIR /app
COPY requirements.txt .
RUN pip install gunicorn==20.1.0
RUN python3 -m venv venv
RUN /bin/bash -c "source venv/bin/activate"
RUN pip install -r requirements.txt --no-cache-dir
COPY . .
CMD ["gunicorn", "--bind", "0.0.0.0:9000", "kittygram_backend.wsgi"]
