FROM maven:3.8.4-jdk-11-slim as builder


COPY . .

WORKDIR /.

RUN mvn dependency:resolve

RUN mvn package

FROM openjdk:11-jre-slim

EXPOSE 80

COPY --from=builder /target/worker-jar-with-dependencies.jar .

CMD java -jar worker-jar-with-dependencies.jar
