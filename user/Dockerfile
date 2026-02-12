FROM node:20.19.5-alpine3.21 as build 
WORKDIR /opt/server
COPY *.js .
COPY package.json . 
RUN npm install


FROM node:20.19.5-alpine3.21
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue" \
    REDIS_URL="redis://redis:6379"
CMD ["node","server.js"]

# FROM node:20.19.5-alpine3.21
# WORKDIR /opt/server
# COPY *.js .
# COPY package.json . 
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue" \
#     REDIS_URL="redis://redis:6379"
# CMD ["node","server.js"]