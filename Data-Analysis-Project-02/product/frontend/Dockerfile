FROM python:3.11-slim

WORKDIR /app
COPY . /app

# Copy the static images folder from the parent directory
COPY ../static /app

RUN pip install --no-cache-dir -r requirements.txt

CMD ["streamlit", "run", "frontend.py", "--server.port=8501", "--server.address=0.0.0.0"]
