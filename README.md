# Nociones de Ciberseguridad y otros chiches


# Checklist de Hardening para SSH (OpenSSH)

## 1. Actualización
- [ ] Verificar y mantener OpenSSH actualizado (`>= 9.8p1`)
- [ ] Revisar CVEs recientes (ej: [CVE-2024-6387 - regreSSHion](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-6387))

---

## 2. Configuración de `/etc/ssh/sshd_config`
- [ ] `Protocol 2`  
- [ ] `PermitRootLogin no` o `prohibit-password`  
- [ ] `PasswordAuthentication no`  
- [ ] `PubkeyAuthentication yes`  
- [ ] `PermitEmptyPasswords no`  
- [ ] `ChallengeResponseAuthentication no`  
- [ ] `X11Forwarding no`  
- [ ] `UseDNS no`  
- [ ] `LoginGraceTime 10` (o `0` para máxima seguridad)  
- [ ] `MaxAuthTries 3`  
- [ ] `AllowUsers red` (o grupo limitado)  
- [ ] `Banner /etc/issue.net` (opcional, advertencia legal o personalizada)

---

## 3. Seguridad externa
- [ ] Firewall activo (`ufw`, `iptables`, `firewalld`)  
- [ ] Cambiar puerto SSH (ej: `Port 2222`)  
- [ ] Configurar `fail2ban` para SSH  

---

## 4. Gestión de llaves
- [ ] Usar llaves RSA (4096) o Ed25519  
- [ ] Revocar llaves obsoletas o comprometidas  
- [ ] Usar `~/.ssh/config` para gestionar hosts conocidos  

---

## 5. Monitoreo y alertas
- [ ] Revisar logs: `journalctl -u sshd`, `/var/log/auth.log`  
- [ ] Scripts o notificaciones para accesos sospechosos  
- [ ] `LogLevel VERBOSE` para mayor detalle  

---

> Mantené esta checklist al día y revisala periódicamente ante nuevas vulnerabilidades.
