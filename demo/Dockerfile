# Build Stage
FROM maven:3.8.2-openjdk-17 AS build
WORKDIR /app
COPY . /app
RUN mvn clean install -DskipTests

# Final Stage
FROM openjdk:17-jdk-slim
ARG ENV
ENV SPRING_PROFILES_ACTIVE=$ENV
COPY --from=build /app/target/configserver-0.0.1-SNAPSHOT.jar /app/app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-Xms2048m", "-Xmx2048m", "-jar", "/app/app.jar"]
