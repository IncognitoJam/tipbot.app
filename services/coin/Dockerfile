ARG TAG=latest
FROM tipbotapp/node-template:${TAG}

ENV TIPBOT_SERVICE=coin
WORKDIR ${ROOT_DIR}/services/${TIPBOT_SERVICE}
LABEL traefik.backend=${TIPBOT_SERVICE} \
    traefik.frontend.rule=Host:api.localhost,api.tipbot.app;PathPrefixStrip:/${TIPBOT_SERVICE}

COPY package*.json ./
RUN npm ci
COPY . .

USER node
CMD ["node", "src/index.js"]
