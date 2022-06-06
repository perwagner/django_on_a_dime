FROM python:3.10

ENV HOME=/
ENV APP_HOME=/app

# Keeps Python from generating .pyc files in the container
ENV PYTHONDONTWRITEBYTECODE=1
# Turns off buffering for easier container logging
ENV PYTHONUNBUFFERED=1
ENV DEBUG 0

RUN apt-get update && apt-get upgrade -y && apt-get install -y \
  && apt-get clean

RUN pip install -U pip

# Install pip requirements
COPY . $APP_HOME/
RUN python -m pip install -r $APP_HOME/requirements.txt

WORKDIR $APP_HOME/

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "conf.wsgi:application"]