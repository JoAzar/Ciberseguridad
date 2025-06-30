# 🔒 Desactivación Segura de Bluetooth en Linux

Este archivo documenta cómo desactivar completamente el soporte de Bluetooth en sistemas Linux para mejorar la seguridad, privacidad y estabilidad de red

---

## 🧠 ¿Por qué desactivar Bluetooth?

Aunque no lo uses, Bluetooth puede

- Compartir el espectro de 2.4GHz con Wi-Fi y generar interferencia

- Abrir puertos y sockets (SCO, PAN, etc.) innecesarios

- Ser explotado por aplicaciones o servicios en segundo plano

- Anunciar presencia o aceptar conexiones sin consentimiento

---

## ✅ Qué logramos desactivando el Bluetooth

- Red más tranquila, sin tráfico innecesario

- Menos consumo de recursos

- Mayor control sobre qué dispositivos pueden interactuar con mi sistema

- Sin sockets Bluetooth ni interfaces `bnep0`, `rfcomm`, etc

---

## 🔧 Cómo desactivar Bluetooth correctamente

### 1. Desactivar el servicio Bluetooth

```bash
sudo service bluetooth stop
sudo update-rc.d bluetooth disable
```

---

2. Bloquear módulos del kernel relacionados


sudo nano /etc/modprobe.d/blacklist-bluetooth.conf

Pegá lo siguiente:

```bash
blacklist bluetooth
blacklist btusb
blacklist btrtl
blacklist btbcm
blacklist btintel
blacklist hci_uart
blacklist rfcomm
blacklist hidp
blacklist bnep
```

---

3. Regenerar initramfs para aplicar el bloqueo

sudo update-initramfs -u


---

4. Reiniciar el sistema

sudo reboot


---

5. (Opcional) Evitar reactivación automática con udev

sudo nano /etc/udev/rules.d/81-disable-bluetooth.rules

Pegá esto

```bash
SUBSYSTEM=="bluetooth", ATTR{enable}="0", ATTR{powered}="0"
```

---

🔍 Verificación

Ver si hay módulos cargados

lsmod | grep -i bluetooth

Ver si el servicio está activo

service bluetooth status


---

🛡️ Resultado

Con estos pasos

- Eliminás soporte Bluetooth del sistema

- Cerrás posibles vectores de ataque

- Mejorás la estabilidad de red si había interferencias

- Mantenés todo sin romper servicios dependientes como pulseaudio o network-manager


---

Creado por Favio Joel Zalazar

---
