# Kubernetes Dashboard

Kubernetes Dashboard, based on the [official guide](https://github.com/kubernetes/dashboard).

## Getting Started

### Prerequisites
- A Kubernetes cluster with kubectl access
- Properly configured ingress controller

### Deployment
To deploy Dashboard, execute the following command:

```sh
$ kubectl apply -f deployment.yaml
```

### Managing permissions

Create an admin service account to manage the cluster:

```sh
$ kubectl apply -f admin-user.yaml
```

We will use the `admin-user` token as a Bearer token to log in to the Dashboard. Get the token by typing:

```sh
$ kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')
```

Copy the token and paste it into the `Enter token` field on log in screen. Click the `Sign in` button, and that's it. You are now logged in as an admin!
