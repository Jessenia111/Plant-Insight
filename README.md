# Plant-Insight

**Dataset used for final training:**
https://drive.google.com/drive/folders/1TudqpfLC2QC_5zFD_cS1wBnoewUfgTcO?usp=drive_link

**The workflow of training:**

During training we faced several main issues:
1. Incompatibilities
2. Not enough CPU/GPU power
3. Imbalanced dataset of not the greatest quality

The first week of making this project we would rather call experimental. For some time we could not install tensorflow directly to the coumputer because of incompatibilities with python version and etc. So we started looking for solutions to train the model in a cloud-based platform, this is how we got exposed to Google Collab. We experimented with VGG16 pre-trained moodel, but then decided to stck to ImageNetV2 model. During training we even ended up paying 11 euros to gain more GPU power, because training on CPU in there was too long and inefficient, let alone saying that sometimes connection got lost and all the process of training was gone with it. 

Majority of these attempts came in vail, but we still decided to document one of them here in the notebook **attemptFirst.ipynb**. As can be seen, model training took there many hours. We did approximately 20 epochs (except for those that were gone due to connection losses), solely running them took about 20 hours. Test accuracy was 70%, but confusion matrix showed that model struggled to make difference between various plants (there were 47 types of them). 

Then we pursued to build an IOS mobile app. Mobile app identifies the plant from the picture made by a user with the help of a  trained model. We realised that to embed the trained model into the app, we neede to convert it to the Core Ml model. With the version of tensorflow 2.17 we previously tried the training it was not possible. So we again faced problems with incompatibilities.

Even though dataset had various pictures in each class and pictures were of a relatively good quality, it still had a disadvantage: classes in general contained a few instances. Given that plants are all green and have leafs, training a classifier on 350 pictures and in some cases even fewer was a struggle. We made decision to eliminate some plants classes from the dataset, because the majority had only 450 images in total (a few contained only 100 though). Given that there is no wonder the model struggled to learn, because the amount of data was not sufficient and plants generally look very much alike. 

This is why we spent some time on manual work with the dataset: we left only 14 classes that contained the biggest amount of pictures. We made another attempt of training the model. We found a better recource of installing tensorflow 2.6, the version we needed to convert the model to Core Ml. Finally resolving the incompatibilities did not seem to be an uphill battle. We managed to train the model once again on a reduced dataset using much more powerful CPU. We ran 195 epochs in total and reached 85% accuracy on test data with 76% precision, which was so much better than everything we achieved before. This attempt is documanted in **attemptSecond.ipynb**.

**Link to GitHub Swift App repository:**
https://github.com/Jessenia111/ToxicFlowerApp

We decided to try another way of training. We manually added five more classes to our existing dataset (using another dataset from Kaggle) resulting to the dataset of 19 classes. New added classes had around 900 images each, which made dataset more imbalanced. We tried to experiment with gradually unfreezeing layers and adding class weights to address issue with imbalanced dataset. This attempt is documented it **attemptThird.ipynb**. We reached even higher accuracy - 89%, but confusion matrix showed that model very much struggled with identifying plants. In practice using this model in the built mobile app, it almost never gave the right answer. 

**Eventually** we decided to stick to our second model and present it on the poster session: **attemptSecond.ipynb**. Its accuracy is 85% and precision is 76%, it identifies 14 plant types and in practice works well (using mobile app). 

Even though we knew that the poster was already made and we were to present our second model, we still wanted to try to achieve other results in training. We used additionaly early stopping. This attempt is documented it **attemptFourth.ipynb**.


