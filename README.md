# Final project: Github-Actions-project Hands-On DevOps #
The Course was an introduction to Github Actions.

# Motivation: #
This repo contains a pipeline yml file ([.github/workflows/CI_CloudDeployment.yaml](https://github.com/rolandoworks/Udemy-Github-Actions-project/blob/main/.github/workflows/CI_ClouldDeployment.yml)) to compile, dockerize and deploy a kotlin application into a Kubernetes cluster on DigitalOcean.

## Pre-requisites summary##
1) The first task is to check the java and docker versions.
```
    run: |
    java --version
    docker --version
```

## Deployment lifecycle summary##
1) Build the Kotlin app using Gradle.
```
    uses: docker/build-push-action@v2
```

2) Uses a pre-built action from the marketplace, to dockerize and push the image.
```
    run: gradle build
```

3) Uses a doctl action to interact with the Kubernetes cluster on DigitalOcean.
```
    uses: digitalocean/action-doctl@v2
```

4) Deploys the [.\pod.yml](https://github.com/rolandoworks/Udemy-Github-Actions-project/blob/main/pod.yml) into the Kubernetes cluster and verifies it's successful.
```
    run: |
        kubectl apply -f $GITHUB_WORKSPACE/pod.yml
        kubectl describe pods demo-kotlinapp
```

### Course Link: ###

[Build, Deploy configure CI CD with Github Actions & Workflow](https://www.udemy.com/share/106pYk3@KHhDgnDLJ-DTgAT8baG__YfPNI6SAQVGI6MjJE1TVoRl8I2Zo61Ucj--TXzzyo72UA==/)
