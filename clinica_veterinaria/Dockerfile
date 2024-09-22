FROM maven:3.8.5-openjdk-17-slim AS build
WORKDIR /app
COPY . .
RUN mvn clean package  # Genera el archivo JAR en la carpeta target/

# Etapa 2: Crear la imagen final
FROM openjdk:17-jdk-slim
ARG JAR_FILE=target/clinica_veterinaria-0.0.1.jar
COPY --from=build /app/${JAR_FILE} app_veterinaria.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app_veterinaria.jar"]