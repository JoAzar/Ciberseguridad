# Checklist de Hardening para SSH (OpenSSH)

(Solo para el servidor no para el cliente)

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

### Seguridad para el Cliente SSH

Es importante asegurarte de que tu máquina cliente (desde donde te conectas) esté bien protegida. Algunas prácticas para mejorar la seguridad en tu máquina cliente incluyen:

## Uso de claves SSH

Usar claves SSH para autenticarte en lugar de contraseñas. Esto es más seguro, ya que las claves públicas y privadas son mucho más difíciles de adivinar o robar que una contraseña. Al generar las claves, se utiliza un par de claves, y tu máquina cliente solo usa la clave privada para acceder a servidores que tengan la clave pública correspondiente.

## Protección de la clave privada
*Si usas autenticación con claves SSH, asegúrate de que tu clave privada (~/.ssh/id_rsa) esté protegida adecuadamente
*No compartirla
*Usar una contraseña de protección para la clave privada si la estás generando (se recomienda usar una passphrase).

## Firewall y medidas locales
Aunque en general el firewall en el cliente SSH no es tan crítico, es una buena práctica habilitar un firewall y asegurarte de que solo se permita el acceso a puertos necesarios.
Podes configurar el firewall para permitir solo ciertas conexiones de red, lo que evitará que tu máquina cliente sea vulnerable a accesos no autorizados.

##Verificar las huellas digitales del servidor:
Cuando te conectas por SSH a un servidor por primera vez, SSH te pedirá que confirmes la huella digital de la clave pública del servidor al que te estás conectando. Esto es una medida de seguridad para evitar que te conectes a un servidor falso (lo que podría ser parte de un ataque de "man-in-the-middle").

´´´Siempre verifica que la huella digital coincida con la que te proporcionaron administradores del servidor, especialmente si es la primera vez que te conectas.´´´

## Actualizaciones de seguridad
Asegúrate de que tu máquina cliente tenga actualizaciones de seguridad instaladas, especialmente las relacionadas con la criptografía y las herramientas SSH. Mantener tu sistema actualizado reduce el riesgo de vulnerabilidades conocidas.

---

> Mantené esta checklist al día y revisala periódicamente ante nuevas vulnerabilidades.
