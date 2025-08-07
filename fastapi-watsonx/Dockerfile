FROM registry.access.redhat.com/ubi8/python-312:1

COPY requirements.txt requirements.txt
# Install any needed packages
RUN pip install --no-cache-dir -r requirements.txt

# Copy only the openapi.py file into the container
COPY watsonxai-endpoint.py /opt/app-root/src/watsonxai-endpoint.py

# Make port 8000 available to the world outside this container
EXPOSE 8000

# Set environment variables for Watsonx API key and URL (to be set at runtime)
ENV WATSONX_IAM_APIKEY=""
ENV WATSONX_PROJECT_ID=""
ENV WATSONX_REGION=""
ENV WATSONX_VERSION=""

# Define environment variable for Python to avoid buffering
ENV PYTHONUNBUFFERED=1

# Run the FastAPI app with Uvicorn when the container launches
CMD ["uvicorn", "watsonxai-endpoint:app", "--host", "0.0.0.0", "--port", "8000"]
