<h1>WAS Prebuilt Github Action</h1>

This is a prebuilt Github Actions "Action" that makes it easier to run the 10ble Web App Scanner in your Github Actions Pipeline.

It is hiding a lot of the code so that the user doesn't have to know as much about running the code. All the user needs to do is input the relevant variables. 

To use it in a Github actions workflow, you would refer to it as:
```
uses: EvanGrace25/10ble-was-cicd-action@main
```

Here is sample code that you could put into your repository in the .github/workflows folder to test this out:
```
name: CI WAS Scan
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  tenablescan:
    name: was-cicd-testing
    runs-on: ubuntu-latest
    steps:
      - name: Print Hello test
        run: |
          echo "Hello World"
      - name: Test Pre-defined action
        uses: EvanGrace25/10ble-was-cicd-action@main
        with:
          access_key: ${{ secrets.ACCESS_KEY }}
          secret_key: ${{ secrets.SECRET_KEY }}
          link_container: petstore
          use_petstore_example: true
```

In this example, it is using the built in Github Actions Secrets manager, so you would want to put your access key and secret key in there as ACCESS_KEY and SECRET_KEY
