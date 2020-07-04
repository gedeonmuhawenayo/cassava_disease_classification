# Notes

- Try to manually look at dataset and get familiar with diseases  
- Research on Semi-Supervised Learning  
- Check winning notebooks  
- Create a base model/submission pipeline

### Observations
- CBB: Brown spots  
- CBSD: Yellow coloration 
- CMD: Deformed Leaves
- CGM: Many scars on Leaves

###  Approaches
- Transfer Learning/Pretrained model  
- AutoEncoder model  
- Semi-supervised Learning
- Multi-modal learning
- Ensemble  

### Models  
- EfficientNet
- Resnet-50/101
- Resnet-50/101

### Data Augmentation methods
- Centre cropping (with different sizes)
- Rotating
- Rescaling
- Horizontal and vertical Flips
- Grey Scaling
- Lighting augmentation
- Pixel shifting (Yellow and Black spots)

### Dealing with Data Distribution
- Batch Normalization
- Proper Weight Intitalizations

### Training
- Early Stopping or  
- Model Checkpointing
- LR with Restart or Cyclic/Traingular LR
- Clip norm

### How to cater for imbalanced data  
- Deal with it in the loss
- Data augmentation and store the data
- Check other approaches 

### How to deal with multiclass diseases
- Label Smoothening  
- Other approaches  

### Predictions
- Testtime Augmentation
- Multi-stage predictions
- Ensembling

### Other ideas
- Train with greyscale  
- Pixel shifting (Yellow and Black spots)  


### Comments  
- 1st Pos  
"""model: 5 fold se_resnext101
data augumentaion: RandomCrop, VFlip, HFilp, RandomRotate
3 * TTA
cv: I don't remember it too clearly, but it should be over 0.925, LB(public): 0.92384, LB(private): 0.93507"""

- Train on extra images as pseudo labels  
I use some models(such as resnet50, seresnext50 and seresnext101) that can get the best LB on leaderboard to ensemble for extraimgas. And then I did some experiments, and found that the CV could be higher if the samples with a filtering probability greater than 95 were used as training set for training.
config：same as above



- 2nd Pos  
`I used 6fold seresnext 101
lr: 2e-4
batch size: 16
input size: 448x448x3
epochs: 5
augmentations: standard
tta: 8x

cv: ~0.92

By averaging folds, it scored 0.927+ on public lb and 0.935+ on private lb.

My CV improvements did not reflect on LB.
I believe strongly that training data is noisy`



### Advices  
- Do not trust the LB, trust your CV.  
- You can ensemble many many models，but it is not necessarily.  



# Colab's file access feature
from google.colab import drive
drive.mount('/content/gdrive/')

#json_file = '/content/gdrive/My Drive/Colab Notebooks/api_data/kaggle.json'

# Then move kaggle.json into the folder where the API expects to find it.
#!mkdir -p ~/.kaggle/ && cp '/content/gdrive/My Drive/Colab Notebooks/api_data/kaggle.json' ~/.kaggle/ && chmod 600 ~/.kaggle/kaggle.json

#download data, will take 30-60 seconds
#!kaggle competitions download -c cassava-disease -p /content/gdrive/My\ Drive/kaggle/cassava
#unzip all data for usage, will take few minutes

path = "/content/gdrive/My Drive/kaggle/cassava"
!unzip -qq "$path/train.zip"
!unzip -qq "$path/extraimages.zip"
!unzip -qq "$path/test.zip"