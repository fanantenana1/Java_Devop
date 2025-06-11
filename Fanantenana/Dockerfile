# Étape 1 : build avec Maven
FROM maven:3.8.6-eclipse-temurin-17 AS builder

WORKDIR /app

COPY Fanantenana/pom.xml Fanantenana/pom.xml
COPY Fanantenana/src Fanantenana/src

RUN mvn -f Fanantenana/pom.xml clean package -DskipTests

# Étape 2 : image d'exécution
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

# Copier le JAR depuis le builder
COPY --from=builder /app/Fanantenana/target/java-devops-1.0-SNAPSHOT.jar app.jar

# Lancer l'application
ENTRYPOINT ["java", "-jar", "/app/app.jar"]

