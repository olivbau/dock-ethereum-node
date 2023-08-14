# Docknode ETH

## Metrics

- `https://yourdomain.com:9100/metrics`
- `https://yourdomain.com:9101/metrics`
- `https://yourdomain.com:9102/metrics`

## Install

0. VPS config (optional)

```bash
apt update
apt upgrade
apt install git
# Or all in one command
apt update && apt upgrade -y && apt install -y git

# install docker https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
```

1. Clone the repository and

```bash
git clone https://github.com/olivbau/docknode-eth.git
cd docknode-eth
```

2. Configure jwt.hex

```bash
openssl rand -hex 32 | tr -d "\n" > "jwt.hex"
```

3. Configure environement variables

```bash
cp .env.example .env

# Generate users passwords for basic auth
docker run --rm caddy:2-alpine caddy hash-password --plaintext 'password'

# Set users and passwords for basic auth
# Set the host
nano .env
```

4. Setup UFW

```bash
ufw allow ssh
ufw deny 8545 && ufw deny 8551 && ufw deny 3500 && ufw deny 4000 && ufw deny 8080
ufw enable
```

5. Run

```bash
docker compose pull
docker compose up -d
docker logs -f docknode-eth-beaconnode-1 --since 10m
docker logs -f docknode-eth-executionnode-1 --since 10m
docker compose down
```
