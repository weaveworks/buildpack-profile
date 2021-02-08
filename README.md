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

XXX: TODO

## Get in touch

[Create an issue](https://github.com/weaveworks/buildpack-profile/issues/new), or
login to [Weave Community Slack (#eksctl)][slackchan] ([signup][slackjoin]).

[slackjoin]: https://slack.weave.works/
[slackchan]: https://weave-community.slack.com/messages/eksctl/

Weaveworks follows the [CNCF Code of Conduct](https://github.com/cncf/foundation/blob/master/code-of-conduct.md). Instances of abusive, harassing, or otherwise unacceptable behavior may be reported by contacting a Weaveworks project maintainer, or Alexis Richardson (alexis@weave.works).
