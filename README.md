# Deployment CI/CD pipeline


## Run the application locally with docker run
docker run --name data -p 7070:7070 -e CONNECTION_STR -e DB_USERNAME -e DB_PASSWORD -e DEPLOYED --network <DB_NETWORK> <YOUR-DOCKERHUB-NAME/<NAME-OF-DOCKERHUB-REPOSITORY>:<DOCKER-TAG>

## Run the application locally with docker-compose
docker compose up