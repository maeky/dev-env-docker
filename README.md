# dev-env-docker

This is my personal dev environment. Heavily based on [dpeterson/dev-container-*](https://github.com/dpetersen/dev-container-base).

## Building

Build and tag it using the following command:

```
docker build --build-arg UID=$(id -u) --build-arg GID=$(id -g) -t ksoderstrom/dev .
```

## Starting

Run the container with:

```
docker run -d \
  --user 
  -h devbox \
  -e AUTHORIZED_GH_USERS="ksoderstrom" \
  -p 0.0.0.0:31122:22 \
  -v /home/ks/code:/home/dev/code \
  ksoderstrom/dev:latest
```

## Connecting

Add the following to the `~/.ssh/config`:

```
Host devbox
  HostName <YOUR IP OR HOSTNAME>
  Port 31122
  User dev
  ForwardAgent true
  StrictHostKeyChecking no
  UserKnownHostsFile=/dev/null
```

and then connect using `ssh devbox`

## TODO

* make mosh work
