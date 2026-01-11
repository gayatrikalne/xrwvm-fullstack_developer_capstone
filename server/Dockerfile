FROM python:3.12.0-slim-bookworm

# Set environment variables
ENV PYTHONBUFFERED 1
ENV PYTHONWRITEBYTECODE 1
ENV APP=/app

# Change the working directory
WORKDIR $APP

# Install requirements
COPY requirements.txt $APP
RUN pip3 install -r requirements.txt

# Copy the rest of the app files
COPY . $APP

# Expose port 8000
EXPOSE 8000

# Make entrypoint executable
RUN chmod +x /app/entrypoint.sh

# Set entrypoint
ENTRYPOINT ["/bin/bash", "/app/entrypoint.sh"]

# Default command to run Django with gunicorn
CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi"]
