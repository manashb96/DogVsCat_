# DogVsCat_

The data was split into 2 folders of train and test and we were given one csv files with names from the test folder.  

The files in the train folder was named as '`cat.x`' and '`dog.x`' with a total of 25000 files
*This code was compiled in Kaggle.*  

We first create a dataframe from the train and test directories and label them according to if it was named `cat` or `dog` in file.  
We then split the data set into train and valid dataset.  

We then create two ImageDataGenerators based on if it is a train or valid dataset.  
Also we use 2 types of Data generators on the basis of whether it is a Vanilla model or a ResNet model.  
If it was a ResNet model then we use a preprocess_input  
Now we create a CNN model using Sequential API with 2 blocks of two conv2d layers followed by 2 blocks of three conv2d layers.  
This is followed by 4 Dense layers with a BatchNormalization and Drop out Layer in between.
We fit the model and get a validation_set accuracy of 92%.

We then create a Resnet50 model with non trainable layers and then we add 2 Dense layers as head of the model. We get a validation accuracy of 99%  

Now for the test dataset we couldn't use DataGenerator for this because of some reason which I probably think is due to the architecture of the test folder and according to flow_from_directory we need to have a structure of Folder->SubFolder->images.  

Instead we create a function to get the filenames from the test directory and then use `load_img` to create an array and then predict it using the model and kept a threshold of 0.5 where if it is greater than 0.5 then predict = 'dog' else 'cat'  

We then create a 4x3 subplot with text which gives predicted result of both the Vanilla Model and also the Resnet model.
