# Fraud Detection in Banking Transactions Using Autoencoders

Efficient detection of credit card fraud has long been a persistent challenge for financial institutions and businesses. The sophistication of fraud techniques and the continuous development of new strategies make identifying fraudulent transactions a crucial aspect of financial security. In this context, the application of advanced machine learning techniques, such as autoencoders, has proven to be a promising solution, especially when working with highly imbalanced datasets.

## Autoencoders
Autoencoders are a class of artificial neural networks used for unsupervised learning of data representations. Their distinctive capability lies in compressing data into a lower-dimensional space and subsequently reconstructing it with high accuracy. This compression–reconstruction process enables the identification of intrinsic patterns and anomaly detection in data.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/autoencoder.png)

### Training and Core Concept

In the context of fraud detection in banking transactions, the autoencoder is trained using normal transactions, allowing it to learn their typical features and patterns. Once trained, the autoencoder compares the characteristics of a new transaction with those it has learned. If the discrepancy between the input and the reconstructed output is significant, the model indicates that the transaction may be fraudulent.

## Dataset Exploration

The success of any fraud detection technique depends on its ability to handle highly imbalanced datasets. The dataset used in this study contains 284,315 normal transactions and only 492 fraudulent transactions. This disproportion underscores the need for approaches capable of managing such imbalances. The dataset is publicly available at the following [[link]][dataset]. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/contador.png)

One might initially assume that the transaction amount would be the key factor in identifying fraudulent behaviour. However, visualising the proportion of transaction types against transaction amounts shows that it is not a decisive factor.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/monto.png)

A brief exploratory analysis reveals that some features show little to no difference between normal and fraudulent transactions, while others exhibit significant variation. These differences are essential for enabling the model to distinguish between the two types.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/f1.png)![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/f2.png)

## Model Design and Architecture

The autoencoder model developed for banking fraud detection consists of three main components:
1. **Encoder:** Reduces the dimensionality of input features, capturing the most important transaction patterns. It includes an input layer of 29 neurons and a hidden layer of 20 neurons.
2. **Latent Space:** Represents features in a lower-dimensional space containing the essential transaction information. This consists of 14 dimensions.
3. **Decoder:** Reconstructs compressed data from the latent space back into its original form, mirroring the structure of the Encoder.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/model_autoencoder.png)

The symmetric architecture of the autoencoder enables compression and reconstruction with the objective of minimising the difference between original and reconstructed data.

## Model Evaluation and Validation

To assess the effectiveness of the autoencoder in fraud detection, the mean squared error (MSE) is used as the performance metric. A predefined threshold is applied to classify transactions as normal or fraudulent. If the reconstruction error exceeds this threshold, the transaction is flagged as potentially fraudulent.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/CodeCogsEqn.png)

Although the model occasionally misclassifies normal transactions, its ability to accurately identify fraudulent cases remains crucial. The confusion matrix shows that the model achieves acceptable performance in detecting fraud, even at the expense of some errors in legitimate classifications.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/cm.PNG)    ![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/confusion_matrix.PNG)

## Conclusión
Fraud detection in banking transactions through the use of autoencoders presents a promising approach in combating financial fraud. The model’s ability to learn patterns of normal transactions and identify anomalies in new data makes it a valuable tool for preventing financial losses and safeguarding customer assets. While challenges associated with imbalanced datasets remain, the autoencoder approach demonstrates its usefulness and potential for early and accurate fraud detection in the financial domain.


[dataset]: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud 
