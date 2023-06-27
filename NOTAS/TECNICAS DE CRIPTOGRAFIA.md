-------------------------------------------------------------------------------
¿QUE TECNICAS SE UTILIZAN ACTUALMENTE?
-------------------------------------------------------------------------------------------------------------
Actualmente se utilizan 4 tipos de criptografía para proteger tus datos, todos con sus ventajas y sus desventajas.

-------------------------------------------------------------------------------
HASHING
-------------------------------------------------------------------------------------------------------------
Las funciones de hash son utilizadas como base fundamental en muchos otros componentes criptográficos, tales como firmas digitales, cifrados de llave publica, contraseñas, entre otros.

*¿Cómo funciona?
Una función de hash recibe un mensaje de longitud arbitraria, y devuelve un valor de tamaño fijo (generalmente entre 256 y 512 bits). 
Las funciones de hash en otros usos criptográficos cumplen las siguientes características:

- Un cambio chico en el mensaje provoca un cambio muy grande en el valor devuelto por la función de hash.
- Dado un valor devuelto por la función de hash a partir de un mensaje M, es demasiado difícil encontrar un valor que produzca ese valor sin conocer M.
- Colisiones (dos mensajes distintos entre si M1 y M2 tales que H(M1) == H(M2)), encontrar dos mensajes que colisionen es muy complicado.

EJEMPLOS DE FUNCIONES HASH
-------------------------------------------------------------------------------------------------------------
MD5
Es un algoritmo de hashing basado en una construcción Merkle-Damgard que produce un valor de 128 bits, usando bloques de 512 bits en sus procedimientos internos. 
*Dato: En 2004 se mostro que MD5 no es resistente a colisiones, lo que hizo que ya no se considerara un hash seguro.

SHA-1
Al igual que MD5 esta basada en una construcción Merkle-Damgard, esta función produce un valor de salida de 160 bits, pero al igual que MD5 ya no se considera seguro por presentar problemas frente a taques de colisiones. 

SHA-2
Usa la misma primitiva que MD5 y SHA-1 (Merkle-Damgard) sin embargo posee 6 variaciones distintas de largo de salida: SHA-224, SHA-256, SHA-512, SHA-512/224 y SHA-512-256.

SHA-3
Utiliza una construcción de esponja que comprende de una familia de 5 funciones hash con diferentes tamaños SHA3-224, SHA3-256, SHA3-38, SHA3-512 y SHAKE128.

FUNCIONES DE DERIVACION DE LLAVES (KDF)
Es una categoría de funciones de hash que deriva de una o mas llaves secretas a partir de una llave principal, usando una función pseudoaleatoria. Estas funciones suelen tener la característica de que sus valores de salida son lentos de verificar (del orden de segundos) esto debido a que la cantidad de veces que se ejecutan es configurable, lo que mitiga el riesgo de un ataque de fuerza bruta para detectar la preimagen de un valor dado.

-------------------------------------------------------------------------------
CRIPTOGRAFIA SIMETRICA
-------------------------------------------------------------------------------------------------------------
Vamos a hablar de 3 tipos de criptografía simétrica: One-time pad, cifradores de bloque y cifradores de flujo.

-------------------------------------------------------------------------------
ONE-TIME PAD
-------------------------------------------------------------------------------------------------------------
Es una técnica de cifrado que no puede ser rota si la llave no se reúsa, en la que un mensaje se cifra ejecutando la operación **xor** entre un valor aleatorio al menos del tamaño del mensaje y el mismo mensaje* 

El funcionamiento de un cifrador de One-Time Pad se puede describir de la siguiente manera:

1.- GENERACION DE CLAVE: La clave se genera de manera aleatoria y debe tener la misma longitud que el mensaje original. La clave puede estar compuesta por una secuencia de bits o caracteres aleatorios.
    
2.- OPERACION DE XOR: Se realiza una operación de XOR entre cada bit (o byte) del mensaje original y el bit (o byte) correspondiente en la clave. El resultado de esta operación se convierte en el texto cifrado.
    
3.- DESCIFRADO: Para descifrar el mensaje cifrado, se realiza nuevamente una operación de XOR entre el texto cifrado y la clave utilizada en el paso anterior. Esta operación recupera el mensaje original.

-------------------------------------------------------------------------------
CIFRADORES DE BLOQUE (Block Cipher)
-------------------------------------------------------------------------------------------------------------
Este método de cifrado divide el texto sin formato en bloques de tamaño fijo. Cada bloque contiene el mismo numero de bits. El cifrado de bloques opera solo en un bloque de texto sin formato y aplica la clave para producir el bloque correspondiente de texto cifrado.

El proceso de un cifrador de bloque consta de varias etapas:

1.- DIVISON DE BLOQUES: El mensaje original se divide en bloques de un tamaño especifico, generalmente de 64 o 128 bits. Si el mensaje no es múltiplo del del bloque, se puede aplicar un relleno (padding) para alcanzar el tamaño necesario.
2.- CLAVE DE CIFRADO: Se utiliza una clave secreta o compartida entre el emisor y el receptor para realizar las operaciones de cifrado y descifrado. La elección de una clave segura esencial para garantizar la seguridad del cifrado.
3.- ITERACIONES DE CIFRADO: El bloque de entrada se somete a múltiples iteraciones o rondas de operaciones criptográficas. Cada ronda consiste en una combinación de transformaciones como sustituciones no lineales, permutaciones y operaciones algebraicas.
4.- FUINCIONES CRIPTOGRAFICAS: Durante cada ronda, se aplican funciones criptográficas como substituciones (S-boxes), permutaciones (P- boxes) y operaciones algebraicas (XOR, adiciones modular, entre otras) para mezclar y transformar los datos.
5.- RONDA FINAL: Después de un numero determinado de iteraciones, se realiza una ronda final que puede incluir una función adicional llamada función de mezcla (mixing function) para aumentar la aleatoriedad y la seguridad del cifrado.
6.- BLOQUE DE CIFRADO: Una vez completadas todas las rondas, se obtiene el bloque cifrado, que es el resultado final del proceso del cifrado. Este bloque se transmite o almacena de manera segura para su posterior descifrado.



-------------------------------------------------------------------------------
CIFRADORES DE FLUJO
-------------------------------------------------------------------------------------------------------------
Los cifradores de flujo funcionan generando una secuencia de bits pseudoaleatorios llamados flujo clave (keystream) que se combinan con el mensaje original mediante una operación de XOR (o exclusivo) para producir el texto cifrado. A diferencia de los cifradores de bloque, los cifradores de flujo encriptan los datos en tiempo real, bit a bit o byte a byte, en lugar de dividirlos en bloques fijos.

El funcionamiento de los cifradores de flujo es el siguiente:

1.- GENERACION DE FLUJO CLAVE: El cifrador genera un flujo clave mediante el uso de una secuencia de bits pseudoaleatorios (PRNG, por sus citas en ingles) alimentada con una clave secreta o compartida. El PRNG toma como entrada la clave y un valor de inicialización llamado vector de inicialización (IV, por sus siglas en ingles) para producir un flujo clave que parece ser aleatorio.
2.- OPERACION DE XOR: El flujo clave se combina bit a bit o byte a byte mediante una operación de XOR con el mensaje original. Cada bit (o byte) del mensaje se XORea con el bit (o byte) correspondiente en el flujo clave.
3.- DESCIFRADO: Para descifrar el mensaje cifrado, se utiliza el mismo flujo clave generado anteriormente. Se realiza la operación de XOR entre el flujo clave y el texto cifrado, lo que permite recuperar el mensaje original.

Es importante destacar que los cifradores de flujo son algoritmos simétricos, lo que significa que la misma clave se utiliza para el cifrado y el descifrado. Además, los cifradores de flujo tienen la propiedad de ser síncronos, ya que el flujo clave se genera en sincronización con el flujo de entrada, lo que permite el cifrado en tiempo real.


-------------------------------------------------------------------------------
CRIPTOGRAFIA ASIMETRICA
-------------------------------------------------------------------------------------------------------------
La criptografía asimétrica, también conocida como criptografía de clave publica, es un sistema criptográfico que utiliza un par de claves diferentes pero relacionadas matemáticamente para cifrar y descifrar información. Este par  de claves consisten en una clave publica y una clave privada.

Funciona de la siguiente manera:

1.- GENERACION DEL PAR DE CLAVES: El primer paso es generar el par de claves. Para ello se utiliza un algoritmo de generación de claves que produce una clave publica que se comparte con otras personas y la clave privada que se mantiene en secreto y solo posee el propietario.
2.- CIFRADO DE INFORMACION: Para cifrar información utilizando criptografía asimétrica, se utiliza la clave publica del destinatario. *Ejemplo: Elisa quiere enviar un mensaje cifrado a Victor. Elisa utiliza la clave publica de Victor para cifrar el mensaje. El mensaje solo puede ser descifrado correctamente utilizando la clave  privada correspondiente que solo Victor posee.*
3.- DESCIFRADO DE INFORMACION: Cuando Victor recibe el mensaje cifrado de Elisa, utiliza su clave privada para descifrarlo. El mensaje descifrado solo puede ser leído correctamente utilizando la clave privada correspondiente a la clave publica utilizada para el cifrado.

Un ejemplo común de criptografía asimétrica es el algoritmo RSA (Rivest-Shamir-Adleman), que utiliza operaciones matemáticas basadas en la factorización de números primos para generar las claves y realizar el cifrado y descifrado.


-------------------------------------------------------------------------------
ALGORITMOS DE INTERCAMBIO DE CLAVES
-------------------------------------------------------------------------------------------------------------
Los algoritmos de intercambio de claves permiten el intercambio seguro de claves de cifrado con una parte desconocida. Los usuarios no comparten información durante el intercambio de claves. El objetivo final es crear una clave de cifrado personalizada que puedan utilizar ambas partes en una fecha posterior.

Un ejemplo de esto y quizá el mas conocido es el algoritmo Diffie-Hellamn.
Diffie-Hellman establece un secreto compartido entre dos usuarios que luego se puede utilizar para intercambiar información secreta a través de una red pública.


![[Pasted image 20230626192637.png]]
-------------------------------------------------------------------------------
MAS ALLA DEL CIFRADO
-------------------------------------------------------------------------------------------------------------
Aunque el cifrado es un método muy seguro, algunas veces no será suficiente.
*Por ejemplo: Si un mensaje cifrado no contiene metainformación acerca de cuando fue mandado, un atacante podría reenviar mensajes de una persona a la otra, haciéndola pensar que dijo nuevamente algo que en realidad no se dijo. Este ataque se denomina ATAQUE DE REPETICION (o Replay Attack), y se puede evitar agregando información secuencial al mensaje.*

Otro problema que puede ocurrir es que el mensaje sea alterado por un atacante antes de llegar al receptor. En el caso del cifrado de flujo, donde la modificación de un byte del texto cifrado altera solamente un byte del texto plano, una modificación de este estilo podría cambiar el significado del mensaje cifrado en una letra o símbolo.
Para evitar este problema, es posible "autenticar" el mensaje a través de "Message Authentication Codes" (MACs), esto permite demostrar que el mensaje cifrado no ha sido intervenido de ninguna forma.

