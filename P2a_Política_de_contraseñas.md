# Política de contraseñas

## Contexto
Por defecto, la mayoría de sistemas operativos, vienene con una política de contraseña muy laxa, una contraseña segura presenta una barrera más al atacante, que en su intento de acceder al sistema, indudablemete dejará más rastro y en algunos casos a provocar el abandondo de ataque.

## Objetivos
* Entender el sistema de contraseñas del sistema operativo linux

En el archivo /etc/passwd se almacena toda la infomación del usuario, antes la contraseña tambien se encontgraba ahi, pero ahora aparece una x y la contraseña se almacena en otro archivo mas seguro /etc/shadow en un informe encriptado que solo los administradores tienen acceso.

* Entender el PAM (Plugable authentication Module)
  
PAM es un sistema que trabaja en cuando un usuario intenta acceder al sistema por ssh o utilizar sudo, verifica que permisos puede tener.

* Instalar y configurar la libreria _pwquality_
* Comprobar y verificar que se ha llevado la práctica de forma correcta
* Documentar la práctica.

### Contaseña debíl

* Tener minimo 6 caracteres: score entre 40 y 50. 
  

  #### restriciones y Pruebas: 
 ```bash
   minlen = 6
   dictcheck = 0 
   ucredit = -1 
   dcredit = -1
   lcredit = -1
   ocredit = -1
   ```

```bash 
vagrant@generic-sad:~$ echo "e4Lm@i" | pwscore
38
```

```bash 
vagrant@generic-sad:~$ echo "AsiR*8" | pwscore
38
```

```bash 
vagrant@generic-sad:~$ echo "@sIr/7" | pwscore
38
```

### Contraseña Media

* Tener minimo 8 caracteres
* tener numero, letras maiusculas y simbolos.
#### Restriciones y Pruebas
 ```bash
   minlen = 8
   dictcheck = 0 
   ucredit = -1 
   dcredit = -1
   lcredit = -1
   ocredit = -1
   ```

```bash 
vagrant@generic-sad:~$ echo "Az34X.9~@" | pwscore 
56
```

```bash 
vagrant@generic-sad:~$ echo "AsiR_2425" | pwscore 
50
```

```bash 
vagrant@generic-sad:~$ echo "xR5M_U7j" | pwscore 
40
```

#### Contraseña Fuerte

* Tener 10 caracteres minimo
* Numeros Letras Simbolos.

#### Restriciones y Pruebas

 ```bash
   minlen = 12
   dictcheck = 0 
   ucredit = -2
   dcredit = -1
   lcredit = -1
   ocredit = -1
   ```

```bash 
vagrant@generic-sad:~$ echo "=GtrA_01hy* ̣" | pwscore 
63
```

```bash 
vagrant@generic-sad:~$ echo "Gxd_\@·A15* ̣" | pwscore 
72
```

```bash 
vagrant@generic-sad:~$ echo "Gxd_\@·A[5* ̣" | pwscore 
75
```

