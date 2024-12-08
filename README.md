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

This is why we spent some time on manual work with the dataset: we left only 13 classes that contained the biggest amount of pictures. We made another attempt of training the model on a reduced dataset using much more powerful CPU. We run totally 195 epochs and reached 85% accuracy on test data, which was already much better. This attempt is documanted in **attemptSecond.ipynb**.

Then we decided to add other 5 classes from another dataset of a better quality with a bigger amount of pictures in each class. Totally we had 18 classes in new dataset.

After that we made one more attempt in training the model using same powerful CPU. We also did some experimenting with unfreezing layers and added classweights (because of the imbalance in dataset). Eventually we trained the model for the third time: **finalAttempt.ipynb**.
