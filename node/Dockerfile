FROM node:14.17.0-slim as base

# Install base dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    curl \
    wget \
    openssh-client

# Install dependencies
COPY package*.json ./
RUN npm ci
COPY . . 

# Configure local development image
FROM base as local

# Configure node user
ARG UID
RUN usermod -u ${UID} node 
USER node
WORKDIR /home/node/app

CMD [ "tail", "-f" , "/dev/null" ]

# Configure production image
FROM base as production

ENV NODE_PATH=./build
RUN npm run build 
