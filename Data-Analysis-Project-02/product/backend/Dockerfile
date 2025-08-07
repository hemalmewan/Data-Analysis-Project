FROM python:3.11-slim

WORKDIR /app
COPY . /app

COPY ./requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt

COPY ./backend.py /app/

CMD ["fastapi", "run", "backend.py","--host", "0.0.0.0", "--port", "80"]

