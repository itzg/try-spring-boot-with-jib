I couldn't easily find a full example of using the Jib Spring Boot Gradle extension, so this is one.

## Usage

Build an image that is published into your Docker daemon:

```shell
./gradlew jibDockerBuild
```

Run that image:

```shell
docker run -it --rm -p 8080:8080 try-spring-boot-with-jib:0.0.1-SNAPSHOT
```

Check that it is running at <http://localhost:8080>

## Background

Without that extension applied, the Spring Boot devtools gets included in the built image. As a result, the devtools classloader will bootstrap as reported by the very first log:

```
ClassLoader org.springframework.boot.devtools.restart.classloader.RestartClassLoader@5e076e79
```

and will try to expose the reload service, etc.