FROM node:20.19.5-alpine3.21 as build
WORKDIR /opt/server
COPY *.js .
COPY package.json .
RUN npm install


FROM node:20.19.5-alpine3.21
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT=8080
CMD ["node","server.js"]

# FROM node:20.19.5-alpine3.21
# WORKDIR /opt/server
# COPY *.js .
# COPY package.json .
# RUN npm install
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT=8080
# CMD ["node","server.js"]