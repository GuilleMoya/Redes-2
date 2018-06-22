SecureBox Client
================

CreativeCommons **(CC)** 2018, Andres Salas Peña (&&res) y Francisco Vicente Lana (p4Ko), Versión 2

SecureBox Client es un servicio de almacenamiento seguro de ficheros accesible por una API REST, creado para la realización de la segunda práctica de la asignatura de Redes 2. 
Es seguro porque incluye el cifrado asimétrico *RSA* y *firma digital*.

Ejecución SecureBox Client
--------------------------
Aunque se incluye en el sexto subapartado de la wiki, aquí se deja una guía para ejecutar el servicio:
* Es importante mencionar que la práctica se ha realizado entera con **Python 2**.
* Utilizar python securebox_client.py -h para que aparezca el cuadro de mando que recoge todas las flags y los argumentos de entrada permitidos para cada una de las funciones.
* Para ir probando cada una de las funciones, se debe ir ejecutando python securebox_client.py con sus flags y argumentos de entrada adecuados.
* Esta es la salida de la terminal cuando se ejecuta securebox_client.py -h:
`
usage: securebox_client.py [-h] [--create_id nombre email]
                           [--search_id cadena] [--delete_id id]
                           [--upload fichero] [--source_id id_fichero]
                           [--dest_id id_fichero] [--list_files]
                           [--download id_fichero] [--delete_file id_fichero]
                           [--encrypt fichero] [--sign fichero]
                           [--enc_sign fichero]
`
Cliente que consume el servicio ofrecido por securebox
`
optional arguments:
  -h, --help            show this help message and exit
  --create_id nombre email
                        Creacion identidad
  --search_id cadena    Busqueda usuario
  --delete_id id        Eliminacion identidad
  --upload fichero      Envio fichero
  --source_id id_fichero
                        ID emisor fichero
  --dest_id id_fichero  ID receptor fichero
  --list_files          Lista ficheros
  --download id_fichero
                        Recupera fichero
  --delete_file id_fichero
                        Elimina fichero
  --encrypt fichero     Cifra fichero
  --sign fichero        Firma fichero
  --enc_sign fichero    Cifra y firma fichero
`

Mencionar que las flags de *--dest_id* y *--source_id* no tiene sentido usarlas solas. Son flags que deben ir acompañando a otras flags:
* La flag de *--encrypt* debe ir acompañada de la flag *--dest_id*
* La flag de *--enc_sign* también debe ir acompañada de la flag *--dest_id*
* La flag de *--upload* también debe ir acompañada de la flag *--dest_id*
* La flag de *--download* (que hace internamente un descifrado) debe incluir la flag *--source_id*
