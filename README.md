# Plant-Insight

**Dataset used for final training:**
https://drive.google.com/drive/folders/1TudqpfLC2QC_5zFD_cS1wBnoewUfgTcO?usp=drive_link

**The workflow of training:**

During training we faced several main issues:
1. A variety of incompatibilities
2. Not enough CPU/GPU power
3. Imbalanced dataset of not the greatest quality

While encountering those challenges we made several attempts in model trainig, one of which is documented in the notebook **attemptFirst.ipynb**. As can be seen, model training took there many hours. We did approximately 20 epochs, solely running them took about 15-20 hours. Test accuracy was 70%, but confusion matrix showed that model struggled to make difference between various plants (there were 47 types of them). 

Even though dataset had various pictures in each class and pictures were of a good quality, it still had a disadvantage: many classes contained too little instances. We made decision to eliminate some plants classes from the dataset, because the majority had only 450 images on average (a few contained only 100 though). Given that there is no wonder the model struggled to learn, because the amount of data was not sufficient and plants generally look very much alike. 

This is why we spent some time on manual work with the dataset: we left only 13 classes that contained the biggest amount of pictures. We made another attempt of training the model on a reduced dataset using much more powerful CPU. We run totally 195 epochs and reached 85% accuracy on test data, which was much better. This attempt is documanted in **attemptSecond.ipynb**.

Then we pursued to build an IOS mobile app. Mobile app identifies the plant from the picture made by a user with the help of the trained model.

**Link to GitHub Swift App repository:**
https://github.com/Jessenia111/ToxicFlowerApp

Additionaly we decided to try another way of training. We manually added five more classes to our existing dataset resulting to the dataset of 19 classes. New added classes had around 900 images each, which made dataset more imbalanced. We tried to experiment with gradually unfreezeing layers and adding class weights to address issue with imbalanced dataset. This attempt is documented it **attemptThird.ipynb**. We reached even higher accuracy, but confusion matrix showed that model very much struggled with identifying plants. In practice while using mobile app with this model, it almost never gave the right answer.

**Eventually** we decided to stick to our second model: **attemptSecond.ipynb**. Its accuracy is 85% and precision is 76%, it identifies 14 plant types and in practice works well. This is the model we presented during poster session and used in our app.


