# Instalación de Microsoft SQL Server en Ubuntu Server mediante SSH

## 📋 **Requisitos Previos**
- Acceso SSH a la máquina virtual Ubuntu Server.
- Usuario con permisos de `sudo`.

---

## 🔐 **1. Conéctate a la máquina virtual por SSH**
Desde tu máquina local, ejecuta el siguiente comando para conectarte por SSH:

```bash
ssh usuario@ip-del-servidor
```

**Ejemplo:**

```bash
ssh admin@192.168.1.100
```

---

## 🔄 **2. Actualiza los paquetes del sistema**
Asegúrate de que tu sistema esté actualizado:

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 🔑 **3. Importa la clave GPG de Microsoft**
Ejecuta el siguiente comando para importar la clave de firma de Microsoft:

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
```

---

## 📦 **4. Agrega el repositorio de Microsoft SQL Server**
Agrega el repositorio oficial de Microsoft para Ubuntu Server:

```bash
sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/22.04/mssql-server-2022.list)"
```

🔔 **Nota:** Si estás usando otra versión de Ubuntu, cambia `22.04` por la versión correspondiente.

---

## ⚙️ **5. Instala Microsoft SQL Server**
Actualiza los repositorios e instala SQL Server ejecutando los siguientes comandos:

```bash
sudo apt update
sudo apt install -y mssql-server
```

---

## 🛠️ **6. Configura Microsoft SQL Server**
Después de la instalación, ejecuta el script de configuración de SQL Server:

```bash
sudo /opt/mssql/bin/mssql-conf setup
```

Durante la configuración, se te pedirá:
- Elegir la edición de SQL Server (por ejemplo, `16` para la Developer Edition).
- Configurar la contraseña de administrador (`sa`).

---

## ✅ **7. Verifica que el servicio esté activo**
Confirma que el servicio de SQL Server está en ejecución:

```bash
systemctl status mssql-server
```

Si no está en ejecución, inicia el servicio con:

```bash
sudo systemctl start mssql-server
```

Habilita el servicio para que se inicie automáticamente al arrancar:

```bash
sudo systemctl enable mssql-server
```

---