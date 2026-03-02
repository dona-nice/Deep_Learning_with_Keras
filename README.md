## Thesis Project: Intrusion Detection via Feedforward Deep Neural Networks
### 1. Abstract / Research Summary
This repository contains the implementation and experimental framework for my Master’s thesis. The research focused on the efficacy of Deep Feedforward Architectures in classifying multi-class network intrusions.

+ **The Problem:** Traditional machine learning models (SVM, Random Forest) often struggle with high-dimensional feature spaces and non-linear relationships in modern network traffic.

+ **The Solution:** Developed a Feedforward Deep Neural network optimized with dropout regularization and Adam optimization to detect attack patterns.

+ **The Result:** Achieved an accuracy of 89% on the NSL-KDD dataset, specifically outperforming baseline models in binary classification of traffic intrusion as normal or attack.

### 2. Methodology & Mathematical Framework
The model utilizes a deep architecture where each hidden layer $h_i$ applies a non-linear transformation:

$$h_i = \sigma(W_i h_{i-1} + b_i)$$

+ **Activation Function:** ReLU was utilized for hidden layers to mitigate the vanishing gradient problem, while Sigmoid was used for the output layer to provide class probabilities.

+ **Loss Function:** Binary Cross-Entropy was employed for binary classification:

$$H(p) = -p \log_2(p) - (1 - p) \log_2(1 - p)$$

**Optimization:** Hyperparameter tuning was performed on learning rates, batch sizes, and hidden layer depth to minimize the loss $H(p)$.

### Enhancing Cybersecurity with Deep Learning: A Novel Network Intrusion Detection System

### Introduction

The growth of internet use has revolutionized communication, leading to vast data transmission across computer networks. However, this digital evolution has escalated security threats, with malicious intrusions now a common hazard to sensitive data. Cybersecurity measures like Intrusion Detection Systems (IDSs) play a critical role in safeguarding networks. Traditional IDSs, such as signature-based systems like Snort, detect known threats but often fail to recognize new, evolving attacks. This limitation has driven research toward deep learning, a branch of machine learning (ML) that is particularly promising for handling complex, large-scale data. This article explores the potential of a deep learning-based IDS that addresses these challenges, drawing on the research by Donatus Ifeanyichukwu Edeh, whose thesis at the University of Turku demonstrated the superiority of a Feedforward Deep Neural Network (FFDNN) for intrusion detection.

### Challenges of Existing Intrusion Detection Systems

Signature-based IDSs primarily rely on predefined rules and are adept at recognizing known attack patterns. However, as attackers continuously develop new threats, these IDSs struggle to keep up. Anomaly-based IDSs that utilize ML approaches aim to identify unusual network behavior indicative of potential threats. While more adaptable, these systems face limitations when handling massive datasets, as they often require substantial computational resources and incur longer runtimes.

### Deep Learning: A Solution for Enhanced Detection

Edeh’s research proposed an FFDNN model for intrusion detection, specifically designed to overcome the limitations of both signature-based and conventional ML IDSs. By applying deep learning, the IDS leverages large datasets and learns complex patterns to identify novel threats more accurately. His study used the NSL-KDD dataset, a widely utilized dataset for intrusion detection benchmarking, allowing for rigorous testing of the model's effectiveness.

### Model Architecture and Training

The FFDNN model was developed using Google’s Colaboratory software, combining the Keras API with TensorFlow. Three FFDNN variants were tested, each with a network architecture that included two hidden layers. Different configurations of neurons were applied: 64 and 32 neurons; 32 and 16 neurons; and 512 and 256 neurons. The ReLU activation function was used for hidden layers, while a sigmoid activation function, suitable for binary classification, was utilized in the output layer. Training optimization was achieved with the Adam optimizer and a 0.2 dropout rate to prevent overfitting. The FFDNN variants were trained over 16, 20, and 20 epochs with batch sizes of 256, 64, and 128, respectively.

### Results: Comparing Deep Learning with Conventional Algorithms

The performance of the FFDNN models was impressive, achieving test accuracies of 89%, 84%, and 87%, surpassing the results obtained with traditional ML models like Random Forest, K-nearest neighbor, Logistic Regression, Decision Tree, and Naïve Bayes, which achieved accuracy scores between 76% and 81%. Metrics such as False Positive Rate (FPR), False Alarm Rate (FAR), F1 Score, and Precision further confirmed the superior performance of the deep learning models.

### Why FFDNNs Outperform Traditional ML in Intrusion Detection

FFDNNs provide an architectural advantage with their dense layers, allowing them to scale effectively with large datasets. This scalability enables faster computation, a critical factor when handling extensive network traffic data. The deep neural network's ability to manage runtime efficiently while achieving high accuracy demonstrates its suitability for real-time intrusion detection in cybersecurity applications.

### Results Analysis and Discussion 
In this thesis, the researcher has conducted a comparative study of the machine learning approaches for intrusion detection using conventional machine learning algorithms and feedforward deep neural networks (FFDNN). My main idea was to develop an FFDNN as a 
classifier to classify network traffic intrusions in the NSL-KDD dataset as normal or attack, while using the conventional machine learning approaches as my controlled experiment. The analysis was performed on five different ML algorithms (DT, LR, RF, NB, KNN), and their performances on the test data gave 81%, 76%, 77%, 77%, 77%, respectively. 

I also analysed three different FFDNNs, namely FFDNN-1, FFDNN-2, and FFDNN-3, based on different hyperparameter values, feature reduction, and data encoding techniques. Their performance on the test data was 89%, 84%, and 87%, respectively. Some important performance indicators, namely, accuracy, true positive rate (TPR = recall), false-positive rate (FPR), precision, F1 measure, and ROC area under the curve (AUC) are used as the bases to judge the model's performance.

<div align="center">
  <img src="https://github.com/user-attachments/assets/5804b98d-e284-4ce2-9084-12bc64e3c93f" alt="Alt Text" width="500" height="300">
</div>
<div align="center">
<img src="https://github.com/user-attachments/assets/cc1585c2-23f2-4677-979f-b1e169acc652" alt="Alt Text" width="500" height="300">
</div>
<div align="center">
<img src="https://github.com/user-attachments/assets/98d06605-e840-4f02-8b62-93650c08bbdc" alt="Alt Text" width="500" height="300">
</div>

Considering the overall performances of all models, the FFDNN-1 performed best with the highest detection accuracy of 89% and precision of 91%, however, the precisions of the DT, RF, and NB were quite high even though their detection accuracy was not above 80% except DT that gave 81%. High precision indicates that the models are reliable compared to low precision, which can result in a lot of false positives, as in the case of the KNN classifier. Another point to note is that high recall does not necessarily mean the best performance, but rather a higher F1-measure shows that the model performed very well. This is because the F1 measure takes into account the harmonic mean of precision and recall, so it tells how accurate a model is. From the experiment, FFDNN-1 had an F1-measure of 90%, which makes it the best model; other FFDNN variants also had a high F1-measure when compared to the F1-measure of the conventional machine learning algorithms.

Another important metric that shows that the FFDNNs performed well is their high ROC area under the curve (AUC); FFDNN-1, FFDNN-2, and FFDNN-3 all had values of 95%, 86%, and 92%, respectively. The higher the AUC value, the more optimal the model becomes (note that 100% indicates a perfect model). Also, it is good to know that the primary aim is to develop machine learning models that would maintain an acceptable true positive rate (TPR) or detection rate (DR) with a low false alarm rate (FAR) or false positive rate (FPR). It was also shown that DT, RF, and NB had very low FAR of 5%, 3%, and 2% respective compared to FFDNNs 11%, 16%, and 13%. This is good, even though their detection rates were not as high as the FFDNNs; however, there could still be an improvement in ensuring that the FFDNNs produce low FAR, since they are scalable in terms of architecture, but this would involve more computational cost. 

Any variant of the feedforward deep neural network (FFDNN-1, FFDNN-2, and FFDNN-3) has the capability as a classifier to classify network traffic intrusions with a high detection rate while offering a reduced FAR; it only depends on the model design, hyperparameters, and architecture. Limitations in the ML approach for intrusion detection are high FAR, and how to strike a balance between false positives and false negatives in terms of intrusion detection policies or profiling. This limitation can be solved by the development of a deeper neural network or the use of another variant of a deep neural network, like the convolutional deep neural network (CNN). 

### Conclusion

This research emphasizes the potential of deep learning to advance cybersecurity. For organizations handling large-scale networks, FFDNN-based IDSs offer a promising solution for timely and accurate threat detection, outperforming conventional methods in both speed and accuracy. As cyber threats evolve, deep learning continues to offer innovative pathways for enhancing network security, making it a critical component in the future of digital protection.

**Keywords:**  Cybersecurity, Deep learning, Intrusion Detection System, Machine learning, Computer networks

