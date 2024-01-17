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
{:format :pointed-dict, :data [{#uuid "f9a12520-21c3-4f76-b118-1fa700d92817" {:entity-type :block, :coords {:y-start 0.6277533814443512, :x-start 0.4113824444779575, :x-end 0.7174712910724937, :y-end 0.9273052777777776}, :events [], :original-aspect-ratio? true, :media-asset-ids #{#uuid "a8f23f8d-3b7a-4de3-a582-a62916b4675d"}, :image-aspect-ratio 2, :id #uuid "f9a12520-21c3-4f76-b118-1fa700d92817", :image-position {:x 43.24324324324364, :y 100}, :url "https://pitch-assets-ccb95893-de3f-4266-973c-20049231b248.s3.eu-west-1.amazonaws.com/a8f23f8d-3b7a-4de3-a582-a62916b4675d?pitch-bytes=51207&pitch-content-type=image%2Fpng", :block-type :image, :image-scale-x 1.162436548223351, :locked-aspect-ratio? false, :created-at 1702934649355}} [#uuid "f9a12520-21c3-4f76-b118-1fa700d92817"]]}


GAN is a model in which two neural networks, the generator and the discriminator, cooperate to generate and distinguish data through adversarial learning. I first learned by generating noise, allowing the generator to create a fake image, and then by allowing the discriminator to distinguish it.
The main parameters are as follows. Epoch is 34,100, and for batch size and optimizer, the values with the lowest FID were selected experimentally.
In the initial 5,000 epoch and below, the discriminator learned faster than the constructor to distinguish the fake data well, but after that, the constructor and discriminator loss values began to become out of balance and stopped learning before those values were out of balance.
