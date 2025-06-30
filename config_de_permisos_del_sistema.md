# Configuración de permisos de seguridad

## Verificamos

`ls -l /etc/sudoers.d`

## Modificamos permisos

`sudo chown root:root /etc/sudoers.d/*`
`sudo chmod 440 /etc/sudoers.d/*`

## Archivo	Permisos

`/etc/shadow	600	-rw-------`	Solo root puede leer y escribir. Nadie más puede ver nada

`/etc/passwd	644	-rw-r--r--`	root puede escribir. Todos pueden leer

`/etc/group	644	-rw-r--r--`	Igual que /etc/passwd, pero para grupos

`/etc/gshadow	600	-rw-------`	Solo root puede leer y escribir. Contiene contraseñas de grupo

### Estos permisos se pueden mejorar aún más quitando los permisos de `grupo`

## Para recordar

# Permisos

## R read/lectura | W write/escritura | X execute/ejecución

| Usuario - Grupo - Otros |
---------------------------
| R W X - R W X - R W X   |

---

Creado por Favio Joel Zalazar
