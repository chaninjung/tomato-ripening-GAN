## 🍅Generative Images about Tomato-Ripening-Images using GAN🍅
The data types are divided into turning, pink, and red, and there was an imbalance in the data because the turning data was relatively small. Therefore, we decided to create a virtual image through GAN.

<p align="center">
<img src="https://github.com/chaninjung/tomato-ripening-GAN/assets/156671303/25c71224-e2fd-4893-9a7e-a93a15435981.gif">
  
<br>

### Training data
The source of the source database is as follows. (TOTAL 2,448)
https://universe.roboflow.com/tharindu-3vjtz/ripe-check-tomato
</p>
The following is my database that implemented ARGUMENT. (TOTAL 7,831)
https://universe.roboflow.com/posco-wyx1a/copy_project_agumentation_7831

<br>
<br>

### GAN for YOLOv5
GAN is used to augment small data sets, such as in this case.
2,000 of the TURNING images enhanced using GAN were randomly selected, and 9,831 images were later learned in the YOLOv5 model.

<br>

### GAN Parameters



GAN is a model in which two neural networks, the generator and the discriminator, cooperate to generate and distinguish data through adversarial learning. I first learned by generating noise, allowing the generator to create a fake image, and then by allowing the discriminator to distinguish it.
The main parameters are as follows. Epoch is 34,100, and for batch size and optimizer, the values with the lowest FID were selected experimentally. </p>
![lossfunction](https://github.com/chaninjung/tomato-ripening-GAN/assets/156671303/a5d011f0-86ba-4a43-b779-d79dcfaf358f) </p>
In the initial 5,000 epoch and below, the discriminator learned faster than the constructor to distinguish the fake data well, but after that, the constructor and discriminator loss values began to become out of balance and stopped learning before those values were out of balance.
