# LDAP
Lightweight access repository, es un servicio que corre en linux que permite la autenticación de usuarios en un lugar centralizado.

## Instalación en Centos 8 
En los repos de Centos 8 no existe openldap-server, hay que construirlo a partir de los binarios. Para esto: https://computingforgeeks.com/install-configure-openldap-server-centos/

## Migrar un servidor LDAP
1. Se crea un backup de la configuracion: `slapcat -n 0 -l config.bck`
2. Se crea un backup de la base de datos: `slapcat -n 1 -l db.bck`
3. En el nuevo server:
	1. Se elimina el folder de configuración `sudo rm -rf /etc/ldap/slapd.d` (ó openldap)
	2. Se agregan las configuraciones `sudo slapadd -n 0 -F /etc/ldap/slapd.d -l config.bck`
	3. Se agregan las entradas de la db: `sudo slapadd -n 1 -l db.bck`

### Configuraciones en la parte del cliente
Una vez agregadas las configuraciones pertinentes con `authconfig-tui`, se deben reiniciar los servicios de `nslcd` y `nscd` para que se comiecen a agarrar nuevos usuarios.

## Ejemplo de búsqueda en LDAP
``ldapsearch -x -LLL -b "dc=cnca,dc=cenat" uid=kzeledon uid``