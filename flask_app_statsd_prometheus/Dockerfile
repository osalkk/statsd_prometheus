FROM python:2.7-alpine
ADD src /application
WORKDIR /application

RUN set -e; \
	apk add --no-cache --virtual .build-deps \
		gcc \
		libc-dev \
		linux-headers \
	; \
	pip install -r requirements.txt; \
	apk del .build-deps;

EXPOSE 5000
VOLUME /application
CMD uwsgi --http :5000  --manage-script-name --mount /myapplication=flask_app:app
