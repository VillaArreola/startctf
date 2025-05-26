# 🚀 startctf

![Demo](/demo.gif)
Script en Bash para automatizar la creación de estructuras de trabajo para máquinas CTF (HTB, TryHackMe, etc.)

Organiza automáticamente carpetas, notas, archivos y lanza escaneos con Nmap para comenzar cada laboratorio de forma rápida y ordenada.

---

## 📦 Instalación

### 🔁 Clonar el repositorio

```bash


git clone https://github.com/villaarreola/startctf.git
cd startctf
sudo cp startctf /usr/local/bin/
chmod +x /usr/local/bin/startctf
```

---
Requerimientos de instalación:
```bash
sudo apt install nmap xclip tree git
```

---

## 🚀 Uso

```bash
startctf <plataforma> <nombre> <IP>
```

Ejemplo:

```bash
startctf HTB Bricks 10.10.10.123
```

---

### 🔄 ¿Qué hace el script?

1. **Verifica si la IP responde a ping:**

   ```bash
   ping -c 1 -W 1 \$IP
   ```

2. **Setea la variable ****`$TARGET`**** y guarda la IP en un archivo:**

   ```bash
   echo "$IP" > ~/.target
   export TARGET="$IP"
   ```

  Opcional Agrega `$TARGET`  a tu `~/.zshrc` o `~/.bashrc`:

   ```bash
   [[ -f ~/.target ]] && export TARGET=$(cat ~/.target)
   ```
    O puedes agregarlo a tu archivo de configuración de shell para que se cargue automáticamente al iniciar una nueva sesión. También puedes crear un alias para consultar el target actual:

   ```bash
   alias target='cat ~/.target'
   ```
  ```bash 

    target
    # Muestra la IP del target actual
    ```
3. **Crea la estructura de carpetas y archivos:**

   ```bash
   mkdir -p ~/ctf/$PLATFORM/$NAME/{files,scripts,nmap}
   touch ~/ctf/$PLATFORM/$NAME/{notes.md,passwd.txt,users.txt}
   ```

4. **Realiza escaneo Nmap (silencioso):**

   ```bash
   nmap -sC -sV -T4 -oA ~/ctf/$PLATFORM/$NAME/nmap/scan $TARGET
   ```

5. **Copia la ruta al portapapeles:**

   ```bash
   echo "~/ctf/$PLATFORM/$NAME" | xclip -selection clipboard
   ```

6. **Muestra la estructura del directorio creada:**

   ```bash
   tree ~/ctf/$PLATFORM/$NAME
   ```

---

Ejemplo:

```
[2025-05-26 10:30:21] HTB - Bricks (10.10.10.123) → /home/villa/ctf/HTB/Bricks
```

---

## 🧠 Autor

**Villa Arreola**
[@villaarreola](https://github.com/villaarreola)

---

