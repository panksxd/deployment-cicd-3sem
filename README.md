# Deployment CI/CD pipeline

## Part 3 - Deployment with docker compose

### Befor you start remember to:

1. Clone the ```docker-compose``` branch on your droplet

**How to clone a specific repository branch**

```bash
    git clone -b <branch_name> <remote_repo>
```

2. Fill out the docker-compose file with the right image name and tag 
3. Fill out the db/init.sql file with the right database name


### How to run the application

1. Run the following command to start the application

```bash
    docker-compose up -d
```

**The first time you may want to run it without the -d flag to see the logs**


### Access the application

```
    <YOUR_DROPLET_IP>:<JAVALIN_PORT>/api/v1/<ENDPOINT>
```