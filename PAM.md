# ¿Qué es PAM? (Pluggable Authentication Modules)

## Es un sistema flexible y modular de autenticación utilizado por muchas distribuciones de Linux

## ¿Qué hace PAM?

PAM permite gestionar la autenticación de usuarios de forma centralizada y configurable. Es como un conjunto de reglas que determina quién puede acceder, cómo y con qué condiciones

## PAM interviene cuando

- Inicias sesión en la terminal o escritorio

- Usás sudo

- Accedés por SSH

- Bloqueás o desbloqueás la pantalla

- Abrís una sesión gráfica o de consola

## ¿Qué tipos de tareas maneja PAM?

- `auth` 	Autenticación (verificar usuario y contraseña)

- `account`	Control de acceso (¿puede este usuario iniciar sesión?)

- `password`	Cambios de contraseña

- `session`	Tareas al iniciar/cerrar sesión (como pam_tmpdir)

## Módulos más comunes/conocidos

- `pam_unix.so`	Autenticación clásica con /etc/passwd y /etc/shadow
- `pam_tally2.so`	Contador de intentos fallidos, bloqueo por fallos
- `pam_faillock.so`	Bloqueo por intentos fallidos también
- `pam_env.so`	Carga variables de entorno
- `pam_tmpdir.so`	Crea un /tmp por usuario
- `pam_exec.so`	Ejecuta un script al autenticarse

## ¿Por qué es importante?

PAM te permite mejorar la seguridad fácilmente aunque hay que manejarlo con mucho cuidado ya que podrías bloquear el sistema
