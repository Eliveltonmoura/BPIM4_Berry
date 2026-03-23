Perfeito — agora integrei a parte do **Git** no seu README e deixei **tudo em ordem final, bem organizado e profissional** 👇

---

# 📘 Instalação do Sistema — Banana Pi BPI-M4 Berry

---

## 📥 1. Baixar o sistema

Acesse:

👉 [https://drive.google.com/drive/folders/1skZIAf16dfH7u3JqvKhPoWCTCDbhLhrH](https://drive.google.com/drive/folders/1skZIAf16dfH7u3JqvKhPoWCTCDbhLhrH)

Baixe:

```bash
Bananapi-Armbian_24.8.2_Bpi-m4berry_jammy_legacy_5.4.125_minimal.img
```

---

## 🧰 2. Baixar o gravador

Baixe o Balena Etcher:

👉 [https://etcher.balena.io/](https://etcher.balena.io/)

---

## 📂 3. Abrir o Etcher (Linux)

```bash
cd Downloads/balenaEtcher-linux-x64
./balena-etcher
```

---

## 💽 4. Gravar no cartão SD

1. **Flash from file**
2. Selecionar a imagem
3. **Select target**
4. Escolher o cartão SD
5. **Flash**

---

## 🔌 5. Preparar a placa

* Inserir o cartão SD
* Ligar a energia
* Conectar cabo TTL
* Abriar a Minecom

---

## 🚀 6. Primeiro boot

* Ligue a placa
* Aguarde iniciar

📌 Caso apareça configuração inicial:
👉 **Siga o passo a passo exibido na tela**

---

## 🔐 7. Login inicial

```bash
usuário: (definido por você)
senha: (definida por você)
```

📌 O login padrão (`root / 1234`) é usado apenas na primeira vez

---

## 🌐 8. Configurar Wi-Fi

### 📄 Criar o script com o GNU nano

```bash
nano wifi.sh
```

Cole:

```bash
#!/bin/bash

SSID="SEU_WIFI"
PASSWORD="SUA_SENHA"

echo "Configurando Wi-Fi..."

sudo ip link set wlan0 up

sudo bash -c "cat > /etc/wpa_supplicant.conf <<EOF
network={
    ssid=\"$SSID\"
    psk=\"$PASSWORD\"
}
EOF"

sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf
sudo dhclient wlan0

echo "Testando conexão..."
ping -c 3 8.8.8.8

echo "Configurando DNS..."
sudo bash -c 'echo -e "nameserver 8.8.8.8\nnameserver 1.1.1.1" > /etc/resolv.conf'

ping -c 3 google.com

echo "Finalizado!"
```

### ⚙️ Dar permissão

```bash
chmod +x wifi.sh
```

### ▶️ Executar

```bash
./wifi.sh
```

---

## ⚙️ 9. Atualizar o sistema

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 🛠️ 10. Problemas com atualização

Se não funcionar:

```bash
sudo apt clean
sudo apt autoclean
```

Depois:

```bash
sudo apt update
```

### 🔎 Testar internet

```bash
ping -c 3 google.com
```

---

## 🧑‍💻 11. Instalar o Git

### 📥 Atualizar

```bash
sudo apt update
```

### 📦 Instalar

```bash
sudo apt install git -y
```

### ✅ Verificar

```bash
git --version
```

### ⚙️ Configurar

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@email.com"
```

---

## 📌 Conclusão

Sistema instalado, internet configurada e Git pronto para uso na Banana Pi BPI-M4 Berry e usar o Radar livre 🚀

---

