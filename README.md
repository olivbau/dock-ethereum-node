# Dock Ethereum Node

## Install 

1. Clone the repository and
```bash
git clone https://github.com/olivbau/dock-ethereum-node.git
cd dock-ethereum-node

```

2. Configure jwt.hex
```bash
openssl rand -hex 32 | tr -d "\n" > "jwt.hex"
cp jwt.hex geth/jwt.hex
cp jwt.hex prysm/jwt.hex
```

3. Configure env vars
```bash
cp .env.example .env
docker run --rm caddy:2-alpine caddy hash-password --plaintext 'password'
# Repace ADMIN_PASSWORD_HASH in .env file
nano .env
```

4. Setup UFW
```bash
ufw allow ssh
ufw enable
```

4. Run
```bash
docker compose up -d
```