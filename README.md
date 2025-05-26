🚀 startctf

Script en Bash para automatizar la creación de estructuras de trabajo para máquinas CTF (HTB, TryHackMe, etc.)

Organiza automáticamente carpetas, notas, archivos y lanza escaneos con Nmap para comenzar cada laboratorio de forma rápida y ordenada.

📦 Instalación

🔁 Clonar el repositorio

git clone https://github.com/villaarreola/startctf.git
cd startctf
sudo cp startctf /usr/local/bin/
chmod +x /usr/local/bin/startctf

🧠 Requisitos

nmap

xclip

tree (opcional, para mostrar estructura)

git (para instalar el script)

Instalalos en Debian/Kali con:

sudo apt install nmap xclip tree git

🚀 Uso

startctf <plataforma> <nombre> <IP>

Ejemplo:

startctf HTB Bricks 10.10.10.123

🔄 ¿Qué hace el script?

Verifica si la IP responde a ping.

Setea $TARGET y guarda la IP en ~/.target

Crea estructura:

~/ctf/HTB/Bricks/
├── files/
├── scripts/
├── nmap/
│   ├── scan.nmap
│   ├── scan.gnmap
│   └── scan.xml
├── notes.md
├── passwd.txt
└── users.txt

Lanza escaneo Nmap

Copia la ruta al clipboard

Muestra la estructura creada

🛡️ Log de uso

Cada vez que se crea una máquina, se registra en:

~/ctf/logs/startctf.log

Ejemplo:

[2025-05-26 10:30:21] HTB - Bricks (10.10.10.123) → /home/villa/ctf/HTB/Bricks

🧠 Autor

Villa Arreola@villaarreola
