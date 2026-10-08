# Install Docker + Kubernetes and run the app — Windows & Linux

At the end you will have our image-classifier app running **twice** on your own computer:

1. with **Docker** (docker compose) → http://localhost:8501
2. with **Kubernetes** → http://localhost:30080

You only install **one program: Docker Desktop**. Kubernetes is a switch inside it.

| Part | What | Windows | Linux (Ubuntu) |
|---|---|---|---|
| 1 | Install Docker Desktop | ~10 min | ~15 min |
| 2 | Run the app with Docker | 5 min | 5 min |
| 3 | Turn on Kubernetes | 3 min | 5 min (+ install `kubectl`) |
| 4 | Run the app on Kubernetes | 5 min | 5 min |

---

## Part 1 — Install Docker Desktop

### 🪟 Windows 10 / 11

1. Go to **https://www.docker.com/products/docker-desktop/** → **Download for Windows**.
2. Run `Docker Desktop Installer.exe`. Keep **"Use WSL 2 instead of Hyper-V"** ticked → **OK** → **Close and restart**.
3. After the restart, open **Docker Desktop** from the Start menu, accept the terms (you can skip sign-in).
4. Wait until the bottom-left corner says **"Engine running"**.

> If Docker asks you to *update WSL*, click the button it shows, then open Docker Desktop again.

### 🐧 Linux (Ubuntu 24.04 / 26.04, 64-bit, with a desktop)

Docker Desktop for Linux needs **KVM** (hardware virtualization). Open a terminal:

**1. Check KVM and give yourself access**
```bash
ls -al /dev/kvm                    # must exist; if not, turn on virtualization (VT-x / AMD-V) in the BIOS
sudo usermod -aG kvm $USER         # then LOG OUT and LOG IN again
```

**2. Add Docker's package repository** (copy the whole block)
```bash
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF
sudo apt update
```

**3. Download and install Docker Desktop**
```bash
curl -LO https://desktop.docker.com/linux/main/amd64/docker-desktop-amd64.deb
sudo apt install ./docker-desktop-amd64.deb
```
(A message *"Download is performed unsandboxed as root…"* at the end is normal — ignore it.)

**4. Start it:** open **Docker Desktop** from your applications menu, accept the terms, wait for **"Engine running"**.

### ✅ Check (Windows and Linux)

```bash
docker
```

---

## Part 2 — Run the app with Docker

Open a terminal **in the course folder** (the one that contains `Day4_Docker_Kubernetes_Cloud`):
* Windows: open the folder in File Explorer → click the address bar → type `powershell` → Enter
* Linux: right-click in the folder → **Open in Terminal**

```bash
cd Day4_Docker_Kubernetes_Cloud/ml-app
docker compose up --build
```

The first time takes a few minutes (Docker downloads Python and the libraries). Wait until you see
`api-1 | ... Listening at: http://0.0.0.0:5000` and `ui-1 | ... You can now view your Streamlit app`.

### ✅ Check
Open **http://localhost:8501** → pick a sample picture → the model says what it is. 🎉

Stop with **Ctrl + C** in the terminal. (The images you just built, `cifar-api:v1` and `cifar-ui:v1`, stay on
your computer — Kubernetes will use them in Part 4.)