# Testing

This role uses [tox](https://tox.readthedocs.io), [molecule](https://molecule.readthedocs.io) and [LXD](https://linuxcontainers.org/lxd/) to test different scenarios and environments.

## Prerequisites (on Ubuntu)

Prepare lxd based on snap:
```
snap install lxd
lxd init
```

Prepare global ubuntu / python requirements:
```sh
sudo apt install python3-pip curl
sudo pip install virtualenv
```

## Prepare Environment
```sh
virtualenv -p python3.8 .venv
source .venv/bin/activate
pip install -r test-requirements.txt
```

## Tox Usage

Run all tests:
```sh
tox
```

List available environments:
```sh
tox -l
```

Run tests in specific environment:
```shsh
tox -e python38-ansible29
```

Run custom command in specific environment:
```sh
tox -e python38-ansible29 -- molecule converge
```


## Testing with docker

There's a special molecule scenario to run the default scenario in docker.

### Prerequisites (on Ubuntu)

Setup Docker:
```sh

# Add gpg key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add sources
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Prepare global ubuntu / python requirements:
```sh
sudo apt install python3-pip curl
sudo pip install virtualenv
```


### Run

Run tests in docker environment and scenario:

```sh
tox -e python38-ansible29-docker -- molecule test -s default_docker
```
