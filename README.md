# DeepCorrect: *Correcting DNN models against Image Distortions*
Created by Tejas Borkar and Lina Karam at Arizona State University ECEE.

## Introduction
In recent years, the widespread use of deep neural networks (DNNs) has facilitated great improvements in performance for computer vision tasks like image classification and object recognition. In most realistic computer vision applications, an input image undergoes some form of image distortion such as blur and additive noise during image acquisition or transmission. Deep networks trained on pristine images perform poorly when tested on such distortions. *DeepCorrect* improves the robustness of pre-trained DNN models by training small stacks of convolutional layers with *residual* connections at the output of the most distortion susceptible convolutional filters in a DNN, to correct their filter activations, whilst leaving the rest of the pre-trained DNN filter outputs unchanged. Performance results show that applying *DeepCorrect* models for common vision tasks like image classification (CIFAR-100, ImageNet), object recognition (Caltech-101, Caltech-256) and scene classification (SUN-397), significantly improves the robustness of DNNs against distorted images and outperforms the alternative approach of network fine-tuning.

A complete description of *DeepCorrect* can be found in our journal paper [IEEE Transactions on Image Processing](https://ieeexplore.ieee.org/document/8746775) or in a pre-print on [ArXiv](https://arxiv.org/abs/1705.02406). 


   **2-dimensional t-SNE embedding of baseline AlexNet DNN features for ImageNet object classes :**
   

   ![baseline AlexNet](https://github.com/tsborkar/DeepCorrect/blob/master/eps_fig/Fig3_1.png)




   **2-dimensional t-SNE embedding of DeepCorrect features for ImageNet object classes :**


  ![baseline AlexNet](https://github.com/tsborkar/DeepCorrect/blob/master/eps_fig/Fig15_1.png)


   **Deep neural network architectures :**
   
   Convolution layers in the *DeepCorrect* models, shown in gray with dashed outlines, are nontrainable layers and their weights are kept the same as those of the baseline models trained on undistorted images. 
  


  ![model_arch](https://github.com/tsborkar/DeepCorrect/blob/master/eps_fig/model_fig.png)



## Citing *DeepCorrect*
If you use *DeepCorrect* in your research, please consider citing:

```
@article{BorkarK17,
  author    = {Tejas S. Borkar and Lina J. Karam},
  title     = {DeepCorrect: Correcting {DNN} models against Image Distortions},
  journal   = {CoRR},
  volume    = {abs/1705.02406},
  year      = {2017},
  url       = {http://arxiv.org/abs/1705.02406},
  archivePrefix = {arXiv},
  eprint    = {1705.02406},
}

```
## License
*DeepCorrect* is released under the MIT License (refer to the LICENSE file for details).

## *DeepCorrect* performance results

#### Top-1 accuracy for undistorted images

|   Model        |  ImageNet (2012) |    SUN-397  |   Caltech-101  |  Caltech-256   |  CIFAR-100  |
| :-----------:  | :--------------: | :---------: |   :----------: |   :---------:  | :---------: |
|  Baseline      |    0.5694        |   0.3100    |     0.8500     |    0.6200      |   0.7028    |


#### Top-1 accuracy for Gaussian blur affected images, averaged over all levels of distortion


|   Model        |  ImageNet (2012) |    SUN-397  |   Caltech-101  |  Caltech-256   |  CIFAR-100  |
| :-----------:  | :--------------: | :---------: |   :----------: |   :---------:  | :---------: |
|  Baseline      |    0.2305        |   0.1393    |     0.4980     |    0.2971      |   0.2502    |
|  Finetuning    |    0.4596        |   0.2369    |     0.7710     |    0.5167      |   0.5727    |
| *DeepCorrect*  |   **0.5071**     | **0.3049**  |   **0.8371**   |   **0.5883**   | **0.6023**  |


#### Top-1 accuracy for AWGN affected images, averaged over all levels of distortion

|   Model        |  ImageNet (2012) |    SUN-397  |   Caltech-101  |  Caltech-256   |  CIFAR-100  |
| :-----------:  | :--------------: | :---------: |   :----------: |   :---------:  | :---------: |
|  Baseline      |    0.2375        |   0.0859    |     0.3423     |    0.1756      |   0.3147    |
|  Finetuning    |    0.4894        |   0.1617    |     0.7705     |    0.4995      |   0.6451    |
| *DeepCorrect*  |   **0.5092**     | **0.2936**  |   **0.8034**   |   **0.5482**   | **0.6452**  |

#### Trainable parameters 

|   Model        |  ImageNet (2012) |  CIFAR-100  |
| :-----------:  | :--------------: | :---------: |
|  Finetuning    |    60.94 M       |   1.38 M    |
| *DeepCorrect*  |      2.81 M      |     0.89 M  |


#### Accelerating training

   ImageNet validation set accuracy vs. training iterations


  ![train_time](https://github.com/tsborkar/DeepCorrect/blob/master/eps_fig/training_times.png)
  
#### Qualitative evaluation for ImageNet images

   SSIM vs. Filter index


  ![ssim](https://github.com/tsborkar/DeepCorrect/blob/master/eps_fig/ssim-crop.png)
  
   PSNR vs. Filter index

  ![psnr](https://github.com/tsborkar/DeepCorrect/blob/master/eps_fig/psnr-crop.png)


A complete description of the results and the corresponding experimental setup can be found
in the [arXiv tech report](https://arxiv.org/abs/1705.02406).





