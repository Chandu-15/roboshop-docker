FROM maven:3.9.11 as build
WORKDIR /opt/server
COPY src ./src
COPY pom.xml . 
RUN mvn clean package 
RUN mv target/shipping-1.0.jar shipping.jar


FROM eclipse-temurin:17-jre-alpine
WORKDIR /opt/server
COPY --from=build /opt/server/shipping.jar /opt/server
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
CMD ["java","-jar","shipping.jar"]


# FROM maven:3.9.11
# WORKDIR /opt/server
# COPY src ./src
# COPY pom.xml . 
# RUN mvn clean package 
# RUN mv target/shipping-1.0.jar shipping.jar
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java","-jar","shipping.jar"]