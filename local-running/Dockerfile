RUN npm ci
COPY --chown=node:node ./configurations ./configurations

COPY --from=development /home/node/configurations ./configurations/
