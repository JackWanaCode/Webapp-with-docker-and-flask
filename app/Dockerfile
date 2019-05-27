FROM python:3
WORKDIR /usr/src/app
RUN apt-get update
RUN apt-get install -y python3-pip
RUN apt-get install python3-dev
RUN apt-get install -y default-libmysqlclient-dev
RUN apt-get install -y zlib1g-dev
RUN apt-get install -y nginx
COPY default /etc/nginx/sites-available/default
COPY mysql.cnf /etc/mysql/conf.d/mysql.cnf
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . /usr/src/app
CMD ./run_script
