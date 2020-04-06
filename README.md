# openhackctf-Abr-2020-writeup

Cómo fui el único que logró resolver dos de los desafíos del openhackCTF de abril 2020, he querido compartir la información de modo que puedan entender la resolución de ellos.

Vamos al grano.

Steg3
"Desde Rusia enviaron un mensaje oculto en una imagen. Usted la capturó y nota algo extraño en la imagen y piensa que pueden ser pistas. Debe obtener el mensaje oculto y validar la flag. Descargue la imagen para obtener lo que trae oculto."
Capitan.jpg

Efectívamente eran pistas. la imagen primero la puse bajo el buscador para reconocer quien era (me parecía haberlo visto en la caja de un cereal)
este se llamaba Cap'n Crunch, que según wikipedia hace alución al Capitan Crunch. (allí el nombre del archivo. vamos bien)
https://en.wikipedia.org/wiki/Cap%27n_Crunch

el nombre también alude a un software generador de diccionarios: crunch.. y dado que la imagen tenía  los caracteres "5 5 marte13" ya parecía el formato de argumentos de crunch.. así que no quedó otra que generar un diccionario

crunch 5 5 marte13 >dict

y utilizar alguna de las tantas herramientas que hay para bruteforcear steghide.

si no tienes ninguna, también se puede hacer por bash

for i in $(cat dict);do echo $i:; steghide extract -sf capitan.jpg -p $i | grep -v not ;done

al terminar la revisión ya tendrán su flag.


DICOM

Para este caso, seguramente era necesario tener conocimientos previos y eficientes sobre la vulnerabilidad de seguridad que tienen los sistemas DICOM (Digital Imaging and Communications in Medicine)
yo lo aprendí gracias a la investigación personal que hice tras leer este post del gran Tito S4vitar

https://s4vitar.github.io/hospital-dicom-exposure/

es por ello que simplemente tomé la IP y el nombre del paciente, lo agregué a mi visualizador y obtube el ID necesario para terminar el desafío.

2003311325191469

Espero que les haya sido de utilidad.
