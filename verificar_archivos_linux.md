# Verificación de archivos con debsums y ls -l

## Debsums

Comando `🔹 sudo debsums -c`

¿Qué hace?

Verifica la integridad de los archivos instalados mediante paquetes .deb, comparando sus checksums actuales con los originales del paquete

¿Para qué sirve?

Detecta archivos modificados o faltantes, lo cual puede ser señal de

- Actualizaciones recientes

- Cambios manuales

- Potencial manipulación maliciosa

Si la salida sale vacía todo está bien, else esos archivos difieren de los originales/no existen

---

Comando `ls -l /usr/sbin/group* /usr/sbin/ifconfig`

¿Qué hace?

Muestra permisos, propietario y fechas de modificación de archivos clave

¿Para qué sirve?

Permite verificar si archivos del sistema fueron

- Modificados manualmente

- Sospechosamente alterados

- Coinciden con fechas de instalación/actualización legítimas

Qué mirar en la salida

- El propietario debe ser `root`

- Debe tener permisos normales `-rwxr-xr-x`

- Fechas de modificación deben coincidir con actualizaciones o instalaciones conocidas `(de ser posible)`

---

Usar ambos comandos te permite

- Detectar archivos modificados `debsums -c`

- Inspeccionar manualmente sus metadatos `ls -l`

Esto te da un panorama sólido sobre posibles alteraciones en binarios sensibles del sistema

---

Creado por Favio Joel Zalazar
    
