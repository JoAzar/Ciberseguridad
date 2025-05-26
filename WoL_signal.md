# Configuración y Uso de Wake-on-LAN (WoL) en Linux

## Verificar soporte WoL en la tarjeta de red

```bash
ip link show
```

Identifica el nombre de la interfaz de red y ejecuta

`sudo ethtool <interfaz>`

Busca la línea

Supports Wake-on: ...
Wake-on: ...

La letra g en Supports Wake-on indica soporte para "magic packet" WoL
Si Wake-on está en d, WoL está desactivado

Activar WoL en la interfaz

`sudo ethtool -s <interfaz> wol g`

Configurar WoL para que se active al iniciar la red

Edita el archivo `/etc/network/interfaces`

Agrega o modifica la configuración de la interfaz

`auto <interfaz>
iface <interfaz> inet dhcp
    post-up /sbin/ethtool -s <interfaz> wol g`

Reinicia la red

`sudo systemctl restart networking`

Habilitar WoL en BIOS/UEFI

Entra al BIOS/UEFI y busca la opción relacionada con Wake-on-LAN o WoL y actívala

Desde otra máquina en la misma red, instala wakeonlan si no lo tienes

`sudo apt-get install wakeonlan`

Envía el paquete mágico usando la dirección MAC de la interfaz que tiene WoL activado

`wakeonlan <MAC-address>`

Para ver la MAC de la interfaz

`ip link show <interfaz>`

`link/ether 11:11:11:11:11:11 (MAC)`
