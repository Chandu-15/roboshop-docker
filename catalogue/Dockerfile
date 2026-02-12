FROM node:20.19.5-alpine3.21 AS build
WORKDIR /opt/server
COPY *.js .
COPY package.json . 
RUN npm install

FROM node:20.19.5-alpine3.21
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=build /opt/server /opt/server
RUN chown -R roboshop:roboshop /opt/server
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node","server.js"]

#  FROM node:20.19.5-alpine3.21
# WORKDIR /opt/server
# COPY *.js .
# COPY package.json . 
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node","server.js"] 