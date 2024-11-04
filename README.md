# BOT GRASS AUTO FARMING
- https://t.me/AirdropFamilyIDN
# Update Grass Python
# Register
- https://app.getgrass.io/register/?referralCode=AYtNN0N1D0pzSCc
- Lite Version
- Node Version
- Format Proxy Dah Ane Kasih Contoh Di ```localproxies.txt```
- Pake Salah Satu Saja, Jika Mau Pake Versi Lite Ya Login Extensi Lite, Kalau Mau Pake Node Ya Login Extensi Node
- ```Dashboard Grass Masih Error``` Kata Team Grass Gw Tanyain Didiscord Tadi, Point Bakal Tetep Masuk.

# Requirements

```
python3 -m venv .venv
```
```
source .venv/bin/activate
```
```
git clone https://github.com/AirdropFamilyIDN-V2-0/grass.git
```
```
cd grass
```
```
pip install -r requirements.txt
```
```
nano local_proxies.txt
```
### see
```
USER_ID=your_user_id
```

##  Pake Salah Satu aja, Jika Mau Pake Versi Lite Ya Login Extensi Lite, Kalau Mau Pake Node Ya Login Extensi Node
```
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
```
sudo cat <<EOF > /etc/systemd/system/grassnode.service
[Unit]
Description=Grass Node Service
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
# How to get userid grass
- login ke web grass , terus inspect / f12 ,  klik console
- paste
``` 
localStorage.getItem('userId')
```
- kalau ga bisa paste ketik ```allow pasting``` enter
- baru paste ```localStorage.getItem('userId')```enter lagi
