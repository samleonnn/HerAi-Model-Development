# HerAi Model Development
HerAi is a digital waste bank that helps users to increase awareness of waste segregation.
In this repository, we develop our model to recognize whether a trash is belong to Organic, Recyclable, or Non-Recyclable category.

Please visit [this link](https://github.com/heriirianto/Capstone-Project-Bangkit2022) to see the full project.

We are working on Convolutional Neural Network for image classifcation. Several architectures have been tried as follows:
* [Basic CNN](https://github.com/samleonnn/HerAi-Model-Development/blob/main/WasteSegregation_modelDev.ipynb)
* [Inception V3 Transfer Learning](https://github.com/samleonnn/HerAi-Model-Development/blob/main/WasteSegregation_TransferLearning_InceptionV3.ipynb)
* [Xception Transfer Learning](https://github.com/samleonnn/HerAi-Model-Development/blob/main/WasteSegregation_TransferLearning_Xception.ipynb)
* [MobileNet Transfer learning](https://github.com/samleonnn/HerAi-Model-Development/blob/main/WasteSegregation_TransferLearning_MobileNet.ipynb)

You can visit files above to see in more details. We do a lot of architecture combination on our project. Based on our experiment, we found that Xception and MobileNet perform the best compare to the other architecture. Visit [this link](https://docs.google.com/spreadsheets/d/1-Bg4fKHLPqKrv1XUlZrT1bGuUyATv9mq/edit?usp=sharing&ouid=111090360116109745014&rtpof=true&sd=true) to see the accuracy in number.

HerAi is designed to be an Android mobile application and users allows to detect the image offline. We realize working with other complex pre-built model is not sufficient to meet the needs. Therefore, we decide to use MobileNet transfer learning and we connected with our own model on top of it. MobileNet transfer learning performs very similar to Xception transfer learning, but the training time and file weight are really different.

For your information, SavedModel file of Xception transfer learning gave us 1GB of file. Meanwhile, SavedModel file of MobileNet transfer learning gave us 29MB of file. Both performing really well, but the model chosen is depends on the model and deployment needs.

During our research, we also find out which neural network forms most efficient for our project. We are looking for a model with highest accuracy and lightest model size. We are comparing between Flatten() layer and GlobalAveragePooling2D() layer. We are looking for a model to work on classification task. As a result, we found that using GlobalAveragePooling2D() layer is better on this and also gives us huge gap on SavedModel file size.
>TL;DR: Using the same model architecture and train in 10 epochs, using Flatten() layer gives us 309 MB SavedModel size. Using GlobalAveragePooling2D() layer gives us 33.4 MB SavedModel file size.

Therefore, we use GlobalAveragePooling2D() layer for our model to connect the convolution base with our neural network.