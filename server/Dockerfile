FROM python:3.12-slim-bookworm

ENV PYTHONUNBUFFERED=1
ENV PYTHONDONTWRITEBYTECODE=1

ENV APP=/app

# Set working directory
WORKDIR $APP

# Copy requirements and install dependencies
COPY requirements.txt $APP/
RUN pip install --upgrade pip && pip install -r requirements.txt

# Copy project files
COPY . $APP/

# Expose Django port
EXPOSE 8000

# Make entrypoint executable
RUN chmod +x /app/entrypoint.sh

# Set entrypoint
ENTRYPOINT ["/bin/sh", "/app/entrypoint.sh"]

# Start the application
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "--workers", "3", "djangoproj.wsgi:application"]
