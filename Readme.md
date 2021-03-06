# Tutorial for Kubernetes (K8s)

The goal of this tutorial is setup a Kubernetes infrastructure for an application that calculates Fibonacci number based on an input from the user.

## Docker

The app consist of 3 components and their respective Dockerfiles. In the app, the user will log in, and the input will be added using Redis in memory and Postgres for the database. The first steps to create the component images, tag them and push them to our Docker registry:

1.  **Client**

    `time docker build -t fibo-client .`

    `docker tag fibo-client jbpino/fibo-client`

    `docker push jbpino/fibo-client`

2.  **Server**

    `time docker build -t fibo-server .`

    `docker tag fibo-server jbpino/fibo-server`

    `docker push jbpino/fibo-server`

3.  **Worker**

    `time docker build -t fibo-worker .`

    `docker tag fibo-worker jbpino/fibo-worker`

    `docker push jbpino/fibo-worker`

## Kubernetes

The goal will be to implement the following infrastructure:

![Screenshot](fibo-k8s-diagram.png)

We could consider the following main object types for Kubernetes:

![Screenshot](k8s-object-types.png)

### Steps:

1.  Create **client deployment** and **ClusterIP service** yaml config files

    `kubectl apply -f k8s/client-deployment.yaml`

    `kubectl apply -f k8s/client-cluster-ip-service.yaml`
