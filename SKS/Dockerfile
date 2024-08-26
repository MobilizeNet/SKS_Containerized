# Use the official .NET SDK image as a base
FROM mcr.microsoft.com/dotnet/sdk:8.0

# Install necessary packages: SQLite3, ODBC, and the SQLite ODBC driver
RUN apt-get update && \
    apt-get install -y build-essential sqlite3 libsqlite3-dev unixodbc unixodbc-dev odbcinst wget && \
    wget http://www.ch-werner.de/sqliteodbc/sqliteodbc-0.9999.tar.gz && \
    tar -xvzf sqliteodbc-0.9999.tar.gz && \
    cd sqliteodbc-0.9999 && \
    ./configure --prefix=/usr/local && \
    make && \
    make install && \
    cd .. && rm -rf sqliteodbc-0.9999*

# Configure the ODBC driver for SQLite3
RUN echo "[SQLite3 ODBC Driver]" >> /etc/odbcinst.ini && \
    echo "Description=SQLite3 ODBC Driver" >> /etc/odbcinst.ini && \
    echo "Driver=/usr/local/lib/libsqlite3odbc.so" >> /etc/odbcinst.ini && \
    echo "Setup=/usr/local/lib/libsqlite3odbc.so" >> /etc/odbcinst.ini

# Set environment variables for ODBC
ENV ODBCINI=/etc/odbc.ini
ENV ODBCSYSINI=/etc

# Copy the application files
COPY deploy /app

# Set the working directory
WORKDIR /app

# Adjust the permissions of the database file
RUN chmod 644 /app/Orders.db && \
    chown root:root /app/Orders.db

# Set the environment variable for the application
ENV ASPNETCORE_URLS=http://0.0.0.0:90

# Entrypoint of the application
ENTRYPOINT ["dotnet", "SKS.dll"]