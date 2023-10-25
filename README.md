# Road-Segmentation
This project implements a UNET with a backbone of VGG19 to perform image segmentation on images of roads, this project used the Road segmentation dataset from kaggle.

### Description
<pre>
  1. This project utilizes a UNET model with a backbone of VGG19 used as encoder.
  2. Using VGG19 significatly outperforms traditional UNET architecture with much more genralised mask being produced.
  3. The project can be utilized for enhancing computer vision algorithms involved in road surveillance, navigation,
     and intelligent transportation systemsand and in autonomous driving systems.
</pre>

### Dataset
<pre>
  1. The dataset was obtained from kaggle.
  2. Link : <href>https://www.kaggle.com/datasets/trainingdatapro/roads-segmentation-dataset/data </href>
  3. This dataset comprises a collection of images captured through DVRs (Digital Video Recorders) showcasing roads. 
     Each image is accompanied by segmentation masks demarcating different entities (road surface, cars, road signs, marking and background) within the scene.
</pre>

### Model Details
<pre>
  1. VGG19 backbone
  2. Model Summary : 
  Model: "model"
__________________________________________________________________________________________________
 Layer (type)                Output Shape                 Param #   Connected to                  
==================================================================================================
 input_1 (InputLayer)        [(None, 512, 512, 3)]        0         []                            
                                                                                                  
 model (Functional)          [(None, 256, 256, 128),      1294496   ['input_1[0][0]']             
                              (None, 256, 256, 128),      0                                       
                              (None, 128, 128, 256),                                              
                              (None, 128, 128, 256),                                              
                              (None, 64, 64, 512),                                                
                              (None, 64, 64, 512),                                                
                              (None, 32, 32, 512)]                                                
                                                                                                  
 sequential (Sequential)     (None, 32, 32, 512)          2361344   ['model[0][6]']               
                                                                                                  
 sequential_1 (Sequential)   (None, 64, 64, 512)          2361344   ['sequential[0][0]']          
                                                                                                  
 concatenate_1 (Concatenate  (None, 64, 64, 1024)         0         ['sequential_1[0][0]',        
 )                                                                   'model[0][4]']               
                                                                                                  
 sequential_2 (Sequential)   (None, 64, 64, 256)          2360320   ['concatenate_1[0][0]']       
                                                                                                  
 sequential_3 (Sequential)   (None, 128, 128, 256)        590848    ['sequential_2[0][0]']        
                                                                                                  
 concatenate_2 (Concatenate  (None, 128, 128, 512)        0         ['sequential_3[0][0]',        
 )                                                                   'model[0][2]']               
                                                                                                  
 sequential_4 (Sequential)   (None, 128, 128, 128)        590336    ['concatenate_2[0][0]']       
                                                                                                  
 sequential_5 (Sequential)   (None, 256, 256, 128)        147968    ['sequential_4[0][0]']        
                                                                                                  
 concatenate_3 (Concatenate  (None, 256, 256, 256)        0         ['sequential_5[0][0]',        
 )                                                                   'model[0][0]']               
                                                                                                  
 conv2d_transpose (Conv2DTr  (None, 512, 512, 1)          2305      ['concatenate_3[0][0]']       
 anspose)                                                                                         
                                                                                                  
==================================================================================================
Total params: 21359425 (81.48 MB)
Trainable params: 8410881 (32.08 MB)
Non-trainable params: 12948544 (49.39 MB)
__________________________________________________________________________________________________
</pre>
![model](https://github.com/sway-am/Road-Segmentation/assets/118014263/446c57d2-bc60-4106-a4d0-d79b384a6c67)


### Sample Data

![Sample inputs](https://github.com/sway-am/Road-Segmentation/assets/118014263/4018879a-e3f1-4086-aee5-98d57c0a7d23)

### Model during Training
##### After 50 epoch

![50_epoch](https://github.com/sway-am/Road-Segmentation/assets/118014263/35ed3dd5-0856-4f3c-a2e6-958d8249c4bb)

#### After 200 epoch

![200_epoch](https://github.com/sway-am/Road-Segmentation/assets/118014263/8b8227da-3451-4c6a-8831-7ed51c056687)


### Sample Predictions
![output](https://github.com/sway-am/Road-Segmentation/assets/118014263/6c760687-0fa5-4d94-9005-395e8d991626)

### Comparision with UNET
#### Traditional UNET images (obtained from kaggle)
![UNET](https://github.com/sway-am/Road-Segmentation/assets/118014263/23e92a2f-8b95-49c9-9eb4-fafe413d09f1)

#### Output of VGG19 backbone UNET
![VGG19_UNET](https://github.com/sway-am/Road-Segmentation/assets/118014263/6da1a8ca-e6da-4d5e-a5c3-f882e8450134)


### Languge & Technologies
<pre>
  Language      : Python v3.10.6
  Libraries     : Tensorflow, keras, pandas, numpy, os, matplotlib
  IDE \ editor  : Google Collabatory
  Related       : Computer Vision, Image segmentation, autonomous vehicle, image processing, machine learning.
</pre>

### Dates and Version
<pre>
  Version : v1.0.0
  Date    : 25-10-23
</pre>





