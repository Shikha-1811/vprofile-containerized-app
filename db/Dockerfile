FROM mysql:8.0

ENV MYSQL_DATABASE=accounts
COPY db_backup.sql /docker-entrypoint-initdb.d/db_backup.sql
