# Dock Ethereum Node

`docker run --rm caddy:2-alpine caddy hash-password --plaintext 'password'`
`openssl rand -hex 32 | tr -d "\n" > "jwt.hex" && cp jwt.hex geth/jwt.hex && cp jwt.hex prysm/jwt.hex`