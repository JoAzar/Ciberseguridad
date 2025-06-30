# Apt-listbugs

## ¿Para qué sirve?

- Muestra bugs de los paquetes que estás a punto de instalar o actualizar. Estos errores provienen del sistema de seguimiento de errores de Debian

## ¿Por qué es útil?

- Para evitar que una actualización rompa tu sistema. Te permite decidir si seguir con la instalación o no

## Ejemplo de uso
Si ejecutás sudo apt upgrade, y el paquete libxyz tiene un bug grave reportado, apt-listbugs te lo va a mostrar y te dará la opción de cancelar la instalación


## Instalación

`sudo apt install apt-listbugs`

### Se integran automáticamente al proceso de instalación/actualización con APT 

---

Creado por Favio Joel Zalazar

fuente https://manpages.debian.org/testing/apt-listbugs/apt-listbugs.1.en.html
