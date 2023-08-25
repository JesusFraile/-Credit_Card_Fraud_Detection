# -Credit_Card_Fraud_Detection
Se ha creado un modelo de machine learning basado en autoencoders para abordar un problema altamente desbalanceado de detección de fraude en operaciones con tarjetas de crédito. 

Un autoencoder es una estructura de redes neuronales cuyo objetivo principal es comprimir y luego descomprimir datos, generalmente para reducir la dimensionalidad de los mismos mientras se intenta retener la información más importante. La red se entrena para minimizar la diferencia entre los datos originales y los datos reconstruidos. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/autoencoder.png)

Se entrenará a la red solo con las **transacciones normales**, de esta forma, una vez entrenada podremos ver la diferencia entre la entrada y el resultado de salida de la red. En el caso de que la diferencia entre estos dos vectores sea muy grande, nos indicará que esa transacción es **fraudulenta**. 

El conjunto de datos con el que se va a trabajar se encuentra disponible en el siguiente [[enlace]][dataset].   Es un conjunto de datos muy desbalanceado con 284315 transacciones normales y 492 transacciones fraudulentas. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/contador.png)


[dataset]: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud 
