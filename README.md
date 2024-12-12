# Plant-Insight

**Dataset used for final training:**
https://drive.google.com/drive/folders/1TudqpfLC2QC_5zFD_cS1wBnoewUfgTcO?usp=drive_link

**The workflow of training:**

During training, we encountered several major issues:

1. Icompatibilities
2. Insufficient CPU/GPU power
3. An imbalanced dataset of suboptimal quality

The first week of the project was experimental. Initially, we could not install TensorFlow directly on the computer due to incompatibilities with the Python version. To address this, we explored cloud-based platforms and started using Google Colab. We experimented with the VGG16 pre-trained model but eventually switched to the ImageNetV2 model. During training, we purchased additional GPU power, as training on a CPU was slow and inefficient. Unfortunately, connection losses on Colab caused us to lose progress multiple times.

Despite these challenges, we documented one of our attempts in attemptFirst.ipynb. Training took around 20 hours for approximately 20 epochs (excluding lost progress). The test accuracy reached 70%, but the confusion matrix showed that the model struggled to distinguish between the 47 plant types in the dataset.

Next, we worked on building an iOS mobile app. The app uses the trained model to identify plants from user photos. To embed the model into the app, we needed to convert it to a Core ML format. However, this was not possible with TensorFlow version 2.17, which led to further compatibility issues.

**Link to GitHub Swift App repository:**
https://github.com/Jessenia111/ToxicFlowerApp

Although the dataset contained various high-quality images, most classes had too few samples. For example, some classes had only 100 images, while the majority had a maximum of 450. This small dataset size, combined with the similarity between plant types, made training a classifier challenging. To address this, we manually reduced the dataset to 14 classes with the largest number of images. We then retrained the model using TensorFlow 2.6, resolving compatibility issues and using a more powerful CPU. This attempt, documented in **attemptSecond.ipynb**, ran for 195 epochs and achieved 85% test accuracy — better than earlier results.

We also tried expanding the dataset by adding five new classes (from another Kaggle dataset), increasing the total to 19 classes. The newly added classes had around 900 images each, making the dataset more imbalanced. To address this, we experimented with gradually unfreezing layers and adding class weights. This attempt, documented in **attemptThird.ipynb**, achieved 89% accuracy. However, the confusion matrix revealed that the model still struggled to differentiate between plants, and in practice, the app rarely provided correct predictions.

Ultimately, we decided to stick with the second model, documented in **attemptSecond.ipynb**. This model achieved 85% accuracy, successfully identifying 14 plant types and working reliably in the mobile app.

Although the second model was selected for the poster session, we continued experimenting. In our fourth attempt, documented in **attemptFourth.ipynb**, we introduced early stopping. However, this did not result in significant improvements.


