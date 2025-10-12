FROM python:3.11-slim

WORKDIR /api

# Install system dependencies for mysqlclient
RUN apt-get update \
    && apt-get install -y gcc default-libmysqlclient-dev pkg-config \
    && rm -rf /var/lib/apt/lists/*

# Copy dependencies and install Python packages
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the code
COPY . .

# Create non-root user and switch to it
RUN useradd -m flaskuser
USER flaskuser

EXPOSE 5001

CMD ["python", "api.py"]
