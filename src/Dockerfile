FROM node:20.10.0-alpine3.18
RUN adduser user -D
WORKDIR /app
COPY --chown=user:user --chmod=764 package*.json .
RUN npm install
COPY --chown=user:user --chmod=764 . .
USER user
EXPOSE 8080
CMD [ "node", "server.js" ]