FROM python:3.9.25-alpine3.21
WORKDIR /opt/server
COPY payment.ini .
COPY *.py .
COPY requirements.txt . 
RUN  pip3 install -r requirements.txt



FROM python:3.9.25-alpine3.21
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
CMD ["uwsgi", "--ini", "payment.ini"]




# FROM python:3.9
# WORKDIR /opt/server
# COPY payment.ini .
# COPY *.py .
# COPY requirements.txt . 
# RUN  pip3 install -r requirements.txt
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"
# CMD ["uwsgi", "--ini", "payment.ini"]