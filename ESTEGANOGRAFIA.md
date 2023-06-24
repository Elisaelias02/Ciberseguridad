¿Qué es la Esteganografía?

La esteganografía no es mas que una practica que consiste en esconder dentro de otro mensaje u objeto, de forma que a simple vista no se sepa la existencia del mensaje oculto.
Podemos ocultar casi cualquier tipo de contenido digital, texto, imágenes, videos o audios. 

Este contenido además puede ser cifrado antes de ocultarlo dentro de otro formato de archivo. 

Esto es algo que se ha practicado durante miles de años para mantener la privacidad de las conversaciones. 
*Dato curioso: En la antigua Grecia, las personas grababan mensajes en madera y luego los ocultaban con cera.*

--------------------------------------------------------------------
¿Por que es importante en ciberseguridad?
-------------------------------------------------------------------------------------------------------------
Los grupos de ransomware y algunas otras amenazas suelen ocultar información cuando se trata de atacar a algún objetivo. 
*Ejemplo: Se pueden ocultar datos, malware o enviar instrucciones a servidores de comando y control; podrían colocar toda esta información en archivos como imágenes, video, sonido o texto que a simpe vista parezca inofensivo. *


--------------------------------------------------------------------
¿Como funciona?
-------------------------------------------------------------------------------------------------------------
Una de las técnicas mas comunes es la esteganografía de "bits menos significativos"  (LSB) Consiste en incrustar la información secreta en los bits menos significativos de un archivo multimedia.

*Por ejemplo:
- En un archivo de imagen, cada pixel esta formado por 3 bytes de datos correspondientes a los colores, rojo, verde y azul; algunos formatos de imagen asignan un cuarto byte adicional a la transparencia o "alfa".
- La esteganografía de LSB modifica el ultimo bit de cada uno de estos bytes para ocultar un bit de datos. Así que para ocultar un megabyte de datos usando este método se necesitaría un archivo de imagen de 8 megabytes.
- Modificar el ultimo bit del valor del pixel no produce un cambio visible en la imagen, lo que significa que cualquier persona que vea la imagen original y la modifica con esteganografía no podrá diferenciarlas.

De la misma manera se aplica a otro tipo de archivos como audio y video, los datos deberán ocultarse en partes del archivo que producen el menor cambio en la salida audible o visual.

Existen otros métodos para ocultar mensajes, como la sustitución de palabras o letras.
Consiste en que el emisor de un mensaje secreto oculta el texto distribuyéndolo dentro de otro que sea mucho mas grande y colocando palabras en intervalos específicos.

También podemos ocultar una partición entera de un disco duro o incrustar datos en la sección de encabezado de archivos y paquetes de red.

Existe también la esteganografía de red o de protocolo, en esta técnica se incrusta información en los protocolos de control de red que usan en la transmisión de datos, como TCP, UDP, ICMP, etc.

--------------------------------------------------------------------
¿Podemos compararlo con la criptografía?
-------------------------------------------------------------------------------------------------------------
Aunque muchas veces suelen compararse, estas practicas no son lo mismo, ya que la esteganografía no consiste en codificar datos al enviarlos ni en usar una clave para decodificarlos al recibirlos.
La criptografía cambia la información a texto cifrado que solo puede entenderse con una clave de descifrado. De esta forma si alguien intercepta el mensaje cifrado podría entender con facilidad que se aplico alguna forma de cifrado.
