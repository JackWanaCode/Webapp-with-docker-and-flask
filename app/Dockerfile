FROM python:3
WORKDIR /usr/src/app
RUN apt-get update && apt-get install -y python3-pip \
    python3-dev \
    default-libmysqlclient-dev \
    zlib1g-dev \
    nginx
COPY default /etc/nginx/sites-available/default
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . /usr/src/app
CMD ./run_script
