# Run Gitlab Server & Runners in local dev environment

### Requirements:

* docker 1.10.0+
* docker compose v1.7+

### Run Gitlab server:

```
docker-compose up -d gitlab-server
``` 

### Launch Runners

* With bash:
```
export SERVER_URL="http://gitlab-server.dev.local/ci"
export RUNNER_NAME="dev-local0"
export RUNNER_IMAGE="someimage"
export RUNNER_TOKEN="yourtoken"

$ docker-compose up gitlab-runner-reg && docker-compose up -d gitlab-runner
```

* With fish shell:
```
set -x SERVER_URL http://gitlab-server.dev.local/ci
set -x RUNNER_NAME dev-local0
set -x RUNNER_IMAGE someimage
set -x RUNNER_TOKEN yourtoken

$ docker-compose up gitlab-runner-reg ; docker-compose up -d gitlab-runner
```
