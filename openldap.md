OPENLDAP
========

LINKS
-----

 * http://code.martini.nu/shelldap - CLI tool for LDAP (recommended)
 * http://linux.die.net/man/1/ldapsearch
 * http://www.rjsystems.nl/en/2100-d6-openldap-provider.php
 * http://www.zytrax.com/books/ldap/
 * http://wiki.rediris.es/gtschema/

SCHEMAS
-------

 * inetOrgPerson: https://tools.ietf.org/html/rfc2798
 * eduPerson: http://software.internet2.edu/eduperson/internet2-mace-dir-eduperson-201602.html
 * schacPersonalCharacteristics: https://www.terena.org/activities/tf-emc2/docs/schac/schac-20061212-1.3.0.schema.txt
 * irisPerson: http://www.rediris.es/ldap/schema/iris.schema  [(+info)](http://www.rediris.es/ldap/esquemas/irisEduPerson.pdf)

TUTORIAL
--------

### Búsquedas


Realizar búsquedas en nuestro directorio. Pongamos algunos ejemplos:

 - Esta búsqueda mostrará todos las entradas del directorio a partirde la rama "dc=setec,dc=com"

```
ldapsearch -x -b 'dc=setec,dc=com' '(objectclass=*)'
```

 - Con esta búsqueda obtendremos los datos del usuario jmsuarez

```
ldapsearch -x -b 'dc=setec,dc=com' uid=jmsuarezo
```

 - Con esta otra buscaremos al usuario jmsuarez en la rama"ou=mad,ou=es,dc=setec,dc=com"

```
ldapsearch -x -b ‘ou=mad,ou=es,dc=setec,dc=com’ uid=jmsuarezo
```

 - Y con esta otra en la rama "ou=us,dc=setec,dc=com" (no mostrará ningún resultado)

```
ldapsearch -x -b ‘ou=us,dc=setec,dc=com’ uid=jmsuarez
```

### Modificación de atributos

Si queremos realizar una modificación de un atributo de una entrada lo haremos creando un archivo LDIF y usando el comando `ldapmodify`. Por ejemplo, queremos cambiar el apellido (sn) a la entrada "uid=jmsuarez", crearemos un archivo LDIF (`ldif4.ldif`) con el siguientecontenido:

```
dn:uid=jmsuarez,ou=mad,ou=es,dc=setec,dc=com
changetype:modify
replace: sn
sn: San Martin
```

Y a continuación ejecutaremos el comando

```
ldapmodify -x -D "cn=root,dc=setec,dc=com" -W -f ldif4.ldif
```

### Borrado de atributos

Si queremos borrar un atributo de una entrada lo haremos creando unarchivo LDIF y usando el comando `ldapmodify`. Por ejemplo, borrar el atributo apellido (sn) de la entrada "uid=jmsuarez",crearemos un archivo LDIF (`ldif4.ldif`) con el siguiente contenido:

```
dn:uid=jmsuarez,ou=mad,ou=es,dc=setec,dc=com
changetype:delete
delete: sn
```

Y a continuación ejecutaremos el comando

```
ldapmodify -x -D "cn=root,dc=setec,dc=com" -W -f ldif4.ldif
```

Podemos comprobar la operación con el comando:

```
ldapsearch -x -b 'dc=setec,dc=com' uid=jmsuarez
```

###  Inclusión de atributos


Si queremos añadir un atributo de una entrada lo haremos creando unarchivo LDIF y usando el comando `ldapmodify`. Por ejemplo, añadir el atributo apellido (sn) a la entrada "uid=jmsuarez", crearemos un archivo LDIF (`ldif4.ldif`) con el siguiente contenido:

```
dn:uid=jmsuarez,ou=mad,ou=es,dc=setec,dc=com
changetype:modify
add: sn
sn: Suarez
```

Y a continuación ejecutaremos el comando

```
ldapmodify -x -D "cn=root,dc=setec,dc=com" -W -f ldif4.ldif
```

Podemos comprobar la operación con el comando:

```
ldapsearch -x -b 'dc=setec,dc=com' uid=jmsuarez
```

###  Modificación de un DN

 Para modificar el DN de una entrada creamos un archivo LDIF (`ldif6.ldif`) con el siguiente contenido

```
dn: uid=msilva,ou=lis,ou=pt,dc=setec,dc=com
changetype:modrdnnewr
dn: uid=msilva2,ou=lis,ou=pt,dc=setec,dc=com
```

Y a continuación ejecutaremos el comando

```
ldapmodify -x -D "cn=root,dc=setec,dc=com" -W -f ldif6.ldif
```

Podemos comprobar la operación con el comando:

```
ldapsearch -x -b 'dc=setec,dc=com' 'uid=msilva*'
```

Borrado de una entrada
---------------------------------------

Si queremos borrar una entrada con todos sus atributos usaremos elcomando `ldapdelete` y a continuación el DN que queremos eliminar:

```
ldapdelete -x -D "cn=root,dc=setec,dc=com" -W "uid=jmsuarez , ou=mad, ou=es, dc=setec, dc=com"
```
