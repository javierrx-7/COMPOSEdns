# ComposeDNS
# Configura un contenedor con la imagen oficial de bind9 utilizando docker-compose.
- internetsystemsconsortium/bind9:9.18
# Utiliza los volumenes tal como lo explica en el setup de la imagen

## Antes creamos la network:
- $ docker network create \
  --driver=bridge \
  --subnet=172.28.0.0/16 \
  --ip-range=172.28.5.0/24 \
  --gateway=172.28.5.254 \
  mired
- $ docker run -itd --network=mired ubuntu
# Ahora si:
services:
  asir_bind9:
    container_name: asir_bind9
    image: internetsystemsconsortium/bind9:9.16
    ports:
      - 53:53/tcp
      - 53:53/udp
    networks:
      mired:
        ipv4_address: 172.28.5.254
    volumes:
      - ./conf:/etc/bind
      - ./zonas:/var/lib/bind
  asir_cliente:
    container_name: asir_cliente
    image: alpine
    networks:
      - mired
    stdin_open: true  # docker run -i
    tty: true         # docker run -t
    dns:
      - 172.28.5.254  # el contenedor dns server
networks:
  mired: 
    external: true
# Añade un Readme.md con la descripción de las opciones del docker-compose.yml
image: la imagen a descargar.
container_name: nombre que le queremos dar al contenedor.
ports: El puerto que utilizará.
volumen: donde estará situado el contenedor.
environment: Zona donde se va ha hacer# ComposeDNS
