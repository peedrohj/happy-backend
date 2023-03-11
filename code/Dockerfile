FROM node:lts-slim as base

# Install GCC, Make, libpq-dev (for psicopg) and procps
RUN apt-get update
RUN apt-get install -y gcc libpq-dev make graphviz procps gettext-base

# Install Postgres Client
RUN mkdir -p /usr/share/man/man1 \
    && mkdir -p /usr/share/man/man7 \
    && apt-get install -y postgresql-client

# Configure local image
FROM base as local

# Build arguments
ARG UID

# Install base dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    curl \
    wget \
    openssh-client

# Install dependencies
RUN npm i -g @nestjs/cli

# Configure node user
RUN usermod -u ${UID} node 
USER node
WORKDIR /home/node/app/code

CMD [ "tail", "-f" , "/dev/null" ]

# Configure production image
FROM base as production

# Install dependencies
COPY package*.json ./
RUN npm install --production

ENV NODE_PATH=./build
RUN npm run build 
