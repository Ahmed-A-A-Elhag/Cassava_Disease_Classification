# Cassava Disease Classification
## 1. Preprocessing:
- Before training different models, a series of preprocessing methods were used on the data:

a. Training data:
   - Random rotation.
   - Random vertical flipping and Random horizontal flipping
   - Resizing the image with different resolutions .
   - Normalization .

b. Test data:
   - Resizing the image with different resolutions.
   - CenterCrop
   - Normalization .

## 2. Experiments:
A baseline model was used to better understand the problem, after that a collection of pretrained models were used, in all the last linear layer of the model was replaced with a new one with 5 neurons output. The pretrained models used are ResNet18, ResNet50, ResNet101,ResNext50, ResNext101.

## 3. Training:
- The following hyper-parameters were used during training:
  - Learning rate : After trying many  learning rates, a lr of 1e-4 was used with a scheduler.
  - Weight decay : To reduce overfitting, L2 regularization was utilized with λ = 1e −3 and 1e-2 .
  - Optimizer: Adam.
  - Batch size: 16, 32, ...
  - Image scaling: 224, 448, 500.

## 4. Models scores:




|    Model      | Number of epochs | Batch size  |Learing rate   | Weight decay | Scheduler    |Best Train Accuracy  |Best val Accuracy  |At eopch      |
| ------------- | -------------    |------------- |------------- |------------- |------------- |-------------------- |-----------------  |------------- |
| ResNet 18     |       15         |     128      |   1e-3       |     0        |    No        |       85%           |     83.37%        |    14        |
|               |       15         |     128      |   1e-4       |     0        |    No        |       87%           |     85.7%         |    5         |
| ResNet 50     |       15         |     128      |   1e-4       |     0        |    No        |       88%           |     87.09%        |    10        |
|               |       15         |     128      |   1e-5       |     0        |    No        |       87%           |     85%           |    14        |
| ResNet 101    |       15         |      64      |   1e-4       |     0        |CosineAnnealingLR |       91%       |     87.7%         |    10        |
|               |       15         |      64      |   1e-4       |     0.02     |    No            |       88%       |     86.38%        |    10        |
| ResNext 50    |       15         |      32      |   1e-4       |     0.02     |    No            |       87%       |     87.18%        |    5         |
|               |       15         |      32      |   1e-5       |     0.001    |CosineAnnealingLR |       90.20%    |     90.19%        |    7         |
| ResNext 101   |       10         |      16      |   1e-5       |     0        |CosineAnnealingLR |       92%       |     88.20%        |    10        |
|               |       10         |       8      |   1e-4       |     0        |CosineAnnealingLR |       90%       |     88.68%        |    9         |
|               |       10         |       8      |   2e-5       |     0        |CosineAnnealingLR |       91.50%    |     91.30%        |    5         |
