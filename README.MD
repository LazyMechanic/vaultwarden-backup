Simple script for automatically backing up Vaultwarden server data as gpg encrypted tar archive and as `KeePassXC` database via cron.
The script is designed to work with systemd `vaultwarden.service` (e.g. in a Proxmox LXC).

### Required:
- `rclone`
- `tar`
- `gpg`
- [`bw`](https://bitwarden.com/help/cli/)
- `systemctl`
- `pip`
- `python3-lxml`

### Usage:
```bash
# Install tools from required list

# Download the project
git clone git@github.com:LazyMechanic/vaultwarden-backup.git /opt/vaultwarden-backup

# Install dependencies and the systemd timer
/opt/vaultwarden-backup/install.sh

# Configure rclone remotes via `rclone config`
# Configure bw server via `bw config server <URL>`
# Configure environment variables in `.env` file

# Adjust the OnCalendar field in /etc/systemd/system/vaultwarden-backup.timer if needed

# Enable and start the backup timer
systemctl enable --now vaultwarden-backup.timer
```