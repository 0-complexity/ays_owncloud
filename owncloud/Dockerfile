FROM owncloud:9.0

COPY gig /usr/src/owncloud/themes/gig

EXPOSE 80

RUN /usr/src/owncloud/occ maintenance:install --admin-pass=admin
RUN /usr/src/owncloud/occ maintenance:mimetype:update-js
RUN sed -i "s/c3c8b3d6ca95c7473f3220c60ef48a40d5ac77c2c75b7724ca295f50d7e73e119a2d588d2a564b197d2b6b43486167e37f80c3bd2337ea7d938ac29a802bebcd/`sha512sum /usr/src/owncloud/core/js/mimetypelist.js | awk '{print $1}'`/g" /usr/src/owncloud/core/signature.json

COPY config.php /usr/src/owncloud/config/
ENTRYPOINT ["/entrypoint.sh"]
CMD ["apache2-foreground"]