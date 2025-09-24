FROM python:3.10-slim

# Set working directory
WORKDIR /app

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application files
COPY . .

# Create a non-root user and switch to it
RUN useradd -ms /bin/bash appuser
USER appuser

# Expose the port your app runs on (adjust if needed)
EXPOSE 5000

# Add a simple healthcheck (adjust URL if your app uses a different route)
HEALTHCHECK --interval=30s --timeout=5s CMD curl -f http://localhost:5000/ || exit 1

# Start the application
CMD ["python", "app.py"]
