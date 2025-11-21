# Build stage
FROM eclipse-temurin:21-jdk-jammy AS build
WORKDIR /workspace/app

COPY gradlew .
COPY gradle gradle
COPY build.gradle .
COPY settings.gradle .
COPY src src

RUN chmod +x gradlew
RUN ./gradlew build -x test

# Runtime stage
FROM eclipse-temurin:21-jdk-jammy
VOLUME /tmp
EXPOSE 8080
COPY --from=build /workspace/app/build/libs/myservice-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]