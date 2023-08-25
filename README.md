# Detección de fraude de tarjetas de crédito usando AutoEncoders
Se ha creado un modelo de machine learning basado en autoencoders para abordar un problema altamente desbalanceado de detección de fraude en operaciones con tarjetas de crédito. 

Un autoencoder es una estructura de redes neuronales cuyo objetivo principal es comprimir y luego descomprimir datos, generalmente para reducir la dimensionalidad de los mismos mientras se intenta retener la información más importante. La red se entrena para minimizar la diferencia entre los datos originales y los datos reconstruidos. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/autoencoder.png)

Se entrenará a la red solo con las **transacciones normales**, de esta forma, una vez entrenada podremos ver la diferencia entre la entrada y el resultado de salida de la red. En el caso de que la diferencia entre estos dos vectores sea muy grande, nos indicará que esa transacción es **fraudulenta**. 

### Exploración del conjunto de datos

El conjunto de datos con el que se va a trabajar se encuentra disponible en el siguiente [[enlace]][dataset].   Es un conjunto de datos muy desbalanceado con 284315 transacciones normales y 492 transacciones fraudulentas. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/contador.png)

A priori se podría pensar que la cantidad de dinero que se retira será el factor clave para identificar las transacciones fraudulentas, pero representando los porcentajes de transacciones de cada tipo frente a la cantidad de dinero sacado se puede ver que no es un factor clave en la identificación. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/monto.png)

Realizando un pequeño proceso de exploración de los datos podemos ver que existen características que no presentan diferencia entre los dos típos de transacciones y algunas con una diferencia bastante significativa. Estas diferencias serán la clave que permitirán al modelo distinguir entre ambos tipos. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/f1.png)![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/f2.png)

### Modelo Autoencoder
El modelo propuesto cuenta con un **Encoder** con una capa de entrada de 29 neuronas, con una capa oculta con 20 neuronas. Un **espacio latente** de dimensión 14 y un **Decoder** simétrico al Encoder. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/model_autoencoder.png)

### Evaluación del modelo
Este modelo recibe un vector de dimensión 29 y devuelve un vector de igual longitud. El objetivo es que el modelo reproduzca la entrada. Es por ello que para estimar el rendimiento del modelo se empleará el error cuadrático medio entre el vector de entrada y el vector de salida. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/CodeCogsEqn.png)

Fijaremos un umbral para hacer la clasificación, este será de 0.7. Si el error es menor que 0.7 se supone que el modelo ha predicho con una precisión aceptable el vector de entrada y por tanto es una transacción correcta. Si el error es mayor que 0.7 se supone que la transacción es fraudulenta, ya que es la primera vez que el modelo ve esos patrones en el vector de entrada y por ello no es capaz de decodificarlo correctamente. Recordemos que el AutoEncoder se ha entrenado **solamente** con las transacciones correctas. 

Obteniendo la matriz de confusión obtenemos que el modelo tiene un rendimiento muy aceptable a la hora de identificar las transacciones fraudulentas. Aunque presenta errores al clasificar 4213 transacciones correctas, es preferible que clasifique correctamente las fraudulentas.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/cm.png)![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/confusion_matrix.png)

















[dataset]: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud 




