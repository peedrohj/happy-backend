FROM python:3.10.2-slim

# Build arguments
ARG UID

# Install base dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    default-jre \
    git \
    curl \
    wget \
    openssh-client

# Install GCC, Make, libpq-dev (for psicopg) and procps
RUN apt-get install -y gcc libpq-dev make graphviz procps gettext-base

# Install Postgres Client
RUN mkdir -p /usr/share/man/man1 \
    && mkdir -p /usr/share/man/man7 \
    && apt-get install -y postgresql-client

# Configure media files
RUN mkdir -p /vol/web/static  \
    && mkdir -p /vol/web/media \
    && chmod -R 755 /vol 

# Create python user 
RUN useradd -ms /bin/bash -u ${UID} python
WORKDIR /home/python/app
USER python

# Define environment variables
ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONFAULTHANDLER 1
ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64

CMD [ "tail", "-f", "/dev/null" ]