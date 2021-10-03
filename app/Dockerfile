FROM python:3.9-alpine

LABEL MANTAINER="Jair Reis"

ENV GRUP_ID=1000 \
    USER_ID=1000

WORKDIR /var/www

ADD ./requirements.txt /var/www/requirements.txt
RUN pip install -r requirements.txt
RUN pip install gunicorn
RUN addgroup -g $GRUP_ID www
RUN adduser -D -u $USER_ID -G www www -s /bin/sh

USER www

EXPOSE 5000

CMD ["gunicorn", "-w", "4", "--bind", "0.0.0.0:5000", "wsgi"]