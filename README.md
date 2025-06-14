# Reverse SSH Tunnel Setup Script

A robust and user-friendly script for setting up secure reverse SSH tunnels between servers. This script automates the process of configuring SSH servers, generating and managing SSH keys, and setting up persistent reverse tunnels.

## 🌟 Features

- **One-Command Setup**: Configure both local and remote servers with a single command
- **Idempotent**: Safe to run multiple times without side effects
- **Secure**: Uses ED25519 SSH keys and proper file permissions
- **Persistent**: Sets up systemd service for automatic tunnel maintenance
- **Multi-Service Support**: Configure multiple services on the same remote server
- **Beautiful Output**: Color-coded status messages and clear progress indicators

## 📋 Prerequisites

- Bash shell
- Sudo privileges on both local and remote servers
- SSH access to the remote server
- Systemd (for service management)

## 🚀 Installation

### Quick Start (One-Line Command)

```bash
sudo bash <(curl -sSL https://raw.githubusercontent.com/aleskxyz/reverse_ssh_tunnel/main/setup_tunnel.sh) root@192.168.1.100:22 -s 443
```

This command will:
1. Download the script
2. Execute it with sudo privileges
3. Set up the reverse tunnel

You can also specify an SSH key:
```bash
sudo bash <(curl -sSL https://raw.githubusercontent.com/aleskxyz/reverse_ssh_tunnel/main/setup_tunnel.sh) root@192.168.1.100:22 -s 443 -i ~/.ssh/id_rsa
```

### Manual Installation

1. Download the script:
```bash
curl -O https://raw.githubusercontent.com/aleskxyz/reverse_ssh_tunnel/main/setup_tunnel.sh
```

2. Make it executable:
```bash
chmod +x setup_tunnel.sh
```

## 💻 Usage

```bash
./setup_tunnel.sh USER@HOST[:PORT] -s SERVICE_PORT [-i SSH_KEY]
```

### Arguments

- `USER@HOST[:PORT]`: Connection string for the remote server
  - Example: `root@192.168.1.100:22`
  - Port is optional (defaults to 22)

- `-s SERVICE_PORT`: Port for the reverse SSH tunnel service
  - Example: `-s 443`

- `-i SSH_KEY`: (Optional) Path to SSH key for authentication
  - Example: `-i ~/.ssh/id_rsa`

### Example

```bash
./setup_tunnel.sh root@192.168.1.100:22 -s 443 -i ~/.ssh/id_rsa
```

## 🔧 What the Script Does

1. **Local Setup**:
   - Generates ED25519 SSH keypair
   - Sets up systemd service for the reverse tunnel
   - Configures automatic tunnel maintenance

2. **Remote Setup**:
   - Configures SSH server for reverse tunneling
   - Injects the public key
   - Sets up necessary SSH configurations

3. **Tunnel Configuration**:
   - Creates persistent reverse SSH tunnel
   - Enables automatic reconnection
   - Configures proper port forwarding


## 📝 License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.
