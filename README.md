import os
import cv2
import scipy
import scipy 
from scipy.stats import skew
from scipy.stats import kurtos
import numpy as np
images=[]
label=[]
folder='location of file'
for i in os.listdir(folder):
  filename=folder+'/'+i
  for j in os.listdir(filename):
    filename2=filename+'/'+j
    images.append(filename2)
    label.append(i)
    img=cv2.imread(filename2)
    img=cv2.resize(img,(224,224))
    img1=cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
    mean=img1.mean()
    variance=img1.var()
    std_deviation=img1.var()
    skew_value=skew(img1,axis=0,bias=True)
    kurtosis_value=kurtosis(img1,axis=0,bias=True)
    statistcal_feature=np.hstack((mean,variance,std_deviation,skew_value,kurtosis_value))

    pass
