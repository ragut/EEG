## Integrante
Raúl Andrés Gutierrez Villarraga ([ra.gutierrez@uniandes.edu.co](mailto:ra.gutierrez@uniandes.edu.co))

## Main.py (Controlador)
Archivo principal para arrancar la aplicación y que contiene el direccionamiento de clases

### MainHandler:
Genera los datos basicos del index de la aplicación web.

### ProcessingtHandler:
Genera como resultado un archivo csv consolidado con la extracción de caracteristicas del EDF identificado ventanas con espasmos 0 y sin ellos 1.

Se configura algunas variables indispensables para el procesamiento:

*	**urlPath**: Ubicación donde se encuentra el archivo base EDF donde se extrae frecuencia de muestreo y canales.
* 	**urlNameFile**: Nombre del el archivo base EDF.

Por otra parte, como variables de entrada por interfaz se tienen:
	
*	**directory (Directorio)**: Ubicación de los archivos EDF que seran procesados.
*	**LenWindow (Tamaño de ventana)**: Se establece el tamaño de las ventanas en segundos para analizar.
*	**select_Allchannel - select_channels (Canales)**: Los canales que se desean tomar para la extracción de caracteristcias	
*	**band_onda (Extrar bandas)**: Se elige método para la extracción de bandas. Solo se utiliza para la función *drawSignals_Channels* - [Documentación](https://raphaelvallat.com/bandpower.html "Documentación")
	*	Welch Method
	*	Multitaper
*	**peaks (Picos)**: Se selecciona el método de extracción de picos. En esta parte se puede configurar algunos parametros de acuerdo a la estrategia seleccionada.
	*	Distance
	*	Prominence
*	**filters (Filtro)**: Se selecciona el método para limpiar la señal.  En esta parte se puede configurar algunos parametros de acuerdo al filtro seleccionada.
	*	Butterworth
	*	Variables 
	*	Sin filtro
	*	Wavelet
	*	STFT Hard
	*	STFT Soft

Variables y funciones adicionales:

*	**filesDirectory**: Obtiene los archivos de la carpeta para ser procesados.	
*	**dataEDF.drawSignals_ChannelsDWT**: Realiza la extracción de características por archivos basado en la Discrete Wavelet Transform.
*	**dataEDF.drawSignals_Channels**: Realiza la extracción de características por archivos basado en el método para la extracción de bandas.

Nota: Estas dos ultimas funciones, generan archivos cvs por canal de las características identificando si existe un espasmo o no.

*	**dataEDF.mergeData**: Unifica los archivos cvs en un unico archivo.

### ProcessingtHandler: