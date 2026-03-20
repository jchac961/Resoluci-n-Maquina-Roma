# Resoluci-n-Maquina-Roma

**Reconocimiento**

Hacemos un escaneo de puertos a la maquina vulnerable, en busca de puertos abiertos corriendo servicios con versiones desactualizadas

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-04 215901" src="https://github.com/user-attachments/assets/7a4a72e3-0dd7-4e71-b260-9cb4f51afb09" />

Encontramos dentro del escaneo con nmap listando los script por defecto, encontramos que hay 3 usuarios que pueden tener acceso a la maquina

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-04 224444" src="https://github.com/user-attachments/assets/95774153-da85-466b-a29f-b4edc59476ed" />

Dentro de los puertos que encontramos abiertos pudimos ver el puerto 21 el cual se encuentra filtrado, procedimos a verificar con el numero ip de la maquina para verificar que encontramos en el servicio http que se encuentra en el mismo

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-04 220403" src="https://github.com/user-attachments/assets/a82ea72d-9182-4b0d-9bb9-81cf5980200b" />

Dentro de este sitio web obtuvimos información de que se esta utilizando un servicio llamado fail2ban el cual trabaja como un guardia de seguridad que se encarga de monitorear la actividad que se esta realizando en la maquina, el mismo tenia algunas restricciones, las cuales solo permitian hacer dos intentos en 60 segundos antes de ser baneado por 10 minutos

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-10 152550" src="https://github.com/user-attachments/assets/ab9a320c-9fc3-48cd-8ab3-9712472c4830" />

Procedimos a realizar un port knocking para liberar el puerto 21 y poder entonces realizar los ataques de fuerza bruta

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-04 225230" src="https://github.com/user-attachments/assets/9e511474-268b-47bd-9ce1-e0f612e68a00" />

Luego procedimos a utilizar la herramienta hydra para hacer fuerza bruta y tratar de encontrar la contraseña de alguno de los usuarios

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-10 150042" src="https://github.com/user-attachments/assets/19af1cae-683f-49a8-ba5e-4a56660c6028" />

Pero se nos paso y el fail2 ban nos baneo

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-04 225319" src="https://github.com/user-attachments/assets/23bce2a8-ecd2-42fc-8e1b-88df01ba1628" />

Procedimos a hacer pruebas utilizando algunas banderas distintas y que la maquina enviara el ataque mediante un tiempo determinado de 1 intento cada 90 segundos, para que no hubiera inconvenientes con el fail2ban y tuvimos exitos

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-10 152210" src="https://github.com/user-attachments/assets/4f4e489d-6382-4a9f-8abb-67a923eaf9dc" />
A continuación subo algunas imagenes de el proceso que hicimos, con cada uno de los usuarios

  # Roma1
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-10 162916" src="https://github.com/user-attachments/assets/7bee347c-befb-46fd-bb16-e234267d79c2" />
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-10 163626" src="https://github.com/user-attachments/assets/ec4533bf-d19b-41d2-9d68-107a8ef4947e" />

Hicimos 126 intentos con el usuario roma1 sin tener ningun resultado positivo

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-10 215810" src="https://github.com/user-attachments/assets/e5a03a52-7831-439d-af97-fcdbe4dbacaf" />

  # Roma2
Con este usuario tambien hicimos algunos intentos

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-10 220517" src="https://github.com/user-attachments/assets/6a12a7a4-4bc3-48d7-aa78-ff8e2f4f4e68" />
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-10 220527" src="https://github.com/user-attachments/assets/5bf1465f-063c-40e3-831f-54868115134c" />
Hicimos aproximadamente 89 intentos sin obetener tampoco resultados positivos

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-14 225159" src="https://github.com/user-attachments/assets/c1f46888-ebd7-4696-9a12-6916d619a974" />
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-14 225150" src="https://github.com/user-attachments/assets/60906585-acc8-4795-83ee-c78fa276a1ce" />

  # Roma3
En este usuario tambien hicimos algunos intentos, los cuales en los primeros realizados encontramos la contraseña

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-14 225539" src="https://github.com/user-attachments/assets/3545ec2d-901f-4bab-95e2-1de9e6112bf7" />
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-14 225552" src="https://github.com/user-attachments/assets/f43ca5cc-ec62-4709-925d-0fdd9f61949e" />
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-14 232231" src="https://github.com/user-attachments/assets/b9c0059e-d357-415b-a857-19dbacbd9be4" />

# Explotación

Luego procedimos a ingesar por medio de ssh y obtuvimos acceso

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-14 232325" src="https://github.com/user-attachments/assets/74761ddd-0105-40de-bcd0-a185946644dd" />

Ya dentro de la maquina listamos archivos en busca de algo importante, y dentro de la maquina Downloads encontramos uno llamado .ssh_part2, verificamos su contenido y procedimos a copiarlo en un archivo de texto llamado hash, 

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-14 232431" src="https://github.com/user-attachments/assets/0f094137-c46a-48af-8272-911a9888d361" />

Seguimos buscando!!
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-14 232528" src="https://github.com/user-attachments/assets/c0334098-d99b-44ea-abc3-d3a8c6ed4a37" />

Y  encontramos en una carpeta llamada Desktop un archivo llamado .ssh_part1 asi que tambien lo utilizamos para el archivo de texto antes mencionado, llamado hash

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 160942" src="https://github.com/user-attachments/assets/f24ecc16-3566-40aa-b2e8-4ada94bd8a16" />

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 161028" src="https://github.com/user-attachments/assets/2597c11d-2014-47a8-bcf9-b7d8e0b0593f" />

Cambiamos el nombre al archivo y lo llamamos id_rsa, y lugo intentamos ingresar mediante ssh pero no obtuvimos acceso, ya que se nos habia pasado otorgar los permisos al archivo

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 162240" src="https://github.com/user-attachments/assets/06884b6d-4376-4d88-8e77-fca2bf39e7f6" />

Procedimos a otorgar los permisos

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 162258" src="https://github.com/user-attachments/assets/8762b995-c681-4be8-ab6d-4136159688b1" />

Y obtuvimos acceso a la maquina 

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 162309" src="https://github.com/user-attachments/assets/8b361aea-c5dd-4248-9755-81444604ca1d" />

De igual manera encontramos archivos llamados .ssh_part1

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 162751" src="https://github.com/user-attachments/assets/fbf7b14f-af7c-424b-82c0-982098c7e474" />

Tambien encontramos el archivo .ssh_part2 y lo descargamos, y procedimos a hacer un archivo llamado hash2 y luego lo convertimos en el archivo id_rsa2

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 163008" src="https://github.com/user-attachments/assets/31d90364-ce06-416b-a1f7-e581f7b339ba" />

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 163229" src="https://github.com/user-attachments/assets/883d48c2-8013-4e16-8a69-0434b1f3fe1e" />

Luego le dimos los permisos

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 163253" src="https://github.com/user-attachments/assets/c61a0da4-1ffa-4478-abda-73e7efeeabb5" />

Ingresamos a la maquina utilizando el usuario roma2 el cual era el unico que podia escalar privilegios como root

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 163327" src="https://github.com/user-attachments/assets/4529bba1-f4ae-406b-b020-557598f48c84" />

Listamos los binarios suid para verificar si encontrabamos alguno mal configurado y en efecto encontramos uno llamado doas

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 163517" src="https://github.com/user-attachments/assets/e679800d-03cf-4ccc-85bf-f690290fc3b2" />

# Resultados

Luego de buscar un poco de información encontramos la manera de ejecutarlo y obtuvimos acceso root

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 163828" src="https://github.com/user-attachments/assets/55ac3cb7-b890-413f-af31-4514e73db613" />

Encontramos un archivo flag.txt

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 163929" src="https://github.com/user-attachments/assets/e7657bcb-2292-4507-bdf2-5564dcd6c6ec" />

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 163942" src="https://github.com/user-attachments/assets/c8a219d7-aaa9-4d6a-8ffb-6d15aeb9f1da" />

Y de esta manera concluimos con la maquina

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-15 164156" src="https://github.com/user-attachments/assets/dde311e1-9352-47df-bd16-05500076355d" />

