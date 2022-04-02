## Integrante
Raúl Andrés Gutierrez Villarraga ([ra.gutierrez@uniandes.edu.co](mailto:ra.gutierrez@uniandes.edu.co))

## Main.py (Controlador)
Archivo principal para arrancar la aplicación y que contiene el direccionamiento de clases

### MainHandler:
Genera los datos basicos del index de la aplicación web.

### ProcessingtHandler:
Genera como resultado un archivo csv consolidado con la extracción de caracteristicas del EDF identificado ventanas con espasmos 0 y sin ellos 1.

Se configura algunas variables indispensables para el procesamiento:
Markup :
	*	urlPath: Ubicación donde se encuentra el archivo base EDF donde se extrae frecuencia de muestreo y canales.
	* 	urlNameFile: Nombre del el archivo base EDF.

Por otra parte, como variables de entrada por interfaz se tienen:
	
	*	directory (Directorio): Ubicación de los archivos EDF que seran procesados.
	*	LenWindow (Tamaño de ventana): Se establece el tamaño de las ventanas en segundos para analizar.
	-	select_Allchannel - select_channels (Canales): Los canales que se desean tomar para la extracción de caracteristcias	
	-	band_onda (Extrar bandas): Elegir metodo para la extracción de bandas. Solo se utiliza para la función drawSignals_Channels.
		<p align="left"> <a href="https://raphaelvallat.com/bandpower.html" target="_blank"> Más información</a></p>
			-	Welch Method
			-	Multitaper
	-	peaks (Picos): Seleccionar metodo de extracción de picos. En esta parte se puede configurar algunos parametros de acuerdo a la estrategia de picos seleccionada.
			-	Distance
			-	Prominence
	-	Filtro: Seleccionar metodo para limpiar la señal:
			-	Butterworth
			-	Variables 
			-
			-
			-
