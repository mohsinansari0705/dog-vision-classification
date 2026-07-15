# How to get the data

This notebook uses two sets of images:

1. The main Stanford Dogs dataset for training and evaluation.
2. A small custom photo zip for the final prediction demo.

## 1. Get the Stanford Dogs dataset

The notebook downloads the original Stanford Dogs archives directly from:

- http://vision.stanford.edu/aditya86/ImageNetDogs/images.tar
- http://vision.stanford.edu/aditya86/ImageNetDogs/annotation.tar
- http://vision.stanford.edu/aditya86/ImageNetDogs/lists.tar

If you are using Google Colab, the notebook expects you to mount Google Drive first and save the files in:

- /content/drive/MyDrive/Dog Vision/dog_vision_data

The notebook then checks whether these files already exist on Drive:

- images.tar
- annotation.tar
- lists.tar

If they are already there, it copies them into the Colab session.
If not, it downloads them with `wget` and then copies them to Drive so you do not need to download them again later.

## 2. Extract the archives

After the `.tar` files are available in `dog_vision_data/`, the notebook unpacks them with:

```bash
tar -xf dog_vision_data/images.tar
tar -xf dog_vision_data/annotation.tar
tar -xf dog_vision_data/lists.tar
```

Once extracted, you should see these files and folders:

- `Images/` - the dog images.
- `Annotation/` - the image annotations.
- `file_list.mat` - the full list of image files.
- `train_list.mat` - the training split.
- `test_list.mat` - the test split.

The notebook loads the `.mat` files directly with `scipy.io.loadmat(...)`,
so keep them in the same working directory as the notebook after extraction.

## 3. Get the custom dog photos

For the final prediction example, the notebook downloads a small zip of custom images from GitHub:

- https://github.com/mohsinansari0705/dog-vision-classification/raw/main/images/dog-photos.zip

The notebook uses:

```bash
wget -nc https://github.com/mohsinansari0705/dog-vision-classification/raw/main/images/dog-photos.zip
unzip dog-photos.zip
```

That gives you the custom dog photos used for inference at the end of the notebook.

## If you are running locally

The notebook’s download cell is written for Google Colab, but the same files work locally too.
If you are not using Colab, just download the archives into a local folder, extract them there,
and make sure the notebook can find the `.mat` files and `Images/` folder from its current working directory.
