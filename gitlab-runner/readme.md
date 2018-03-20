Generate a config file before running the containers

Here is how to create the config.toml, and make sure the location is specified in the compose file

https://docs.gitlab.com/runner/configuration/advanced-configuration.html

Here is an config file that was used for a while:
(Don't forget to set your executor token)

```
concurrent = 1
check_interval = 0

[[runners]]
  name = "lugdocker.eecs.wsu.edu"
  url = "https://gitlab.com/"
  token = $EXECUTOR_TOKEN
  executor = "docker"
  [runners.docker]
    tls_verify = false
    image = "docker:latest"
    privileged = false
    disable_cache = false
    volumes = ["/var/run/docker.sock:/var/run/docker.sock","/cache"]
  [runners.cache]
    Insecure = false
```