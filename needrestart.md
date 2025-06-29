# Needrestart

## Se utiliza para verificar qué servicios deben reiniciarse después de una actualización del sistema en Fedora y Ubuntu

## Instalación

`sudo apt update && sudo apt install needrestart`

## Comandos interesantes

1. Muestra qué servicios debe reiniciarse `restart -s`
2. Reinicio del sistema solo si el kernel cambió `restart -r l`
3. Corre en modo batch (sin interacción) `restart -b`

## Automatizar reinicio (no recomendado)

`sudo nano /etc/needrestart/needrestart.conf`

- a = automático
- 1 = solo kernel
- n = nunca
- i = interactivo

```bash
$nrconf{restart} = 'a';
```


Creado por Favio Joel Zalazar

Fuente https://www.baeldung.com/linux/check-service-needs-restart
