#console

* ip address
	ip show addr

* disk space
	df -H

# passwd

```bash
sudo passwd
```

- **-a o –all**: esta opción, en combinación con la opción -s, garantiza que recibas información sobre todos los usuarios.
- **-d o –delete**: esta opción permite desactivar una contraseña.
- **-e o –expire**: esta opción hace que la contraseña pierda su validez. En el próximo inicio de sesión, se deberá determinar una nueva contraseña con el comando passwd.
- **-i o –inactive [Días]**: esta opción permite determinar cuándo debe eliminarse una cuenta. Aquí se tiene en cuenta el número de días que un usuario ha estado inactivo después de que su contraseña haya caducado.
- **-k o –keep-tokens**: esta opción limita las opciones de cambio para las contraseñas que ya han caducado.
- **-l o –lock**: esta opción permite bloquear la contraseña de un usuario.
- **-n o –mindays [Días]**: esta opción permite determinar el mínimo de días que hay que esperar antes de poder volver a cambiar la contraseña.
- **-S o –status**: esta opción muestra los valores actuales de un usuario.
- **-u o –unlock**: esta opción anula la opción -l o –lock.
- **-w o –warndays [Días]**: esta opción se utiliza para avisar a un usuario de que una contraseña está a punto de caducar. El parámetro “[Días]” determina con cuánto tiempo de antelación debe enviarse el aviso.
- **-x o –maxdays [Días]**: esta opción determina después de cuántos días debe renovarse una contraseña.
## SSH

Remove host fingerprint:
```bash
ssh-keygen -f "/home/dev/.ssh/known_hosts" -R "172.18.22.61"
```

https://www.youtube.com/watch?v=ShcR4Zfc6Dw&ab_channel=Fireship

https://blog.desdelinux.net/el-kernel-de-linux/