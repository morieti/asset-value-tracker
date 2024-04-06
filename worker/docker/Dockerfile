FROM python:3.11

WORKDIR /var/www/html/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV TZ=Asia/Tehran
ENV PATH "${PATH}:/home/nonroot/.local/bin"

RUN apt update
RUN apt install -y vim curl gettext apt-utils supervisor
RUN apt autoclean

RUN pip install --upgrade pip

COPY start-container /usr/local/bin/start-container
RUN chmod +x /usr/local/bin/start-container

EXPOSE 8000

ENTRYPOINT ["start-container"]
