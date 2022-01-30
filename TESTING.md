# Testing

This role uses [tox](https://tox.readthedocs.io), [molecule](https://molecule.readthedocs.io) and [LXD](https://linuxcontainers.org/lxd/) to test different scenarios and environments.

## Prerequisites (on Ubuntu)

Setup Docker-CE:
```
sudo apt-get install docker-ce
```
Prepare global ubuntu / python requirements:
```
sudo apt install python3-pip curl docker-ce
sudo pip install virtualenv
```

## Prepare Environment
```
virtualenv .venv
source .venv/bin/activate
pip install -r test-requirements.txt
```

## Tox Usage

Run all tests:
```
tox
```

List available environments:
```
tox -l
```

Run tests in specific environment:
```
tox -e python3.6-ansible29
```

Run custom command in specific environment:
```
tox -e python3.6-ansible29 -- molecule converge
```
