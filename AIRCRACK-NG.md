Aircrack-ng es una suite de herramientas de seguridad informática que se enfoca en la detección y análisis de vulnerabilidades en redes inalámbricas. Utiliza ataques de diccionario y fuerza bruta para recuperar claves WEP y WPA/WPA2.

-----------------------------------------------------------------------------
AIRMON-NG
-------------------------------------------------------------------------------------------------------------

Airmon-ng es una herramienta dentro de la suite Aircrack-ng que permite habilitar y configurar interfaces de red inalámbrica en modo monitor. El modo monitor permite capturar y analizar paquetes de todas las redes WiFi cercanas, incluso aquellas a las que no estamos conectados.

El proceso para habilitar el modo monitor con airmon-ng es el siguiente:

1. Verificar las interfaces disponibles: Se ejecuta el comando "airmon-ng" para listar las interfaces inalámbricas presentes en el sistema.
    
2. Detener cualquier proceso que utilice la interfaz: Es posible que procesos como NetworkManager interfieran con airmon-ng, por lo que se deben detener mediante comandos como "service network-manager stop".
    
3. Habilitar el modo monitor: Se utiliza "airmon-ng start <interfaz>" para poner la interfaz en modo monitor. Por ejemplo, "airmon-ng start wlan0" habilitará el modo monitor en la interfaz "wlan0".
    
4. Verificar el cambio: Se puede usar nuevamente "airmon-ng" para asegurarse de que la interfaz ahora esté en modo monitor.
    

Una vez que la interfaz está en modo monitor, se puede usar con otras herramientas de Aircrack-ng, como Airodump-ng para capturar paquetes y analizar las redes inalámbricas cercanas, o Aireplay-ng para realizar ataques de inyección de paquetes y pruebas de seguridad.

Al finalizar, es importante deshabilitar el modo monitor utilizando "airmon-ng stop <interfaz>" para restaurar la interfaz a su estado original y reactivar los procesos que se detuvieron previamente.

	-------------------------------------------------------------------------------------------------------------
AIRBASE-NG
-------------------------------------------------------------------------------------------------------------
Airbase-ng es una herramienta de Aircrack-ng que permite crear un punto de acceso inalámbrico falso. Funciona emitiendo un SSID (nombre de red) falso y, cuando los dispositivos se conectan, captura paquetes enviados por ellos. Se utiliza con fines de pruebas de seguridad y análisis de vulnerabilidades en redes WiFi.

El funcionamiento de airbase-ng es el siguiente:

1. Verificar interfaces: Se ejecuta "airmon-ng" para listar las interfaces inalámbricas disponibles y asegurarse de que no haya conflictos.
    
2. Detener servicios: Se detienen servicios como NetworkManager que pueden interferir con airbase-ng.
    
3. Habilitar modo monitor: Se pone una interfaz en modo monitor con "airmon-ng start <interfaz>".
    
4. Configurar el punto de acceso: Se utiliza "airbase-ng -e <SSID> -c <canal> <interfaz>" para iniciar el punto de acceso falso. Se especifica el SSID y el canal a usar.
    
5. Asignar dirección IP: Se asigna una dirección IP a la interfaz virtual creada para el punto de acceso.
    
6. Activar enrutamiento: Se activa el enrutamiento IP para que los dispositivos conectados al punto de acceso puedan acceder a la red.
    
7. Iniciar DHCP: Se inicia un servidor DHCP para asignar direcciones IP a los dispositivos conectados.
    
8. Capturar paquetes: A medida que los dispositivos se conectan al punto de acceso falso, airbase-ng captura los paquetes enviados y recibidos.
    
9. Análisis y pruebas: Con los paquetes capturados, se pueden realizar análisis de seguridad y pruebas de vulnerabilidades en la red inalámbrica.
    

Es fundamental utilizar airbase-ng con responsabilidad y solo en redes que uno tenga permiso para analizar. El uso no autorizado puede ser ilegal y causar daño a la privacidad y seguridad de las redes y dispositivos afectados.

-------------------------------------------------------------------------------------------------------------
AIRDUMP-NG
-------------------------------------------------------------------------------------------------------------
Airodump-ng es una herramienta de Aircrack-ng que actúa como sniffer de redes inalámbricas. Captura y muestra información de redes cercanas, como SSID, dirección MAC, potencia de señal, canales y dispositivos conectados. Útil para análisis de seguridad y búsqueda de redes disponibles.

Funcionamiento:

1. Seleccionar interfaz: Se ejecuta "airmon-ng" para listar interfaces inalámbricas disponibles y "airmon-ng start <interfaz>" para poner una en modo monitor.
    
2. Iniciar airodump-ng: Se lanza "airodump-ng <interfaz en modo monitor>" para escanear redes. Muestra información en tiempo real.
    
3. Filtrar resultados: Opcionalmente, se pueden aplicar filtros para centrarse en una red específica o un canal.
    
4. Capturar datos: Airodump-ng graba paquetes capturados en archivos .cap y .csv para análisis posterior.
    
5. Reconocer redes: Las redes cercanas y sus detalles son mostrados en la interfaz de airodump-ng.
    
6. Capturar handshake: Si se busca romper una clave WPA/WPA2, se debe capturar el handshake de un cliente al conectarse a la red.
    
7. Finalizar: Se cierra airodump-ng con Ctrl+C y se procesa la información obtenida con otras herramientas como Aircrack-ng.

-------------------------------------------------------------------------------------------------------------
AIRPLAY-NG
-------------------------------------------------------------------------------------------------------------
Airplay-ng es una herramienta de Aircrack-ng que se utiliza para generar tráfico de red inalámbrica falso y llevar a cabo ataques de inyección de paquetes. Esto puede usarse para probar la seguridad de redes WiFi y, en combinación con Aircrack-ng, intentar romper claves WEP/WPA.

Funcionamiento:

1. Modo monitor: Se inicia una interfaz en modo monitor con "airmon-ng start <interfaz>".
    
2. Seleccionar objetivo: Se elige la red WiFi objetivo a atacar y se identifica el BSSID (dirección MAC del punto de acceso).
    
3. Falsificar dirección MAC: Se cambia la dirección MAC de la interfaz para hacerla parecerse a un cliente conectado legítimo.
    
4. Iniciar ataque: Se ejecuta "aireplay-ng -1 0 -a <BSSID> -h <MAC> -e <ESSID> <interfaz>" para autenticarse al punto de acceso.
    
5. Generar tráfico falso: Se utiliza "aireplay-ng -3 -b <BSSID> -h <MAC> <interfaz>" para generar tráfico falso y recopilar vectores de inicialización (IVs) para redes WEP.
    
6. Capturar handshake (WPA/WPA2): Si el objetivo es una red WPA/WPA2, se espera a que un cliente se conecte y se capture el handshake.
    
7. Ataque de fuerza bruta (WEP): Con suficientes IVs, Aircrack-ng se usa para intentar descifrar la clave WEP.
    
8. Ataque de diccionario (WPA/WPA2): Con el handshake capturado, Aircrack-ng se emplea para probar claves desde un diccionario hasta encontrar la correcta.
    
9. Finalizar: Una vez obtenida la clave (en caso de éxito), se detiene el ataque y se restaura la configuración de la interfaz.

-------------------------------------------------------------------------------------------------------------
AIRCRACK-NG
-------------------------------------------------------------------------------------------------------------
Aircrack-ng es una suite de herramientas de seguridad para redes inalámbricas. Permite analizar, capturar paquetes y realizar ataques de fuerza bruta o diccionario para recuperar claves WEP/WPA/WPA2, evaluando la seguridad de redes WiFi y mejorando su protección.

Funcionamiento:

1. Modo monitor: Se inicia una interfaz en modo monitor con "airmon-ng start <interfaz>".
    
2. Airodump-ng: Captura paquetes de redes cercanas, mostrando información relevante como SSID, BSSID, canales y clientes conectados.
    
3. Aireplay-ng: Genera tráfico falso y puede llevar a cabo ataques de inyección de paquetes para obtener IVs (vectores de inicialización) o capturar handshakes en redes WPA/WPA2.
    
4. Aircrack-ng: Utiliza IVs capturados para romper claves WEP con ataques de fuerza bruta. En redes WPA/WPA2, usa handshakes y un diccionario para intentar descifrar la contraseña.
    
5. Uso responsable: Aircrack-ng debe utilizarse legalmente con permiso del propietario de la red, ya que el acceso no autorizado es ilegal y éticamente cuestionable.






