FROM python:3.8

ENV user kctf
ENV port 5000

RUN apt-get update -y
RUN apg-get install -ypp unzip curl
RUN wget -O /home/kctf/chromedriver.zip http://chromedriver.storage.googleapis.com/`curl -sS chromedriver.storage.googleapis.com/LATEST_RELEASE`/chromedriver_linux64.zip

RUN unzip /home/kctf/chromedriver.zip chromedriver -d /home/kctf/
RUN chmod 775 /home/kctf/
RUN chmod 557 /home/kctf/chromedriver
RUN apt-get install -y python3
RUN apt-get install -y python3-pip python-dev build-essential musl-dev gcc
RUN adduser --disabled-password $user
ADD ./web_readbot /home/kctf/
WORKDIR /home/kctf/
RUN pip3 install selenium
USER $user
EXPOSE $port

ENTRYPOINT ["python"]
CMD ["main.py"]