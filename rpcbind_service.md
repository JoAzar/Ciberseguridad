# Securizar rpcbind y servicios RPC en Linux

## ¿Qué es `rpcbind`?

`rpcbind` es un servicio que mapea los programas RPC (Remote Procedure Call) a los puertos donde están escuchando, permitiendo que otros programas puedan localizarlos y comunicarse con ellos. Es fundamental para servicios como NFS (Network File System).

## ¿Por qué puede ser un riesgo de seguridad?

- Expone puertos dinámicos usados por servicios RPC.
- Puede revelar información sobre servicios activos en el sistema.
- Vulnerable a ataques de denegación de servicio (DoS) o, en versiones antiguas, ejecución remota de código.
- Exponer `rpcbind` en redes públicas puede permitir ataques externos.

## ¿Cuándo es seguro mantenerlo activo?

- Si usás NFS para compartir archivos en red
- Si necesitás servicios que dependan de RPC

## ¿Cómo identificar si `rpcbind` está activo?

Ejecutá:

```bash
sudo ss -ltnp | grep rpcbind
```

También podés ver puertos abiertos relacionados (111 TCP/UDP y puertos dinámicos)

## ¿Cómo desactivarlo si no es necesario?

### Parar los servicios

`sudo service rpcbind stop && sudo service nfs-common stop`

### Evitar que se inicien al arrancar

`sudo update-rc.d rpcbind disable && sudo update-rc.d nfs-common disable`

### Confirmar que no hay montajes NFS activos

`mount | grep nfs`

### Verificar que los puertos estén cerrados

`sudo ss -ltnp | grep 111`

### Eliminar por completo

`sudo apt remove --purge rpcbind nfs-common`

### Recomendaciones adicionales

Si necesitás usar rpcbind, no exponer el puerto 111 a Internet

### Configurar un firewall para bloquear accesos externos

`sudo ufw deny from any to any port 111 proto tcp`
`sudo ufw deny from any to any port 111 proto udp`

---

# A tener en cuenta

---

# Vulnerabilidades recientes en rpcbind

### CVE-2017-8779 – Denegación de servicio (DoS) por consumo de memoria

**Descripción**:  
Las versiones de `rpcbind` anteriores a la **0.2.4**, junto con `libtirpc` hasta la **1.0.2-rc3** y `ntirpc` hasta la **1.4.3**, no consideran el tamaño máximo de los datos RPC al asignar memoria para cadenas XDR. Esto permite que atacantes remotos envíen paquetes UDP maliciosos al puerto 111, causando un **consumo excesivo de memoria** y una **denegación de servicio**.

🔗 [Ver en GitHub Advisory](https://github.com/advisories/GHSA-fr7x-wc8q-h255)  
🔗 [Ver en OpenCVE](https://app.opencve.io/cve/CVE-2017-8779)

**Estado**:  
A pesar de su antigüedad, esta vulnerabilidad sigue siendo relevante en sistemas que no han sido actualizados.

---

### CVE-2010-2064 – Escritura arbitraria de archivos mediante enlaces simbólicos

**Descripción**:  
La versión **0.2.0** de `rpcbind` permite a usuarios locales escribir en archivos arbitrarios mediante un ataque de enlace simbólico en los archivos `/tmp/portmap.xdr` y `/tmp/rpcbind.xdr`. Esto puede llevar a la **ejecución de código con privilegios elevados**

🔗 [Ver en OpenCVE](https://app.opencve.io/cve/CVE-2010-2064)

**Estado**  
Aunque es una vulnerabilidad antigua, sigue siendo importante para sistemas que aún no han sido parchados

---

**Recomendación**: Mantené `rpcbind` y sus dependencias siempre actualizadas o desinstalalo si no lo necesitás
