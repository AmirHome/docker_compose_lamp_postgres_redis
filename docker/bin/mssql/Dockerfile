FROM mcr.microsoft.com/mssql/server:2019-latest


# ARG DB_PASSWORD
# ENV ACCEPT_EULA=Y
# ENV SA_PASSWORD=${DB_PASSWORD}
# EXPOSE 1433

USER root

# Create a config directory
RUN mkdir -p /usr/config
WORKDIR /usr/config

# Bundle config source
COPY . /usr/config

# Grant permissions for to our scripts to be executable
RUN chmod +x /usr/config/entrypoint.sh
RUN chmod +x /usr/config/configure-db.sh

ENTRYPOINT ["./entrypoint.sh"]

#docker exec -it db-mssql /opt/mssql/bin/sqlservr --version
