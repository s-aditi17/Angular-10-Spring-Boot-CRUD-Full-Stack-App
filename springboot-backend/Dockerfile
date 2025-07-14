FROM maven:3.9.4-eclipse-temurin-17 as build

WORKDIR /app

# Copy your custom Maven settings.xml into Maven config folder
COPY settings.xml /root/.m2/settings.xml

# Copy the whole project
COPY . .

# Run Maven build using your settings.xml (optional: explicitly specify settings)
RUN mvn clean package -DskipTests

FROM openjdk:17-jdk-slim

WORKDIR /app

# Copy the built jar from the build stage
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
