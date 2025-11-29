# Stage 1: Build the app
FROM eclipse-temurin:17-jdk-alpine AS build
WORKDIR /app
COPY employeeBackend/pom.xml .
COPY employeeBackend/src ./src
RUN apk add --no-cache maven
RUN mvn clean package -DskipTests

# Stage 2: Run the app
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
