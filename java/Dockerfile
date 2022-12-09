FROM maven:3.8-openjdk-8 as builder

WORKDIR /usr/src/app

COPY . .

RUN mvn clean package -DskipTests=true

FROM openjdk:8-jdk

EXPOSE 8448

WORKDIR /usr/src/app

LABEL maintainer="Theo NOEL"

COPY --from=builder /usr/src/app/target/java*.jar docker-java.jar

CMD ["java", "-jar", "docker-java.jar"]