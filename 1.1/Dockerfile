FROM tutum/lamp:latest

MAINTAINER Gildásio Júnior (gjuniioor@protonmail.com)

# Install bricks
RUN rm -rf /app

ADD https://downloads.sourceforge.net/project/owaspbricks/Betwa%20-%201.1/OWASP%20Bricks%20-%20Betwa.zip?r=http%3A%2F%2Fsechow.com%2Fbricks%2Fdownload.html&ts=1498533036&use_mirror=ayera /bricks.zip

RUN apt-get update
RUN apt-get install unzip -y
RUN unzip bricks.zip
RUN rm bricks.zip
RUN mv bricks app

RUN echo 'echo "create database bricks;" | mysql -u root -p' >> /run.sh

RUN echo "<?php\n\$dbuser = 'root';\n\$dbpass = '';\n\$dbname = 'bricks';\n\$host = 'localhost';\n\$showhint = true;\n\$server = 'http://127.0.0.1';\n\$scriptpath = '/release-channel';\n?>" > /app/LocalSettings.php

EXPOSE 80 3306

CMD ["/run.sh"]
