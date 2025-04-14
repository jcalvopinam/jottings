## Reemplazar Docker Desktop por OrbStack

En este documento se explica como reemplazar Docker Desktop por Orbstack sin perder la imagen (y nuestra base de datos).

_**Requisitos:**_

- Tener corriendo el docker desktop con nuestra imagen, tal como lo hacemos siempre.
- Tener instalado brew (si seguiste el instructivo de armado de ambiente es muy probable que ya lo tengas).

![[docker-desktop.jpg|600]]

### Backup (no necesario)

Por las dudas, podemos hacer un backup de nuestra imagen. El directorio en el cual generalmente se encuentra la imagen de docker desktop, donde tenemos nuestra base de datos, es:
```shell
~/Library/Containers/com.docker.docker/Data/vms/0/data/Docker.raw
```

(por ese motivo siempre que borramos la aplicación de Docker Desktop no perdemos la imagen, ya que se encuentra en una carpeta distinta).

> Recomendación: guardar la carpeta com.docker.docker que se encuentra dentro de la carpeta llamada Containers.

---

## Instalación de Orbstack

- Instalamos orbstack
```shell
brew install orbstack
```

- Posible error al ejecutar el comando:
![[orbstack.jpg|600]]

- Seguramente tengamos Docker dentro de la carpeta Applications. Para asegurarnos, ejecutemos:
```shell
ls /Applications/Docker.app
```

- Si vemos una carpeta Contents, entonces la tenemos ahí.
![[****migrate-docker-desktop.jpg|600****]]

- Si no encontramos nada, es posible que tengamos la app en otro directorio (tenemos que encontrarlo). Si tenemos la aplicación en esa ruta, ahora ejecutamos:
```shell
sudo mkdir -p /Applications/Docker.app/Contents/Resources/cli-plugins
```

- Luego, ejecutamos:
```shell
brew cleanup
```

- Deberíamos tener la aplicación de OrbStack instalada. En caso contrario ejecutamos de nuevo el comando:
```shell
brew install orbstack
```

## OrbStack

- Abrimos OrbStack
![[orbstack.jpg|600]]

- Elegimos Docker
![[migrate-docker-desktop.jpg|600]]

- Click en Migrate: 
Suceden dos cosas:

1. Se migra la imagen al directorio de OrbStack
2. Se cierra el Docker Desktop porque a partir de ahora vamos a usar esta aplicación de reemplazo.

![[migrating-image.jpg|400]]

![[stopping-docker.jpg|400]]
Listo, se trasladó la imagen de docker a Orbstack.

Levantamos el contenedor:

![[start-container.jpg|600]]

Si abrimos una nueva terminal y ejecutamos el comando:
```java
docker ps
```

Ya deberíamos ver nuestra imagen corriendo, sin tener Docker desktop y solo con OrbStack.