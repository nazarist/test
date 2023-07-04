FROM node:16.20.0

RUN apt-get update && apt-get install -y --no-install-recommends \
    rubygems build-essential ruby-dev \
    && mkdir /build-dir \
    && rm -rf /var/lib/apt/lists/*


WORKDIR /build-dir

COPY client/package*.json /build-dir

RUN npm install -g babel babel-runtime babel-register mocha nodemon \
    && npm install \
    && mkdir -p /var/www/client/


WORKDIR /var/www/client/

RUN chown -R node.node ./ \
    && ln -s /build-dir/node_modules node_modules

USER node

# Bundle app source
COPY . .

EXPOSE 3000
CMD [ "npm", "start" ]