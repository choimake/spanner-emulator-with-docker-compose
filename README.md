# spanner-emulator-with-docker-compose

## Requirement
- docker
- docker-compose
- direnv
- spanner-cli

## Installation

### Install direnv
See [here](https://direnv.net/docs/installation.html) for details.

### Install spanner-cli
```
$ go install github.com/cloudspannerecosystem/spanner-cli@latest
```
See [here](https://github.com/cloudspannerecosystem/spanner-cli?tab=readme-ov-file#install) for more details.

## How to use

First, allow direnv
```
direnv allow
```

Then, start docker-compose.  
> [!NOTE]
> The init process takes some time to complete, so please wait until it is finished.
```
$ docker-compose up -d
```

Then, set the gcloud config like this
```
$ gcloud config list                   

[api_endpoint_overrides]
spanner = http://localhost:9020/
[auth]
disable_credentials = true
[core]
account = xxxx@yyy.jp
disable_usage_reporting = True
project = test-project
```

Then, connect to spanner emulator
```
$ spanner-cli -p test-project -i test-instance -d test-database
```
