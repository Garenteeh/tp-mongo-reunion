FROM maven:3.9.5-eclipse-temurin-21 AS builder

WORKDIR /app

COPY settings.xml /root/.m2/settings.xml

COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:21-jre

WORKDIR /app

COPY --from=builder /app/target/tourisme-api-0.0.1-SNAPSHOT.jar ./app.jar

EXPOSE 8080

CMD ["java", "-jar", "./app.jar"]
