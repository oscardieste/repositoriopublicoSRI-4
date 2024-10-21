# repositoriopublicoSRI-4 Óscar Dieste Maroñas 2ºASIR

## Docker Network 

### Crear unha rede en docker
Para crear a rede empreguei o comando ``docker network create --driver=bridge --subnet=172.29.0.0/16 --ip-range=172.29.5.0/24 --gateway=172.29.5.254 oscarred``.
Puxenlle de nome oscarred

### Crear dous contenedores unidos a esa rede
Uso o comando ``docker run -itd --name=oscar1 --network=oscarred ubuntu `` e despois para o segundo contenedor uso `` docker run -itd --name=oscar2 --network=oscarred ubuntu`` , aqui poñemoslle o nombre de cada contenedor pegada a cada subrede.
### Comprobar que os contenedores están na rede
Para ver os contenedores da rede, usamos  o comando ``docker network inspect oscarred``.
### Comprobar que os contenedores poden verse entre eles
Usamos o comando ``apt install -y iputils-ping``. Despois si vemos que estamos no meu primeiro contenedor despois facemos ping co contenedor 2 ej: ``ping oscar2``.
### Listar os contenedores conectados á rede
Para listar os contenedores, usamos o comando ``docker network ls``.
### Listar as propiedades da rede
Para ver as propiedades da rede solo temos que utilizar o comando `docker network inpect oscarred`.
### Crea outra rede
Para crear unha red faremos o mismo e usaremos o mesmo comando pero sustituindo os nome e as direccións IP.
``docker network create --driver=bridge --subnet=172.33.0.0/16 --ip-range=172.30.5.0/24 --gateway=172.30.5.254 oscarredd``
### Lanza dous contenedores novos conectados a esa nova rede
Usei: 
``docker run -itd --name=dieste1 --network=oscarredd ubuntu``.
``docker run -itd --name=dieste2 --network=oscarredd ubuntu``.
### Comproba as posibles conexións entre os 4 contenedores
O que  fixen foi: ping no contenedor dieste1, e  fixen ping a dieste1 da outra rede co comando ping oscar1, dame erro por ser distinta red.Mentres que facendo ping oscar2 non da erro ao ser da mesma rede.
## Docker compose

### Segue os pasos da guía de iniciación de docker-compose, e explica coas túas palabras os pasos que segues e qué fan
Seguindo os pasos da web, primeiro creamos o arquivo de configuración, onde incluímos todos os ficheiros necesarios. Logo, ao executar o comando ``docker compose up`` e abrir o navegador para acceder ao noso localhost, podemos ver na páxina e na terminal cantas veces accedemos.

### Agora que sabes algo máis de docker-compose, crea un arquivo (ou varios arquivos) de configuración que ó ser lanzados cun docker-compose up, resulten nunha rede docker á que estean conectados 3 contenedores, explica os parámetros do .yaml usado
Os parámetros son:

Versión: Versión de docker compose.

Volumes : Montar un directorio do contenedor.

Image: httpd.

Container_name: nome do contenedor.

Networks: redes  que están conectadas.

Portos: mapeo.

ports: mapeo o porto
### Busca e proba 4 parámetros e configuracións diferentes que podes incluir no arquivo compose, explica qué fan. (por exemplo diferentes cousas que facer coa opción RUN)
 depends_on: Asegura que os servizos se inicien nun orde específico.

 environment: Define variables de entorno para a configuración do contedor.

 restart: Configura como e cando debe reiniciarse un contedor.

 labels: Permite engadir metadatos aos contedores para unha mellor organización.
