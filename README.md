# COMPOSEdns
# Configura un contenedor con la imagen oficial de bind9 utilizando docker-compose.
- internetsystemsconsortium/bind9:9.18
# Utiliza los volumenes tal como lo explica en el setup de la imagen

## Antes creamos la network:
- $ docker network create
- $ docker network create \
  --driver=bridge \
  --subnet=172.28.0.0/16 \
  --ip-range=172.28.5.0/24 \
  --gateway=172.28.5.254 \
  mired
- $ docker run -itd --network=mired ubuntu
# Ahora si:
services:
  bind9:
    image: internetsystemsconsortium/bind9:9.18
    container_name: asir_bind9
    networks:
      - mynetwork

  app-container-1:
    image: your-app-image-1 # Reemplaza 'your-app-image-1' con la imagen de tu primera aplicación
    container_name: app-container-1
    networks:
      - mynetwork
    # Configura los parámetros de tu primera aplicación

  app-container-2:
    image: your-app-image-2 # Reemplaza 'your-app-image-2' con la imagen de tu segunda aplicación
    container_name: app-container-2
    networks:
      - mynetwork
    # Configura los parámetros de tu segunda aplicación

networks:
  mynetwork:
# Añade un Readme.md con la descripción de las opciones del docker-compose.yml
image: la imagen a descargar.
container_name: nombre que le queremos dar al contenedor.
ports: El puerto que utilizará.
volumen: donde estará situado el contenedor.
environment: Zona donde se va ha hacer