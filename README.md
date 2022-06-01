# HopeNet
This is my HopeNet implement.  
## Predictions
First I will show you some predicted results:  

<img src="https://github.com/Younai2021/HopeNet/blob/main/demo/image00082.jpg" width="200"  /> <img src="https://github.com/Younai2021/HopeNet/blob/main/demo/image00202.jpg" width="200"  />
<img src="https://github.com/Younai2021/HopeNet/blob/main/demo/image00514.jpg" width="200"  />
## Preparations
1, You should create a directory named `datasets` to store the training and test data. (Here I use 300W_LP for training and AFLW2000 for testing)   
__Note that__ you need to have a `files.txt` file to store the filenames in the datasets which are not provided by the datasets originally. Use the `create_filename_list.py` to do this.  
2, You should create a directory named `outputs` with two subdirectories `images` for storing the predicted iamges and `sanpshots` for archives.
## Training
I used 300W_LP for training and I trained 1 epoch. However, there was some problems with the model. It predicts a constant result on all the inputs on test time. Therefore, I finally use a model weights that offered by the offical hopnet repository named `hopenet_robust_alpha1.pkl`. You can download this file on the official hopenet repository.

## Testing
I used AFLW2000 for testing. Some results are showed at the beginning.  
The metrics of the model is showed as follows:  
Direction | Yaw | Pitch | Roll
---- | -----  | ----- | -----
MAE Loss | 9.1709 | 7.0361 | 5.7762


## Comparisons
Model | Yaw | Pitch | Roll | MAE 
----|---- | -----  | ----- | -----
HopeNet | 9.17 | 7.04 | 5.78 | 7.33
FSA-Net* | 4.85 | 6.27 | 4.96 | 5.36
img2pose† | 3.43 | 5.03 | 3.28 | 3.91 
img2pose* | 6.70 | 17.17 | 15.15 | 13.00
Dlib† (68 points) | 18.273 | 12.604 | 8.998 | 13.292
QuatNet†† | 3.973 | 5.615 | 3.920 | 4.503
HPE†† | 4.870 | 6.180 | 4.800 | 5.280
TriNet†† | 4.198 | 5.767 | 4.042 | 4.669
6DRepNet | 3.67 | 4.87 | 3.37 | 3.97

All models are trained on 300W-LP and tested on AFLW2000.  
*FSA-Net is implemented on pytorch, note that the official version is implemented on tensorflow.  
*img2pose implementation uses parameters of mean and std on part of the database because the original database brings overflow of memory.  
Dlib is implemented on `C++`. The result is reported by others.  
Methods marked with † are reported by others.  
Methods marked with †† are __not open source__.

## Notes
Most of the codes are from the offical hopenet repository.  
Thanks. ^_^
