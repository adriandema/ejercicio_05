# ejercicio_05


## HEALTHCHECK
Es una instrucción en Dockerfile que permite configurar un monitoreo para determinar si el contenedor está ejecutando normalmente. Se define un comando y otros parámetros como frecuencia o los reintentos. Tipicamente para servicios web se suele configurar en el comando un curl o wget a un servicio interno que determine el estado

por ejemplo

```
HEALTHCHECK --interval=5m --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
```

Luego en ejecución, el comando ```docker ps``` puede basarse en esa información para completar la información en la columna status 

```
CONTAINER ID   IMAGE                             COMMAND                  CREATED        STATUS        
df9b2dd9e105   adriandema/ejemplo:latest             "/usr/local..."   24 hours ago   Up 24 hours (healthy)                                                                       
```

## ONBUILD
Es una instrucción con la que se pueden calificar otras instrucciones en Dockerfile, que afecta las construcciones de imágenes basadas en ella. Podemos agregarle ONBUILD a un ADD o un RUN y el efecto es que en la construcción de una imagen hija, se van a ejecutar esos commandos como si estuvieran inmediatametne luego del FROM.


Se puede usar para generalizar ciertos pasos inciales en una imagen madre. Normalmente se identifican con etiquetas especiales para que lo tenga en cuenta quien las utilice como imagen base.



## VOLUME
Declara un volumen "anónimo" montado en el path indicado dentro del contenedor. En la máquina host será mapeado a una carpeta específica y puede persistir más allá de la vida del contenedor o reutilizarse desde otros contenedores. No es tan claro como los volúmenes mapeados con con ```docker run``` o ```docker-compose```
