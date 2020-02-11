# edge-informed-sisr

Edge-Informed Single Image Super-Resolution, ICCV 2019

# Documentation

## Preparation

First run ```pip install -r requirements.txt``` if you have not done so

   If you get an error on Windows installing torch, go to https://pytorch.org/ , select what version you want and run the command they suggest

## Modes

- Mode 1 (train): mode is used for training
- Mode 2 (test): mode used to upscale images. Does not provide any results other than upscaled images. That's why in config file it does not require HR variable
- Mode 3 (eval): mode used to evaluate model performance. For this mode you need to have low resolution and high resolution images

## How to upscale image (mode 2)

1. Run test.py with "```python test.py --path PATH_TO_YOUR_MODEL_AND_CONFIG --input PATH_TO_IMAGE_FOLDER --output PATH_TO_OUTPUT_FOLDER --model 1_OR_2_OR_3```"

    **Parameters explained**:

   ```--path``` path to the folder where config file and model files are located

   ```--input``` path to folder where images are located OR path to file with the list of images OR path to single image

   ```--output``` where to store results of upscaling

   ```--model``` 1: edge model, 2: SR model, 3: joint SR model with edge enhancer

## How to train model

1. Create folder for your model
2. Copy ```config.yml.example``` to that folder
3. Rename ```config.yml.example``` to ```config.yml```
4. Config parameters in config file. Set ```TRAIN_FLIST_LR``` to folder with low resolution images, ```TRAIN_FLIST_HR``` to folder with high resolution images (can be file with list of images in both cases)
5. Set validation set variables in the same way
6. Run ```python main.py --path PATH_TO_YOUR_MODEL --model 1_OR_2_OR_3```

     Check testing section for details of arguments