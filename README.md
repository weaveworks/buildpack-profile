# Buildpack Profile

This is a Buildpack quickstart profile for EKS and Firekube.

## Prepare Docker Hub Credential

Put your Docker username and password, and create a secret using the following command:

```
$ cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Secret
metadata:
  name: registry-credentials
  annotations:
    build.pivotal.io/docker: index.docker.io
type: kubernetes.io/basic-auth
stringData:
  username: <username>
  password: <password>
EOF
```

## Installation on EKS
```
$ EKSCTL_EXPERIMENTAL=true eksctl enable profile \
    --cluster=test-cluster \
    --region us-west-2 \
    --git-url=git@github.com:myorg/test-kubernetes \
    git@github.com:chanwit/buildpack-profile
```

## Installation on Firekube

```
$ export PATH=$HOME/.wks/bin:$PATH

$ wksctl profile enable \
    --git-url=git@github.com:chanwit/buildpack-profile
```

## Start to build an image

