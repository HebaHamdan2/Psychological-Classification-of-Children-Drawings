# Psychological Classification of Children Drawings With Deep Learning
## Overview
This project leverages deep learning to classify children's psychological health based on their drawings. Using pretrained models such as **EfficientNetB0, EfficientNetB1, MobileNetV2, ResNet50, and YOLOv8n-cls**, the model was trained and evaluated to determine the best approach for real-time classification. The top-performing model, YOLOv8n-cls, is designed to be deployed in web or mobile applications to help parents monitor and analyze their children's drawings, potentially helping identify signs of psychological stress or well-being.

## Dataset Information
The dataset used for training and evaluation was collected from children aged 6 to 15 in Mecca. It consists of 500 images, split as follows:
- **Training set**: 80% of the images
- **Validation set**: 10%
- **Test set**: 10%

The dataset is labeled into four categories:
- **Anger and aggression**
- **Anxiety**
- **Happy**
- **Sad**

You can access the dataset [here](https://universe.roboflow.com/anamel/anamelclassification/dataset/1).

### Data Preparation
The `prepare-dataset.ipynb` script processes the raw dataset to organize images into subdirectories for each class. Below is a snippet of the Python code used for this process:

```python
import os
import pandas as pd
import shutil

# Define paths
dataset_path = './anamelClassification.v1i.multiclass'
splits = ['train', 'val', 'test']

# Organize images into class subdirectories
for split in splits:
    csv_file = os.path.join(dataset_path, f"{split}/_classes.csv")
    split_folder = os.path.join(dataset_path, split)
    
    # Read the CSV file
    labels_df = pd.read_csv(csv_file)
    
    # Clean up column names (remove leading/trailing spaces)
    labels_df.columns = labels_df.columns.str.strip()
    
    # Class columns (excluding the filename column)
    class_columns = ['Anger and aggression', 'anxiety', 'happy', 'sad']
    
    for _, row in labels_df.iterrows():
        image_name = row['filename']
        class_label = None
        for class_name in class_columns:
            if row[class_name] == 1:
                class_label = class_name
                break
        
        if class_label is None:
            print(f"Warning: No class label found for {image_name}")
            continue
        
        # Create class subdirectory if it doesn't exist
        class_dir = os.path.join(split_folder, class_label)
        os.makedirs(class_dir, exist_ok=True)
        
        # Move the image to the class subdirectory
        source_path = os.path.join(split_folder, image_name)
        dest_path = os.path.join(class_dir, image_name)
        
        if os.path.exists(source_path):
            shutil.move(source_path, dest_path)
        else:
            print(f"Warning: File {source_path} does not exist.")
