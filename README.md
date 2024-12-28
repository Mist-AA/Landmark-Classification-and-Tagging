# Landmark Classification & Tagging for Social Media
## Overview
This GitHub repository contains the implementation of a landmark classification and tagging system for social media images. The project is divided into three major steps, each implemented in a corresponding Jupyter Notebook:

1. **CNN from Scratch (cnn_from_scratch.ipynb)**
2. **Transfer Learning (transfer_learning.ipynb)**
3. **App Development (app.ipynb)**
   
## Step 1: CNN from Scratch
### Data Preprocessing (data.py)
The get_data_loaders function in src/data.py processes the dataset for training. It includes data transformations such as resizing, cropping, and normalization. Data augmentation is applied during training to enhance model generalization. The visualize_one_batch function displays a batch of images with their labels for visual inspection.

### Model Architecture (model.py)
The CNN architecture is implemented in the MyModel class in src/model.py. The architecture is designed for landmark classification, with the number of output classes controlled by the num_classes parameter. Dropout, if used, is controlled by the dropout parameter. The architecture does not apply softmax in the forward method.

### Loss and Optimizer (optimization.py)
The loss function (CrossEntropy) and optimizers (SGD and Adam) are defined in src/optimization.py. The functions take model parameters, learning rates, momentum, and weight decay as input.

### Training the Model (train.py)
The training loop is implemented in src/train.py. The train_one_epoch, valid_one_epoch, and optimize functions handle training, validation, and optimization steps, respectively.

### Testing the Model
The model is tested against the test set, achieving a test accuracy of about 50%. TorchScript is then used to export the model for deployment.

### Export Using TorchScript (predictor.py)
The src/predictor.py file handles the export of the trained model using TorchScript. The forward method applies defined transforms and returns model predictions using the exported model.

## Step 2: Transfer Learning
### Transfer Learning Architecture (transfer.py)
Transfer learning is implemented in src/transfer.py. All parameters of the loaded architecture are frozen, and a linear layer is added for classification based on the specified number of classes.

### Training and Testing
The transfer learning model is trained with reasonable hyperparameters, achieving a test accuracy of about 71%. The model is exported using TorchScript for deployment.

## Step 3: App Development
### App Implementation (app.ipynb)
The app.ipynb notebook contains the development of a simple app using one of the exported TorchScript models. The chosen model is loaded using torch.jit.load, and the app displays predictions for an image not in the training or test set.

## Conclusion
This project showcases the end-to-end process of building a landmark classification system, from data preprocessing to model training and deployment in an app.
