## Deployment CI/CD pipeline

### Part 2 - Docker

1. Sign up for a Dockerhub account
2. Create a new repository on Dockerhub
3. Create a new file called Dockerfile in the root of the project
4. Copy the following code into the Dockerfile

```dockerfile
FROM eclipse-temurin:17-alpine
# This is the jar file that you want to run
COPY target/app.jar /app.jar
# This is the port that your javalin application will listen on
EXPOSE 7070
# This is the command that will be run when the container starts
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

5.  Add the following to the workflow.yml file

```yaml
      -
        name: Login to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      -
        name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2
      -
        name: Build and push
        uses: docker/build-push-action@v4
        with:
          context: .
          file: ./Dockerfile
          push: true
          tags: ${{ secrets.DOCKERHUB_USERNAME }}/<NAME-OF-DOCKERHUB-REPOSITORY>:<DOCKER-TAG>
```


6. Add secrets to your GitHub repository

GO TO (GitHub Secret): Settings -> Secrets and variables -> actions -> New repository secret

- key -> DOCKERHUB_USERNAME : value -> your dockerhub username
- key -> DOCKERHUB_TOKEN : value -> your dockerhub token

GO TO (Dockerhub token) : https://hub.docker.com/settings/security -> New Access Token
