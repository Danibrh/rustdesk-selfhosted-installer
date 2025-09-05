# RustDesk Self-Hosted Server & Custom Installer

This project documents the setup of a **self-hosted RustDesk server (hbbs + hbbr)** on a VPS and the creation of a **professional Windows installer (EXE)** using Inno Setup with pre-configured server settings.

---

## 📌 Features

- Self-hosted RustDesk server running in Docker (hbbs + hbbr).
- Secure custom configuration (`RustDesk2.toml`) distributed with the installer.
- Professional Windows installer built with Inno Setup.
- Automated installation of RustDesk MSI with pre-applied settings.
- Documented step-by-step deployment process.

---

## 🛠️ Tech Stack

- **Server**: Ubuntu 22.04 LTS on AWS EC2
- **Containers**: Docker & Docker Compose
- **Remote Tool**: RustDesk (self-hosted)
- **Installer**: Inno Setup 6
- **Languages**: Shell, Inno Setup Script

---

## 📂 Repository Structure

See [`Project Structure`](./) for an overview of the folders:
- `server/` → Docker setup for hbbs/hbbr.
- `installer/` → MSI, config, and Inno Setup script.
- `docs/` → Screenshots documenting the process.

---

## 🚀 Deployment Steps

### 1. Server Setup
1. Provision an **Ubuntu VPS** (tested on AWS EC2).
2. Open required ports **21115–21119 TCP/UDP** in the security group.
3. Deploy RustDesk server using Docker:
   ```bash
   sudo docker compose up -d
   ```
4. Verify services:
   ```bash
   sudo ss -tulpn | grep 211
   sudo docker logs -f hbbs
   sudo docker logs -f hbbr
   ```

### 2. Installer Setup
1. Place `rustdesk-1.4.1-x86_64.msi` and `RustDesk2.toml` inside the `installer/` folder.
2. Compile the installer with Inno Setup (`setup.iss` script).
3. The output will be available in `/installer/output/`.

### 3. Client Configuration
- Install the generated EXE on Windows.
- RustDesk automatically points to your custom server.
- No manual configuration required for the end-user.

---

## 📷 Screenshots

*(Add your own captures in `/docs/` folder with the following names)*

1. **Server running in Docker** → `01_server_running.png`  
2. **Inno Setup script ready** → `02_inno_setup.png`  
3. **Installer built successfully** → `03_installer_built.png`  
4. **Client with pre-configured server** → `04_client_configuration.png`  
5. **Successful remote connection test** → `05_successful_connection.png`

---

## 📜 License

MIT License – feel free to use, modify, and share.

## Author
Created by **Daniel Bracho**  
GitHub: [@Danibrh](https://github.com/Danibrh)


