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
I used 300W_LP for training and I trained 1 epoch. However, there was some problems with the model. It predicts a constant result on all the inputs on test time. Therefore, I finally use a model weights that offered by the offical hopnet repository named `hopenet_robust_alpha1.pkl`. You can download this file on the offical hopenet repository.

## Testing
I used AFLW2000 for testing. Some results are showed at the beginning.  
The metrics of the model is showed as follows:  
Direction | Yaw | Pitch | Roll
---- | -----  | ----- | -----
MAE Loss | 9.1709 | 7.0361 | 5.7762

## Notes
Most of the codes are from the offical hopenet repository.  
Thanks. ^_^


Model | Yaw | Pitch | Roll | MAE 
----|---- | -----  | ----- | -----
HopeNet | 9.17 | 7.04 | 5.78 | 7.33
FSA-Net | 4.85 | 6.27 | 4.96 | 5.36
6DRepNet | __3.67__ | __4.87__ | __3.37__ | __3.97__

*All models are trained on 300W-LP and tested on AFLW2000.
