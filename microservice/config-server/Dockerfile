FROM openjdk:17-jdk-slim

WORKDIR /app

# Instalar herramientas necesarias
RUN apt update && apt install -y curl

# Copiar el JAR
COPY target/*.jar app.jar

# Puerto
EXPOSE 7777

# Ejecutar con opciones para deshabilitar métricas
ENTRYPOINT ["java", "-noverify", "-XX:TieredStopAtLevel=1", "-Dservlet.registerMBeans=false", "-Dio.micrometer.system-metrics.enabled=false", "-Dmanagement.metrics.enable.system=false", "-Dmanagement.metrics.enable.process=false", "-Dmanagement.metrics.enable.jvm=false", "-Dspring.jmx.enabled=false", "-jar", "app.jar"]