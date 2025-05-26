# Linux con zRAM

## ¿Por qué zRAM es mejor que el swap tradicional?

El sistema de swap tradicional en Linux usa el **disco duro o SSD** para almacenar datos que no caben en la RAM. Aunque útil, esto tiene dos grandes problemas

- **Es lento**: incluso los SSD son mucho más lentos que la RAM

- **Desgasta el disco**: especialmente los SSD, con cada escritura

**zRAM** resuelve este problema al crear un bloque de **swap comprimido dentro de la misma RAM**

- **Ahorra espacio de RAM** al comprimir los datos poco usados

- **Aumenta el rendimiento**, porque acceder a RAM comprimida es mucho más rápido que al disco

- **Evita el desgaste de tu disco**

Ideal para equipos con poca RAM, netbooks, servidores pequeños o sistemas embebidos

---

## ¿Cómo activar zRAM en Linux?

### 1. Instalá los paquetes necesarios

```bash
sudo apt install zram-tools
```

### Editá el archivo de configuración

`sudo nano /etc/default/zramswap`

### Ejemplo de configuración básica

```bash
ENABLED=true
ALGO=zstd       #zstd = buena compresión, lz4 = más rápido
PERCENT=50      #Porcentaje de RAM que se usará como zRAM
```

### Activá zRAM

`sudo systemctl restart zramswap`

