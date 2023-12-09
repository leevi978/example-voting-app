FROM node:18-slim

# add curl for healthcheck
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# have nodemon available for local dev use (file watching)
RUN npm install -g nodemon

ADD package.json ./
ADD package-lock.json ./

RUN ls

RUN npm ci
RUN npm cache clean --force
RUN mv /app/node_modules /node_modules

COPY . .

ENV PORT 8080

EXPOSE 8080

CMD ["node", "server.js"]
