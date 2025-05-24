# Memoria swap en Linux

## ¿Qué es la memoria swap?

La memoria swap es un espacio en disco que se utiliza como extensión de la memoria RAM cuando ésta se encuentra llena. Sirve para "intercambiar" páginas de memoria que no se usan activamente, permitiendo que el sistema siga funcionando sin quedarse sin memoria

## Configuración actual del sistema (ejemplo)

- Memoria RAM total: 32,0 GiB
- Memoria swap total: 10,0 GiB  
- Swap usado: 500 MiB  
- Swap libre: 9,5 GiB

## Ubicación y configuración del swap

Si en el archivo `/etc/fstab` aparece configurado `/swap/swap swap swap defaults 0 0`

Esto indica que el espacio de swap está ubicado en la ruta `/swap/swap` y está activado con los parámetros por defecto

## Estado actual del swap

El sistema tiene 10 GiB de swap activos, de los cuales 500 MiB están en uso. Esto significa que la memoria RAM se está utilizando principalmente, pero el sistema usa swap para mejorar la gestión de la memoria y evitar que las aplicaciones se queden sin memoria disponible.

## Conclusión

Tener swap activo es útil incluso en sistemas con RAM suficiente, ya que permite manejar picos de uso y mantener la estabilidad del sistema.

---

# Cómo genero mi swap si no lo tengo?

---

## Pasos para crear un archivo de swap

1. **Crear un archivo de swap**  
Decide el tamaño del swap que deseas crear (por ejemplo, 2 GiB):

```bash
sudo fallocate -l 2G /swapfile
```

Si fallocate no está disponible, puedes usar `sudo dd if=/dev/zero of=/swapfile bs=1M count=2048`

Asignar permisos correctos

El archivo de swap debe tener permisos restrictivos `sudo chmod 600 /swapfile`

### Configurar el archivo como swap

`sudo mkswap /swapfile`

### Activar el archivo swap

`sudo swapon /swapfile`

### Verificar que el swap está activo

`sudo swapon --show && free -h`

### Hacer que el swap sea persistente en el arranque (que no se borre la configuración al reiniciar el sistema)

Añade la siguiente línea al archivo `/etc/fstab`

`/swapfile none swap sw 0 0`


