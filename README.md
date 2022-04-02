## Integrante
Raúl Andrés Gutierrez Villarraga ([ra.gutierrez@uniandes.edu.co](mailto:ra.gutierrez@uniandes.edu.co))

## Main.py (Controlador)
Archivo principal para arrancar la aplicación y que contiene el direccionamiento de clases

### MainHandler:
Genera los datos basicos del index de la aplicación web.

### ProcessingtHandler:
Genera como resultado un archivo csv consolidado con la extracción de características del EDF identificado ventanas con espasmos 0 y sin ellos 1.

Se configura algunas variables indispensables para el procesamiento:

*	**urlPath**: Ubicación donde se encuentra el archivo base EDF donde se extrae frecuencia de muestreo y canales.
* 	**urlNameFile**: Nombre del el archivo base EDF.

Por otra parte, como variables de entrada por interfaz se tienen:
	
*	**directory (Directorio)**: Ubicación de los archivos EDF que seran procesados.
*	**LenWindow (Tamaño de ventana)**: Se establece el tamaño de las ventanas en segundos para analizar.
*	**select_Allchannel - select_channels (Canales)**: Los canales que se desean tomar para la extracción de características	
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

*Nota: Estas dos ultimas funciones generan archivos csv por canal de las características identificando si existe un espasmo o no.*

*	**dataEDF.mergeData**: Unifica los archivos csv en un unico archivo.

### MergetHandler:
Unifica los archivos csv con características en un solo archivo csv.

*	**directory (Directorio)**: Ubicación de los archivos csv que seran unificados.
*	**file_final.mergeData**: Unifica los archivos csv en un unico archivo.

### EvaluateModeltHandler:
Contribuye a la evaluación de modelos de Machine Learning y Sampling con diferentes mecanismos de evaluación. Se puede generar evaluación de características a traves de PCA.

Se configura algunas variables indispensables para el procesamiento:

*	**repository**: Directorio donde se encuentra el archivo csv a procesar.
*	**filesDirectory**: Mapea los archivos en la carpeta de procesamiento.
*	**headDataframe**: Obtiene nombre de las características para seleccionar el predictor.

Por otra parte, como variables de entrada por interfaz se tienen:

*	**predictor**: Se selecciona la característica la cual será el predictor del modelo.
*	**sampleSpasm**: Se determina la cantidad de muestras que serán separadas (utilizadas como test). El resto de muestras con Espasmos serán utilizadas para entrenar el modelo.
*	**fileProcess**: Archivo seleccionado con características para ser procesado.
*	**value_pca**: Se habilita PCA para reducir dimensionalidad de características.
*	**modeltoEvaluate**: Se puede seleccionar el modelo a entrenar.
	*	DecisionTree
	*	SVC
	*	GaussianNB
	*	EasyEnsemble
	*	BalancedRandomForest
	*	RandomForest
	*	SGDClassifier
	*	LinearSVC
*	**validationModel**: Se puede seleccionar el mecanismo de evaluación.
	*	Kfolds
	*	RepeatedStratifiedKFold
*	**Sampling**: Tipo de estrategia de muestreo.
	*	SMOTEENN
	*	SMOTE
	*	UPOVER
	*	NONE
*	**over_value**: Se determina el rango de el overSampling sobre la muestra. 
*	**under_value**: Se determina el rango de el underSampling sobre la muestra.
*	**value_k**: Configuración del K correspondiente al número de vecinos para construir las muestras (Solo se utiliza para SMOTE y SMOTEENN)

Otras variables y funciones:

*	**control_file**: Carga el archivo a procesar.
*	**dataframe_base**: Genera dataframe del archivo csv, se elimina datos donde no se encuentren datos vacios.
*	**data_y_base**: Dataframe unicamente con la variable predictora
*	**data_x_base**: Dataframe con las características de cada variable predictora.
*	**data_x_spasms, data_y_spasms**:  Datos filtrados y ajustados con espasmos.
*	**data_x_nospasms, data_y_nospasms**: Datos filtrados y ajustados con espasmos.
*	**x_train, y_train**: Se define conjunto de datos de entrenamiento.
*	**x_test, y_test**: Se define conjunto de datos de entrenamiento.
*	**cv**: Tiene la configuración del metodo de cross validation.
*	**param_grid**: Tiene la configuración del modelo a probar.
*	**modeltChoose**: Define el modelo a probar.

Para el PCA, se define la variable:
*	**n_comp**: Cantidad de componentes que se desea reducir lsa características obtenidas inicialmente.
*	**pca_pipe**: Se crea el flujo de construcción del PCA.
*	**proyecciones, proyecciones_test**: Resultado de la reducción de dimensiones a través de PCA. Estas serán los datos de entrada para entrenar y probar el modelo.



