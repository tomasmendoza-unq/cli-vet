# Etapa 1: Compilar el proyecto
FROM maven:3.8.5-openjdk-17-slim AS build
WORKDIR /app
COPY ./
RUN mvn clean package

# Etapa 2: Crear la imagen final
FROM openjdk:17-jdk-slim
ARG JAR_FILE=clinica_veterinaria-0.0.1.jar
COPY --from=build /app/target/${JAR_FILE} app_veterinaria.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app_veterinaria.jar"]
