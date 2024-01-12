# WordPress using Kubernetes

Contains the Kubernetes manifest files to deploy the WordPress application.
Only for learning purposes.

Followed this tutorial : https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/

## Getting started

Using [minikube](https://github.com/kubernetes/minikube), run the following commands:

```zsh
minikube start --nodes 3
kubetcl apply -k ./
minikube service wordpress
```

## Troubleshooting

Scaling the WordPress application,  e.g. by running the command `kubetcl scale --replicas=3 deployment wordpress`, spawns the following issues :

### Untimely disconnection

User is disconnected at each new page.
Probably since the auth token provided by one replica at login is not recognized by other replicas.

### Unavailable content

Files, e.g. pictures, are not displayed frequently. Files are probably not shared between replicas.