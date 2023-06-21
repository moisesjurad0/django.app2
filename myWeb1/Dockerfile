FROM python:3.11

ENV PYTHONUNBUFFERED=1

# Set the working directory
WORKDIR /code

# Copy and install dependencies
COPY requirements.txt /code/
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code
COPY . /code/

# # Download the wait-for-it.sh script
# RUN curl -o /usr/local/bin/wait-for-it.sh https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh && \
#     chmod +x /usr/local/bin/wait-for-it.sh

# Run migrations and start the application
#CMD ["bash", "-c", "/usr/local/bin/wait-for-it.sh db:3306 -- python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]

# start the application
CMD python manage.py runserver 0.0.0.0:8000
