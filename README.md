Contoh Keygen
#!/bin/bash

# === Konfigurasi awal ===
TARGET_USER="Organizer1"          # Ganti jika username Windows beda
TARGET_IP="192.168.18.19"         # IP Windows target
KEY_NAME="id_ed25519"

echo "🔐 Membuat SSH key baru..."
ssh-keygen -t ed25519 -f ~/.ssh/$KEY_NAME -N ""

echo "🛡️ Mengatur firewall Linux (UFW)..."
sudo ufw allow 22
sudo ufw enable

echo "📡 Mengirimkan public key ke Windows..."
ssh-copy-id -i ~/.ssh/${KEY_NAME}.pub ${TARGET_USER}@${TARGET_IP}

echo "✅ Selesai! Sekarang kamu bisa SSH tanpa password:"
echo "ssh ${TARGET_USER}@${TARGET_IP}"

