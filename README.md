## What is Pi-hole?

![Image](https://images.openai.com/static-rsc-4/EFipC4yLAOukgIv7RhJFbU7s69c9jNOhpJUEJXSaTrEibgku0VJkOYUNH7-knAdznJuTR6b9MOLD0FeGWizknEZ2Eg4sdY8ExZDoEaeVIQUPnfsL_22ag8QUTAR4oBZuJlA7T8cBrJTExRPx7V_RNVj_wYUF7LMvRupNr0n8Jz-2BGtb6QcKsZrgfqeyqu7Q?purpose=fullsize)



[Pi-hole Official Website](https://pi-hole.net/?utm_source=chatgpt.com)
[Pi-hole Documentation](https://docs.pi-hole.net/?utm_source=chatgpt.com)

Pi-hole is a network-wide DNS blocker that blocks ads, trackers, and malicious domains for every device on your network.

You can run it on:

* Raspberry Pi
* Old PC
* VM
* Docker
* VPS
* Home server

---

# Before Installing

## Recommended

* Static IP address
* Fresh Linux install
* At least:

  * 512 MB RAM
  * 2 GB storage


---

# 1. Install Pi-hole on Debian / Ubuntu

# Update your system first


```bash
sudo apt update && sudo apt upgrade -y
```

## Install curl

```bash
sudo apt install curl -y
```

## Run the installer

```bash
curl -sSL https://install.pi-hole.net | bash
```

OR

```bash
wget -O basic-install.sh https://install.pi-hole.net
sudo bash basic-install.sh
```

---

## Installer Questions

During setup:

* Choose DNS provider

  * Cloudflare
  * Google
  * Quad9
* Select interface

  * usually `eth0` or `wlan0`
* Confirm static IP
* Enable:

  * Web Admin Interface
  * Query logging

---

## After Installation

Admin panel:

```text
http://YOUR-IP/admin
```

Example:

```text
http://192.168.1.10/admin
```

Show password:

```bash
pihole -a -p
```

---

# 2. Install Pi-hole on Red Hat / Fedora

## Update your system first


```bash
sudo dnf upgrade --refresh -y
```

![Image](https://images.openai.com/static-rsc-4/QOeDOp9nhPzyKdFKYMTmH8NxmpXvhDE6Y_i8wQYTNQ_fXtIUHn0GEk6i02aHSOsY9x56qzDMdg6kCP2uE3I13JvJvB6oPSKJRYFowBybCzj2wfVzvgtsVuUe2VmeEHQcwk6vqlNnjtF5SFfu9LFFGrFbr6hB1652ID-QXmcHOmR61WiVy3qJ2ZyXtdNo9nj4?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/qSrMOCMW4HzFQlVe8kwsrWY3J9YChIwounfYTkumf5mNmIBB3Xuna3AJB6b_whxzhkjEbMuMVbQsFoKOdzJWa9L4ZAH_GyVl6ufAt_OnEUVeR0VWnDKoPp_SImjVN2XH7r9SDE2WQjuqc8f_iu09joefdXxOYHok_atOM1Hny1wPHM2zbeAO_uhsSrHaRBJJ?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/QOeDOp9nhPzyKdFKYMTmH8NxmpXvhDE6Y_i8wQYTNQ_fXtIUHn0GEk6i02aHSOsY9x56qzDMdg6kCP2uE3I13JvJvB6oPSKJRYFowBybCzj2wfVzvgtsVuUe2VmeEHQcwk6vqlNnjtF5SFfu9LFFGrFbr6hB1652ID-QXmcHOmR61WiVy3qJ2ZyXtdNo9nj4?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/POaIrw_tMF3NMgWUMR7yKC3cuO9CkozikmjWuxcp5kgPkh1Nn11muqumN7p0B7RiEF91TnX1awRjGwd3niqUSifMRAeDY8rMUKPcCxwV3mVkTfBB4_s42gDySDPsFq12PilD35MTEKsIXh5mU1PcoTdeIlEts1rA5JJGhQdpCh_NNWGlr-USuB-1aWUgUNja?purpose=fullsize)

## Install required packages

```bash
sudo dnf install curl wget git -y
```

## Run installer

```bash
curl -sSL https://install.pi-hole.net | bash
```

---

## Open firewall ports

```bash
sudo firewall-cmd --permanent --add-service=dns
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
```

---

## SELinux (if needed)

If web interface has problems:

```bash
sudo setenforce 0
```

Permanent:

```bash
sudo nano /etc/selinux/config
```

Change:

```text
SELINUX=enforcing
```

to:

```text
SELINUX=permissive
```

---

# 3. Install Pi-hole on Arch Linux

# Update your system first


```bash
sudo pacman -Syu
```

![Image](https://images.openai.com/static-rsc-4/Z9hdl5ycQw6NJR7t2ckCDxhScz40JiM0Q6Mp4ssIs8udPZz1ZCJerWHJmaFeMUHNg58Eq1pyDoVFSjjFePvwbYHiKx5epaNGLjrD8-2ntIz9Dcdgbl39rsv7mqbTf5y0APnFPDWmzCvfSycbp6bMokpSkpbVCaHybfU0Ih2nWmPKVodVMiiEog7csegLYdiN?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/BSnYZVp_UqdPPMFWmy4i4qdVLm21jVYn3Mqnrrsqxg1fSvSUbyLVfOtq8a3fObPYbw4IIGeC8EwENfchBXtQTMXnYJI8dPFx1I2rlZlPrB2nfdf8R8-pm2Y3Z5Y2YOYaJCXEpu8NBwwg-ukjU9qfJg-ZYoWMk8I_M3H5GJuWifho--YwMhM1yWrkVw99ShyR?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/NP8KIjDK0vSh_34mg-m6oMVkLt9rzh8jCAthXKBuDfF_6wbfUNRXZcuxSWzs7OW18QsOIu2fdlcWN2l-7p9vhWos9MDtYRg4cvHcnGVmdwKti8M6eO0Z5cLRJ9NwIC01fkF5TN4xBZMznOuminl5-glQ3REe_2dIcjJvjjTH3mkamFiiTanoHTHn_8PAKoXe?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/Q18l7FkW1dVhha_BKD_3oxwBOZbDz2uw9Y39w6Hdn_n0TQwDdLeBMT2v-3AQ5j28-E7ujIzEvZYeTL5D6eL50BEtZVEXNfIvKdGcnlIt-PY5BXhSzfpVdPHUEXLu8FhD06mrSxz-zP04mKXXWanxgTexYXBAtkdE7mX9kHMP4_2g6Sfw9sc5mk6AxKUYClig?purpose=fullsize)

Pi-hole is not officially supported on Arch, but works well.

## Install dependencies

```bash
sudo pacman -S curl git base-devel
```

---

## Method 1 (Recommended): Official Installer

```bash
curl -sSL https://install.pi-hole.net | bash
```

---

## Method 2: AUR

Install an AUR helper like paru:

```bash
sudo pacman -S --needed base-devel git

git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

Install Pi-hole:

```bash
paru -S pi-hole-server
```

---

# Set Pi-hole as Your DNS

After installation, set your router DNS to your Pi-hole server IP.

Example:

```text
Primary DNS: 192.168.1.10
```

Then every device on your network uses Pi-hole automatically.

---

# Useful Pi-hole Commands

## Update Pi-hole

```bash
pihole -up
```

## Check status

```bash
pihole status
```

## Restart DNS

```bash
pihole restartdns
```

## Tail logs

```bash
pihole -t
```

## Disable blocking temporarily

```bash
pihole disable 5m
```

---

# Recommended Setup for You

Since you already have:

* Raspberry Pi
* Old office PC
* Linux experience
* KVM/libvirt setup

Good options:

1. Raspberry Pi 5 + Debian Lite
2. Fedora/Arch VM in KVM
3. Old office PC as dedicated home server

---

# Docker Method (Works Everywhere)

[Pi-hole Docker Guide](https://docs.pi-hole.net/docker/?utm_source=chatgpt.com)

Example:

```bash
docker run -d \
  --name pihole \
  -p 53:53/tcp \
  -p 53:53/udp \
  -p 80:80 \
  -e TZ="Asia/Kolkata" \
  -e WEBPASSWORD="password" \
  --restart=unless-stopped \
  pihole/pihole
```

---

# Recommended Extras

You can pair Pi-hole with:

* Unbound
* WireGuard
* Home Assistant
* Jellyfin

For a full homelab setup.
