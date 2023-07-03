# Intelligent_APT_Generator
TFM_ RUBEN_GONZALEZ_GOMEZ

## Instalación

### Paso 1: Instalar MITRE Caldera
1. Accede a su [repositorio](https://github.com/mitre/caldera) e instale Caldera.

### Paso 2: Clonar el repositorio
1. Abre una terminal o línea de comandos en tu sistema.
2. Navega hasta la ubicación donde deseas clonar el repositorio de Intelligent_APT_Generator.
3. Ejecuta el siguiente comando para clonar el repositorio:

```shell
git clone https://github.com/ejemplo/programa.git 
```

### Paso 3: Instalar los módulos de Python

1. Instala Tensorflow, Numpy y Matplotlib.
 ```shell
pip install tensorflow numpy matplotlib
```

## Ejecución

### Paso 1: Desplegar servidor Caldera
1. Abre una terminal y navega hasta la ubicación donde esté el repositorio de Caldera clonado.
2. Ejecuta el siguiente comando:
```shell
python3 server.py --insecure 
```
3. Una vez iniciado, inicia sesión en http://localhost:8888 utilizando las credenciales predeterminadas red:admin.

### Paso 2: Desplegar agente Caldera
1. En la interfaz de Caldera, accede al panel de *agents* y selecciona la opción *Sandcat*
2. Comprueba que el valor de *app.contact.http* se corresponde con la dirección IP y el puerto donde está desplegado el servidor de MITRE Caldera.
3. Copia el comando que Caldera genera y ejecútalo en la máquina víctima.

### Paso 3: Ejecutar Intelligent APT Generator
1. Abre una nueva terminal y navega hasta la ubicación donde esté el repositorio con la aplicación Intelligent_APT_Generator clonada.
2. Navega hasta la carpeta *app*.
```shell
cd app 
```

3. Antes de ejecutarla, es necesario saber que la aplicación requiere los siguientes parámetros:

| Parámetro | Descripción                  |
| --------- | ---------------------------- |
| `-c`, `--cookie`      | Valor de la cookie API_SESSION (Obligatorio)|
| `-p`, `--platform`      | Plataforma sobre la que se va a desarrollar la APT. 1: Linux; 2: Windows; 3: Darwin (Obligatorio) |
| `-ne`, `--num_epochs`      | Número de epochs durante las que se desea entrenar al modelo. Recomendable que el valor esté entre 1000 y 3000, dependiendo de la complejidad del problema (Default: 1000)|
| `-e`, `--evaluate`      | Cada cuántas epochs se debe evaluar el modelo (Default: 50) |
| `-t`, `--target`      | Perfil del atacante. 1: Crypto mining; 2: Disrupt Wi-Fi; 3: Encrypter (Obligatorio) |

Asegúrate de proporcionar los valores adecuados para cada parámetro al ejecutar la aplicación. Puedes usar la siguiente sintaxis para pasar los parámetros:

Solo parámteros obligatorios:
```shell
python main.py -c <valor_cookie> -p <plataforma> -t <target>
```

Todos los parámetros:
```shell
python main.py -c <valor_cookie> -p <plataforma> -ne <num_epochs> -e <evaluate> -t <target>
```

## Resultados

Una vez que se haya terminado de ejecutar, podrás ver las gráficas que muestran la evolución del aprendizaje de la red neuronal.

Después de cerrar estas gráficas, podrás consultar el perfil de adversario creado en la interfaz de Caldera, en el apartado *adversaries*. Todos los nombres de los adversarios creados por la apliación empezarán con la palabra *Intelligent*.

Además, podrás consultar el estado de la ejecución de esta APT en la máquina víctima en la interfaz de Caldera, en la sección *operations*.

### Ayuda

Para cualquier incidente con MITRE Caldera consulte su [documentación](https://caldera.readthedocs.io/en/latest/).

Para cualquier consulta acerca del proyecto, contactar con rubengg2000@gmail.com.