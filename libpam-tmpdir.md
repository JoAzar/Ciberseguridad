# libpam-tmpdir

## ¿Para qué sirve?

Es un módulo que cambia la ubicación de las variables de entorno TMP y TMPDIR para que cada usuario tenga su propio directorio temporal en lugar de usar el directorio global `/tmp`

## Beneficios

✅ Mejora la seguridad

- Evita que varios usuarios compartan el mismo /tmp, lo que:

    Reduce riesgos de ataques de tipo symlink o inseguridad por archivos temporales compartidos

    Aísla procesos de distintos usuarios

✅ Privacidad

- Los archivos temporales de cada usuario quedan fuera del alcance de otros usuarios no privilegiados

✅ Orden y mantenimiento

- Facilita la limpieza automática y el monitoreo de los archivos temporales por usuario

## ¿Cómo funciona?

Cuando se inicia sesión (por ejemplo en consola, escritorio o ssh), PAM configura variables `tmp`

## Instalación

`sudo apt install libpam-tmpdir`

Luego de instalar, agregar a la configuración PAM de los servicios, por ejemplo en `/etc/pam.d/common-session` -> `session optional pam_tmpdir.so`

---

Creado por Favio Joel Zalazar

Fuente https://packages.debian.org/sid/admin/libpam-tmpdir
