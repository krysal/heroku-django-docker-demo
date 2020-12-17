# Pull official base image
FROM python:3.7-stretch

# Ensures that the python output is sent straight to the terminal
# without buffering it first
ENV PYTHONBUFFERED 1

# Prevents Python from writing pyc files to disc
ENV PYTHONDONTWRITEBYTECODE 1

# Install Python dependency management tools
RUN pip install --upgrade pip \
    && pip install --upgrade setuptools \
    && pip install --upgrade pipenv

# Set work directory
WORKDIR /app

# Copy the Pipenv files into the container
COPY Pipfile .
COPY Pipfile.lock .

# Install project dependencies system-wide
RUN pipenv install --system

# Copy project
COPY . .

CMD gunicorn hello_hddd.wsgi:application --bind 0.0.0.0:$PORT
