# <img src="https://raw.githubusercontent.com/loohive/onion-pipe-relay/main/src/assets/logo/logo.png" height="32"> Vault-over-Tor (maintained by LOOHIVE)

**Vault-over-Tor** is a pre-configured, hardened HashiCorp Vault instance maintained by the LOOHIVE Infrastructure Team. It is accessible exclusively via Tor Onion Services, providing zero-knowledge secret storage with identity-hiding transport.

## 🚀 Architecture
- **HashiCorp Vault**: The core secret engine.
- **Tor v3 Service**: Exposes Vault via a `.onion` address.
- **Nginx Ingress**: Handles local routing and security headers within the container.
- **Auto-Unseal Ready**: Scripts included for manual or automated unsealing.

## 🐳 Quick Start

### 1. Launch the Stack
```bash
docker compose up -d
```

### 2. Initialize Vault
```bash
docker exec -it vault-tor sh /init-vault.sh
```
*Save your recovery keys and root token securely!*

### 3. Retrieve Your Onion Address
```bash
cat ./keys/hostname
```

## 🛠️ Configuration
- `vault-config.hcl`: Tuned for Tor performance and UI security.
- `nginx.conf.template`: Hardened Nginx headers for the Vault UI.

## 🛡️ Security Features
- **Hidden Ingress**: No listener on physical public ports.
- **E2E Encrypted**: Tor inherently encrypts all traffic to the onion service.
- **Volume Isolation**: Data and keys are stored in separate persistent volumes.
