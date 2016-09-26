# Run Gitlab Server & Runners in local dev environment

### Requirements:

* docker 1.10.0+
* docker compose v1.7+

### Run Gitlab server:

```
docker-compose up -d gitlab-server
```
* Set this "frendly" name in your /etc/hosts:
```
su -c 'echo "127.0.0.1 gitlab-server.dev.local" >> /etc/hosts'
```

### Launch Runners

* With bash:
```
export SERVER_URL="http://gitlab-server.dev.local/ci"
export RUNNER_NAME="dev-local"
export RUNNER_IMAGE="someDockerBuilderImage"
export RUNNER_TOKEN="yourToken"
# Required for runner agents to be able to resolve "gitlab-server.dev.local"
export RUNNER_EXTRA_HOSTS="gitlab-server.dev.local:yourIp"

$ docker-compose up gitlab-runner-reg && docker-compose up -d gitlab-runner
```

* With fish shell:
```
set -x SERVER_URL http://gitlab-server.dev.local/ci
set -x RUNNER_NAME dev-local
set -x RUNNER_IMAGE someDockerBuilderImage
set -x RUNNER_TOKEN yourToken
# Required for runner agents to be able to resolve "gitlab-server.dev.local"
set -x RUNNER_EXTRA_HOSTS gitlab-server.dev.local:192.168.88.2

$ docker-compose up gitlab-runner-reg ; docker-compose up -d gitlab-runner
```


### Example

```
$ docker-compose up -d gitlab-server

export SERVER_URL="http://gitlab-server.dev.local/ci"
export RUNNER_NAME="dev-local"
export RUNNER_IMAGE="ruby:2.1"
export RUNNER_TOKEN="yourTy7YD_vcjaYaLzmCkx2a8ken"
export RUNNER_EXTRA_HOSTS="gitlab-server.dev.local:192.168.88.2"

$ docker-compose up gitlab-runner-reg && docker-compose up -d gitlab-runner
```