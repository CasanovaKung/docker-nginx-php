FROM mysql:5.7.22

LABEL maintrainer="Jakkrapan Wongchan<casanovakung@windowslive.com>"

# RUN { \
#   echo '[mysqld]'; \
#   echo 'character-set-server = utf8'; \
#   echo 'collation-server = utf8_unicode_ci'; \
# } > /etc/mysql/conf.d/charset.cnf
ADD ./conf.d/charset.cnf /etc/mysql/conf.d/charset.cnf

EXPOSE 3306
CMD ["mysqld"]
