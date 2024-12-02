# Psychological Classification of Children Drawings 

## Overview
This project leverages deep learning to classify children's psychological health based on their drawings. Using pretrained models such as **EfficientNetB0, EfficientNetB1, MobileNetV2, ResNet50, and YOLOv8n-cls**, the model was trained and evaluated to determine the best approach for real-time classification. The top-performing model, **YOLOv8n-cls**, is designed to be deployed in web or mobile applications to help parents monitor and analyze their children's drawings, potentially helping identify signs of psychological stress or well-being.

## Acknowledgment
This work was heavily inspired by and based on the findings of the paper:  
**"A Children's Psychological and Mental Health Detection Model by Drawing Analysis based on Computer Vision and Deep Learning"**  
**Amal Alshahrani, Manar Mohammed Almatrafi, Jenan Ibrahim Mustafa, Layan Saad Albaqami, Raneem Abdulrahman Aljabri**  
Available at: [here](https://etasr.com/index.php/ETASR/article/view/7812)  

This research provided valuable insights into the use of **YOLOv8n-cls**, which achieved a top-1 accuracy of 94% at epoch 10 with a smaller model size, making it highly efficient for mobile applications. Inspired by their findings, I retrained their dataset to reach comparable results, achieving a top-1 accuracy of **95.99% at epoch 10**.

## Dataset Information
The dataset used for training and evaluation was collected from children aged **6 to 15 in Mecca**. It consists of **500** images, split as follows:
- **Training set**: 80% of the images
- **Validation set**: 10%
- **Test set**: 10%

The dataset is labeled into four categories:
- **Anger and aggression**
- **Anxiety**
- **Happy**
- **Sad**

You can access the dataset [here](https://universe.roboflow.com/anamel/anamelclassification/dataset/1).

## Data Preparation
 The dataset preparation process involves organizing raw data into class-specific folders, making it ready for training. This step is automated using the [prepare-dataset.ipynb](./prepare-dataset.ipynb) notebook in the repository.  

## Results
The evaluation of the pretrained models showed the following results:
![Screenshot 2024-12-01 170424](https://github.com/user-attachments/assets/8a60b359-8460-4d36-a7df-6cfb9eb12eab)

**Note**: YOLOv8n-cls achieved the highest performance and was selected as the best model for real-time analysis.

## Future Work
The next step involves integrating the trained model into a web or mobile application, enabling parents to access real-time analysis of their children's drawings and store them for ongoing monitoring.
