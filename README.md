# RepSE-CBAMNet
This is the source code for the paper titled "[RepSE-CBAMNet: A Hybrid Attention-Enhanced CNN for Brain Tumor Detection
RGELAN]([https://ieee-dataport.org/documents/brain-tumor-mri-dataset](https://ebooks.iospress.nl/doi/10.3233/SHTI250401))" Repository

## Instructions
After downloading the repository from GitHub:
1. Rename the folder to RGELAN (if it's not already named like that).
2. Upload it to your Google Drive (MyDrive).

Download the Br35H and figshare datasets from [IEEEDataPort](https://ieee-dataport.org/documents/brain-tumor-mri-dataset). From now on Br35H will be refered to as the First Dataset and figshare as the Second Datase.

Copy the all four coco.yalm (*coco.yaml*, *coco1.yaml*, *coco2.yaml* and *coco3.yaml*) files from */content/drive/MyDrive/RGELAN/data* and past them at your *MyDrive*.

## For the First Dataset
Download the dataset from the provided link.

### Dataset Preparation
Unzip the downloaded file.

After unzipping the files, ensure that the final folder architecture is as below. You can either rename the folders after unzipping the data or
create a folder architecture as below and copy the files to it.

```plaintext
brain/
├── TRAIN/
│   ├── images/
│   └── labels/
├── VAL/
│   ├── images/
│   └── labels/
```
If you are executing this code in colab, ensure that the *brain* folder is placed in mydrive. For our model we used 500 images for training and 201 images 
for validation.

## For the Second Dataset
Download the dataset from the provided link.

### Dataset Preparation
Unzip the downloaded file.
Delete the following files: *cvind.mat* and *README.txt*.
Unzip all remaining files in the folder. If they were unzipped inside subfolders, move the files out and delete those subfolders.
After unzipping everything, delete the zip files as well.
Rename the folder to Figshare_dataset.
The final folder architecture should be:
```
Figshare_dataset/
├── 1.mat
├── 2.mat
.
.
.
└── 3064.mat
```

Upload the *Figshare_dataset* folder to your Google Drive (MyDrive).

### Converting the Dataset to Images and Labels
Open the *RepSE-CBAMNet_Dat2.ipynb* file in Google Colab.
Run the entire "Necessary stuff" section (this is required).
Navigate to the "Second Brain Tumor Datasett" section and execute the following:
**converting image figshare dataset**
**connecting to google drive**
**create separate dataset based on label**
The dataset will be saved in *MyDrive/Figshare_dataset/brain* and will be ready for use.

### Organizing Training and Validation Sets
Follow these steps:
1. In MyDrive, create a folder named Folds2.
2. Inside *Folds2*, create 5 subfolders: *fold_1*, *fold_2*, *fold_3*, *fold_4*, and *fold_5*.
3. Inside each *fold_@* folder, create two more subfolders: *labels* and *images*.
4. Evenly distribute all image files across the *images* folders and all text files across the *labels* folders (613 in each).
Additionally:
Inside the *Folds2* folder, create 5 subfolders named *train1*, *train2*, *train3*, *train4*, and *train5*. Each of these should contain empty *images* and *labels* subfolders.
The final folder architecture should look like this:
```
MyDrive/
└── Folds2/
    ├── fold_1/
    │   ├── images/ (613 image files)
    │   └── labels/ (613 label files)
    ├── fold_2/
    │   ├── images/
    │   └── labels/
    ├── fold_3/
    │   ├── images/
    │   └── labels/
    ├── fold_4/
    │   ├── images/
    │   └── labels/
    ├── fold_5/
    │   ├── images/
    │   └── labels/
    ├── train1/
    │   ├── images/ (empty)
    │   └── labels/ (empty)
    ├── train2/
    │   ├── images/ (empty)
    │   └── labels/ (empty)
    ├── train3/
    │   ├── images/ (empty)
    │   └── labels/ (empty)
    ├── train4/
    │   ├── images/ (empty)
    │   └── labels/ (empty)
    └── train5/
        ├── images/ (empty)
        └── labels/ (empty)
```
   
In MyDrive, create a folder named *brain22*.
Inside *brain22*, create two subfolders: *TRAIN* and *VAL*.
Distribute the dataset as follows:
1. Place 2,184 images and their corresponding labels in the *TRAIN* subfolder.
2. Place the remaining 879 images and their corresponding labels in the *VAL* subfolder.
The final folder structure should be:
```
MyDrive/
└── brain2/
    ├── TRAIN/ 
    │   └── (2,184 image and 2,184 label files)
    └── VAL/
        └── (879 image and 879 label files)
```
## For the Third Dataset
Download the dataset from the [Ultralytics]([https://ieee-dataport.org/documents/brain-tumor-mri-dataset](https://github.com/ultralytics/ultralytics/blob/main/ultralytics/cfg/datasets/brain-tumor.yaml))..
Unzip the downloaded file.
Rename the folder to brain-tumor if it is not already named that.
The folder should look like this:
```plaintext
brain-tumor/
├── train/
│   ├── images/
│   │   └── (893 image files)
│   └── labels/
│   │   └── (893 label files)
├── valid/
│   ├── images/
│   │   └── (223 image files)
│   └── labels/
│   │   └── (223 label files)
```
Upload that in MyDrive.

### RCS-YOLO Preparation
For the first dataset, results for both RCS-YOLO and RepVGG-GELAN were already available, so no further processing was needed. However, for this dataset, new results needed to be generated.
To utilize RCS-YOLO, we used Ming Kang's repository, which can be accessed from [RCS-YOLO](https://github.com/mkang315/RCS-YOLO). After downloading the repository, rename the folder to RCS-YOLO (if it is not already named as such) and upload it to your Google Drive (MyDrive).
Next, navigate to the directory */content/drive/MyDrive/RCS-YOLO/data*, and place the *coco22.yaml* and *coco33.yaml* files from our repository in this location.

### Running the rest of the Code
The **Finding optimal number of anchors** section generates a modified version of the *ne-rcs-gelan-c-v39.yaml* file, incorporating our proposed architecture with the optimal configuration and number of anchors. (do not run this, we already did)
The subsequent sections **Yolov9c**, **RepVGG-GELAN**, **RCS-YOLO**, and **RepSE-CBAMNet** when executed, produce results for their respective architectures.


