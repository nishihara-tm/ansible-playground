## Setup

```bash
mkdir .ssh
cd .ssh
ssh-keygen
```

## To launch

```bash
docker-compose build
docker-compose up
```

## To Test playbook

```bash
docker-compose exec ansible ansible-playbook -i /playbook.yml
```