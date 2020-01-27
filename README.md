# Modak-Image-Recognition
A Neural Network which recognises Modak in images
[Link to Dataset](https://drive.google.com/open?id=1pIZQh_a8TLnjj_2Lm6Lu4PNa9Hcpq84R)

Modak Image Recognition Task

I have used keras for this task which is a binary classification problem to predict if an image consists of modak or not. All code is available in the jupyter notebook in the repository. I have used Google Colab which gives free to a pretty powerful GPU thereby speeding up training time significantly.

## 1. Data collection and preparation of images

I obtained the images for this task from google images. I used [the following link](https://chrome.google.com/webstore/detail/download-all-images/ifipmflagepipjokmbdecpmjbibjnakm?hl=en) chrome extension.
The usage is simple, Enter a search keyword (modak) and then scroll down to the very end till all the images in the page are displayed.
After this, clicking on the extension downloads all the images in a zip file. 

I repeated the search with similar keywords like 'ukadiche modak' and 'sweet modak'. After combining all the obtained images, I went through the folder containing these images and removed some irrelevant images.

After doing this, I had around 2339 images. 

Next, for getting images apart from  modak, I entered the keywords 'Laddu', 'Gulab Jamun' and 'Boorelu'. All of these were sweets which were round in shape. So, the main idea was to see if the model was able to differentiate between modak(which is kind of round in shape) and the other sweets which were round but not modak.

I used data augmentation techniques like Random Horizontal Flip, Random rotation, zooming to make the model more robust and generalize better.

## 2. Training and validation split

I used 90 % of the total number of images as the training set which were about 2107 and the remaining 232 images for validaion.

## 3. Training the network

I used VGG16 network as the backbone and froze the weights of the backbone leayers during training. I added a fully connected layer with 'relu' as the activation function, a dropout layer to prevent overfitting and then finally a fully connected and then finally a Dense Layer with sigmoid activation funtion since this is a binary classification problem.

I used the Adam Optimizer with learning rate 0.01 since it is empirically proven to converge faster compared to others like sgd. I used a batch size of 32 as it has a reasonable tradeoff with speed and I obtained good accuracy.

I set the total number of epochs to be trained as 20 and used a callback for Stopping Early on in case the validation accuracy did not increase for more than 3 epochs and saved only the best weights of the model. In my case, it stopped at the 9th epoch as it already achieved good accuracy

## 4. Results

I obtained a final training accuracy of 96.19 % and a validation accuracy of 97.5 %
Plotting the loss and accuracy as the training progressed:
![alt text](https://github.com/jiteshm17/Modak-Image-Recognition/blob/master/screenshots/accuracy_loss_plot.png)

## 5. Testing the model

I used a test set to see the prediction results for a few sample images and the model did a good job of classifying them correctly.
