FROM python:3.11-slim

WORKDIR /app

# Copy requirements first to leverage caching
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the app
COPY . .

# Create non-root user
RUN useradd -m appuser
USER appuser

EXPOSE 5002

CMD ["python", "app.py"]
