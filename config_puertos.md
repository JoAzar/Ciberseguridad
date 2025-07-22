# 🔐 Recomendaciones de Seguridad en Puertos


Este documento enumera puertos que se recomienda **bloquear a nivel de entrada en el router** para reforzar la seguridad de una red doméstica o pequeña oficina. Se explican los protocolos involucrados, el servicio correspondiente y el motivo por el cual deberían estar cerrados si no se utilizan específicamente

---

# 🧱 Puertos a Bloquear en el Router (Entrada)

| Puerto(s)    | Protocolo | Servicio/Aplicación         | ¿Por qué bloquearlo?                                                                 |
|--------------|-----------|-----------------------------|---------------------------------------------------------------------------------------|
| 23           | TCP       | Telnet                      | Inseguro, transmite en texto plano. Reemplazado por SSH.                             |
| 21           | TCP       | FTP                         | También transmite contraseñas sin cifrar. No recomendado sin TLS/SSL.                |
| 445          | TCP       | SMB / Windows Sharing       | Muy explotado en ataques (EternalBlue, ransomware, etc.).                            |
| 135-139      | TCP/UDP   | NetBIOS / Windows RPC       | Peligroso si se expone a internet. Usado para escaneos, exploits y propagación.      |
| 514          | UDP       | Syslog                      | Sólo necesario internamente. Innecesario y riesgoso si se expone.                    |
| 69           | UDP       | TFTP                        | Muy inseguro, sin autenticación.                                                     |
| 1900         | UDP       | SSDP (UPnP Discovery)       | Abusable para ataques DDoS por reflexión (como Mirai Botnet).                        |
| 111          | TCP/UDP   | RPCBind / NFS               | Vulnerabilidades frecuentes en sistemas antiguos de archivos compartidos.           |
| 161-162      | UDP       | SNMP                        | Riesgo de exposición de configuración y datos de red.                                |
| 520          | UDP       | RIP                         | Protocolo de enrutamiento obsoleto.                                                  |
| 1433         | TCP       | Microsoft SQL Server        | Bloquear si no se expone a internet. Vulnerable a ataques automatizados.            |
| 3306         | TCP       | MySQL                       | Igual que el anterior, bloquear si no se accede desde fuera de la red local.         |
| 80           | TCP       | HTTP                        | ⚠️ Solo bloquear si no usás servicios web internos. De lo contrario, dejar abierto.  |
| 8080         | TCP       | HTTP Alternativo            | ⚠️ Igual que el 80, depende de si lo usás para servidores o servicios internos.       |

---

## ✅ Recomendaciones Adicionales

- **No bloquear puertos sin saber para qué sirven.** Consultá siempre antes de cerrar algo esencial para el funcionamiento de tu red o dispositivos

- **Desactivar UPnP** si no lo necesitás. Puede abrir puertos automáticamente sin tu autorización explícita

- **Bloqueá todo lo que no uses**, y habilitá solo lo que realmente necesités (modelo de seguridad por denegación predeterminada)

- Usá herramientas como `nmap` para escanear los puertos abiertos en tu red y verificar la exposición

---

## 🧩 Puertos HTTP comunes: 80 y 8080

### 🔸 Puerto 80 (HTTP)

- 📤 **Entrada (desde Internet hacia tu red)**

  - ❌ **Bloquear si no tenés un servidor web corriendo.**
  - ✅ **Dejar abierto solo si necesitás servir una web pública.**

- 📥 **Salida (desde tu red hacia Internet)**

- ✅ **No bloquearlo.** Algunas páginas aún redirigen desde HTTP antes de llegar a HTTPS.

---

### 🔸 Puerto 8080 (HTTP alternativo, usado por proxies o paneles web)

- 📤 **Entrada**

  - ❌ **Bloquear si no lo usás.** Muchos paneles web de administración lo usan

  - ✅ **Abrir solo si es necesario para un servicio específico.**

- 📥 **Salida**

  - ✅ Puede dejarse abierto

  - 🔍 Si querés ser más estricto, analizá si alguna app lo necesita primero

---

## ✅ Resumen

| Puerto | Entrada (desde Internet) | Salida (desde red interna) |
|--------|--------------------------|-----------------------------|
| **80**     | ❌ Bloquear si no se usa web | ✅ Mantener abierto          |
| **8080**   | ❌ Bloquear si no se usa    | ✅ o 🔍 revisar antes         |

---

## Consejo

Si querés máxima seguridad

- 🔒 **Bloqueá ambos en entrada**

- 🚪 **Dejá salida abierta** salvo que sepas exactamente qué tráfico querés evitar

---

Creado por Favio Joel Zalazar
