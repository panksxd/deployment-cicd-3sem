## Deployment CI/CD pipeline

### Part 1 - GitHub workflow pipeline

1. Create a new repository on GitHub and push the project to the repository
2. Create a folder called .github/workflows
3. Create a new file called workflow.yml
4. Copy the following code into the workflow.yml file

```yaml
name: API JAVALIN WORKFLOW
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      -
        name: Checkout
        uses: actions/checkout@v3
      -
        name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'
      -
        name: Build with Maven
        run: mvn --batch-mode --update-snapshots package
        
``` 
5. Remember to create an .gitignore file. https://www.toptal.com/developers/gitignore

6. Push the changes to GitHub and go to the actions tab to see the workflow in action
