# composeDNS
# Configura un contenedor con la imagen oficial de bind9 utilizando docker-compose.
 - internetsystemsconsortium/bind9:9.18
## Utiliza los volumenes tal como lo explica en el setup de la imagen
- services:
-     bind9:
-        image: internetsystemsconsortium/bind9:9.18
-        container_name: asir_bind9
-        restart: always
         ports:
-             " - "53:53""
-        volumes:
-              "- ./conf:/etc/bind9"
-              "- ./lib:/var/lib/bind"
-        environment:
-              "- TZ=Europe/Madrid"
## Añade un Readme.md con la descripción de las opciones del docker-compose.yml
- image: la imagen a descargar.
- container_name: nombre que le queremos dar al contenedor.
- ports: El puerto que utilizará.
- volumen: donde estará situado el contenedor.
- environment: Zona donde se va ha hacer
