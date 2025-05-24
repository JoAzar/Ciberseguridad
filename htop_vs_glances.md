# Informe Comparativo de Seguridad: htop vs Glances

| Aspecto                        | htop                                                                              | Glanses
|--------------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------
| **Naturaleza**                 | Herramienta local para monitoreo de procesos y recursos del sistema.              | Herramienta de monitoreo que puede operar localmente o en modo servidor con acceso remoto.                                |
| **Exposición de red**          | No abre ningún puerto, no escucha conexiones. Funciona solo en consola local.     | Puede abrir puertos para interfaz web o API remota, expone servicios a la red.                                            |
| **Superficie de ataque**       | Muy baja, ya que no hay comunicación ni puertos abiertos.                         | Mayor, debido a que la escucha de puertos aumenta el riesgo de ataques remotos si no se configura bien.                   |
| **Autenticación y seguridad**  | No aplica (no hay red ni autenticación).                                          | Soporta autenticación y configuraciones para limitar accesos, pero depende de la correcta implementación y mantenimiento. |
| **Configuración de seguridad** | No requiere configuración especial para seguridad, dado que no expone nada en red.| Requiere configuración cuidadosa para restringir accesos, uso de firewalls, VPN, y posibles cifrados.                     |
| **Riesgos potenciales**        | Solo riesgos locales (privilegios, ejecución de comandos).                        | Riesgos de exposición remota, posibles vulnerabilidades CVE relacionadas con el servidor web integrado o APIs.            |
| **Casos de uso ideales**       | Uso local y seguro en terminales o servidores sin necesidad de monitoreo remoto.  | Monitoreo remoto, integración con sistemas externos, generación de alertas y reportes automáticos.                        |
| **Mantenimiento**              | Muy bajo, actualización puntual de la herramienta.                                | Mayor, requiere actualizar y revisar configuraciones de red y seguridad constantemente.                                   |

---

## Conclusión

- Si priorizas **seguridad y simplicidad** y solo necesitas monitoreo local, **htop es la opción más segura y confiable**
  
- Si necesitas **monitorización remota o integración avanzada**, puedes usar **Glances**, pero siempre configurando adecuadamente la seguridad de red y autenticación para minimizar riesgos
  
- Para un uso seguro con Glances, limita el acceso al puerto solo a redes confiables, usa VPNs o túneles SSH, y mantenlo siempre actualizado para evitar vulnerabilidades conocidas

---

# Recomendación personal (queda a gusto de cada quien tomarlo o dejarlo)


### Monitoreo remoto con SSH y htop

- **Seguridad:**  
  SSH ofrece un canal cifrado y autenticado para acceder remotamente al sistema, sin necesidad de abrir puertos adicionales para monitoreo.

- **Funcionamiento:**  
  Desde otra computadora, se conecta por SSH al servidor y ejecuta `htop` en la terminal remota, visualizando el uso de recursos y procesos en tiempo real.

- **Ventajas:**  
  - No se expone ningún puerto extra ni servicio web.  
  - Usa el mismo canal seguro que para cualquier administración remota.  
  - Reduce la superficie de ataque al mínimo.  
  - No requiere configuraciones adicionales de servicios o autenticación fuera del SSH.

- **Desventajas:**  
  - No tiene interfaz gráfica web ni reportes automáticos.  
  - Es necesario tener acceso SSH configurado y permisos adecuados.

**Conclusión:** Para monitoreo remoto seguro sin abrir puertos extras, usar SSH con herramientas como `htop` es una solución muy eficaz y recomendada si no se requiere interfaz web o integración avanzada

Creado por Favio Joel Zalazar
