
# BOT GRASS AUTO FARMING

> **Informasi lebih lanjut**: [Airdrop Family IDN](https://t.me/AirdropFamilyIDN)

---

## Update Grass Python

- **Registrasi**: [Daftar di Grass](https://app.getgrass.io/register/?referralCode=AYtNN0N1D0pzSCc)
- **Versi Lite**: Gunakan versi ini jika Anda ingin menjalankan bot tanpa menggunakan node.
- **Versi Node**: Gunakan versi ini jika Anda ingin menjalankan bot dengan node.

> **Catatan**: Format proxy sudah disediakan sebagai contoh di file `local_proxies.txt`. Gunakan salah satu versi saja. Jika Anda memilih versi Lite, login di ekstensi Lite. Jika Anda memilih versi Node, login di ekstensi Node.

**Informasi Tambahan**: Dashboard Grass saat ini sedang mengalami kendala, namun poin akan tetap masuk sesuai informasi dari tim Grass di Discord.

---

## Requirements

### 1. Siapkan Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 2. Clone Repository

```bash
git clone https://github.com/AirdropFamilyIDN-V2-0/grass.git
cd grass
```

### 3. Instalasi Dependensi

```bash
pip install -r requirements.txt
```

### 4. Konfigurasi Proxy

Edit file `local_proxies.txt` untuk memasukkan daftar proxy yang Anda gunakan:

```bash
nano local_proxies.txt
```

### 5. Atur USER_ID

Setel `USER_ID` Anda yang akan digunakan dalam menjalankan bot:

```bash
USER_ID=your_user_id
```

---

## Cara Mendapatkan `user_id` di Grass

1. Login ke website Grass, lalu buka **Developer Console** dengan menekan `F12` atau klik kanan lalu pilih **Inspect**.
2. Di tab **Console**, ketik dan jalankan perintah berikut untuk mendapatkan `user_id`:

    ```javascript
    localStorage.getItem('userId')
    ```

    Jika tidak dapat menempel di Console, ketik `allow pasting` dan tekan `Enter`, lalu jalankan perintah di atas lagi.

---

## Menjalankan Bot Menggunakan `systemd`

> Gunakan salah satu konfigurasi berikut sesuai dengan versi yang Anda pilih (Lite atau Node).

### Konfigurasi untuk Versi Node

Jalankan perintah berikut untuk membuat file service `systemd` untuk versi Node:

```bash
sudo cat <<EOF > /etc/systemd/system/grassnode.service
[Unit]
Description=Grass Node Service
After=network.target

[Service]
Type=simple
WorkingDirectory=/root/grass
ExecStart=/root/.venv/bin/python /root/grass/localgrassnode.py
Environment="USER_ID=$USER_ID"
StandardOutput=journal
StandardError=journal
Restart=always

[Install]
WantedBy=multi-user.target
EOF
```

### Konfigurasi untuk Versi Lite

Jika menggunakan versi Lite, buat service `systemd` dengan perintah berikut:

```bash
sudo cat <<EOF > /etc/systemd/system/grassnode.service
[Unit]
Description=Grass Lite Service
After=network.target

[Service]
Type=simple
WorkingDirectory=/root/grass
ExecStart=/root/.venv/bin/python /root/grass/localgrasslite.py
Environment="USER_ID=$USER_ID"
StandardOutput=journal
StandardError=journal
Restart=always

[Install]
WantedBy=multi-user.target
EOF
```

### Langkah Selanjutnya

1. **Reload `systemd`** untuk memuat konfigurasi baru:

    ```bash
    sudo systemctl daemon-reload
    ```

2. **Mulai Service**:

    ```bash
    sudo systemctl start grassnode.service  
    ```

3. **Aktifkan Service Otomatis saat Boot**:

    ```bash
    sudo systemctl enable grassnode.service  
    ```

5. **Cek log**:

    ```bash
    journalctl -u grassnode.service -f
    ```

---
