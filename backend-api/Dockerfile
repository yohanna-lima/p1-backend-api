# Etapa de build
FROM maven:3.9.4-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Etapa de execução
FROM eclipse-temurin:17-jdk
WORKDIR /app
COPY --from=build /app/target/backend-api.jar app.jar
EXPOSE 8080
ENV SPRING_PROFILES_ACTIVE=docker
CMD ["java", "-jar", "app.jar"]
