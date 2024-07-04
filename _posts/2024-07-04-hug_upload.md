---
title: 'Upload dataset to Hugging Face'
date: 2024-07-04
permalink: /posts/upload_dataset_huggingface/
tags:
  - Hugging Face
  - Dataset
  - Deep Learning

---

# Upload dataset to Hugging Face

## Register on Hugging Face
Create a account on Hugging Face and login to your account.
[https://huggingface.co/](https://huggingface.co/)

## Requirements
```bash
# create a virtual environment using conda or venv
conda create -n upload_data python=3.9
conda activate upload_data

# install required packages
conda install datasets transformers
```

## Get the token
Go to your profile and apply for a token in the `Access Tokens` section.  
Choose the `Write` option and copy the token. see the different options [here](https://huggingface.co/docs/hub/security-tokens)  

## Login to Hugging Face in your terminal
```bash
huggingface-cli login

# paste the token
```

## Upload the dataset
Here is an example of uploading a dataset to Hugging Face.  
In this example, I will upload the cat dot image dataset. The dataset contains 25000 images of cats and dogs. And it also has a csv file that contains the labels of the images.  

labes.txt:
```txt
cat.0.jpg;0
cat.1.jpg;0
cat.10.jpg;0
cat.100.jpg;0
cat.1000.jpg;0
cat.10000.jpg;0
cat.10001.jpg;0
cat.10002.jpg;0
...
```
The first column is the image name and the second column is the label.  0 for cat and 1 for dog. 

```python
import os
import pandas as pd
from datasets import Dataset, DatasetDict
from PIL import Image

# set your dataset path
img_dir = 'dataset/images'
label_file = 'dataset/labels.txt'

# read the labels
labels_df = pd.read_csv(label_file, sep=';', header=None, names=['image', 'label'])

# read the images
def load_image(sample):
    image_path = os.path.join(img_dir, sample['image'])
    with Image.open(image_path).convert('RGB') as img:
        img_byte_arr = io.BytesIO()
        img.save(img_byte_arr, format='JPEG') # convert the image to byte array
        img_byte_arr = img_byte_arr.getvalue()  # get the byte array
    sample['image'] = img_byte_arr
    return sample

# create Hugging face dataset
dataset = Dataset.from_pandas(labels_df)
dataset = dataset.map(load_image, num_proc=4)

# split the dataset
train_test_split = dataset.train_test_split(test_size=0.2)

dataset_dict = DatasetDict({
    'train': train_test_split['train'],
    'test': train_test_split['test']
})

# push the dataset to the hugging face
# Hugging Face will create a new dataset with the name `username/dataset_name`
dataset_dict.push_to_hub("username/dataset_name")
```


Run the above code in your terminal.  
If it is successful, you will see the dataset in your Hugging Face.

## Use the dataset
You can use the dataset in your code like this:
```python
from datasets import load_dataset

# load the dataset
# The dataset will be downloaded from the Hugging Face
dataset = load_dataset("username/dataset_name", split="train")

# get the first sample
byte = dataset['train']['image'][0]
image = Image.open(io.BytesIO(byte))
plt.imshow(image)
```
#### Also you can write a dataloader for the dataset