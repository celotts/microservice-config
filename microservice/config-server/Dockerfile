FROM openjdk:17-jdk-slim

# Install curl for health checks
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*

# Add JVM options to disable metrics and monitoring
ENV JAVA_TOOL_OPTIONS="-XX:+UseContainerSupport \
    -Dspring.jmx.enabled=false \
    -Dcom.netflix.servo.DefaultMonitorRegistry.disable=true \
    -Dmanagement.metrics.export.simple.enabled=false \
    -Dmanagement.endpoints.enabled-by-default=false \
    -Dio.micrometer.system-metrics.enabled=false \
    -Dmanagement.metrics.enable.process=false \
    -Dmanagement.metrics.enable.system=false \
    -Dspring.autoconfigure.exclude=org.springframework.boot.actuate.autoconfigure.metrics.MetricsAutoConfiguration,org.springframework.boot.actuate.autoconfigure.metrics.SystemMetricsAutoConfiguration,org.springframework.boot.actuate.autoconfigure.metrics.web.tomcat.TomcatMetricsAutoConfiguration"

COPY target/*.jar app.jar

ENTRYPOINT ["java", "-jar", "/app.jar"]