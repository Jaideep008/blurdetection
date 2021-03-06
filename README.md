# Blur Detection
Blur Detection works using the total variance of the laplacian of an
image, this provides a quick and accurate method for scoring how blurry
an image is.

This package only depends on numpy and opencv, to install them run, 

```
pip install -U -r requirements.txt
```

The repository has a script, `jai.py` which lets us run on single images or directories of images. The blur detection method is highly dependent on the size of the image being processed. To get consistent scores we fix the image size to HD, to disable this use  `--variable-size`. The script has options to, 

```bash
# run on a single image
python jai.py -i input_image.png

# run on a directory of images
python jai.py -i input_directory/ 

# or both! 
python jai.py -i input_directory/ other_directory/ input_image.png
```

. In addition to logging whether an image is blurry or not, we can also,

```bash
# save this information to json
python jai.py -i input_directory/ -s results.json

# display blur-map image
python jai.py -i input_directory/ -d
```
In addition to it, we can even segregate  the blur image in another folder by using a parameter `-save` and give the path for the the blur images to  get saved.
syntax:
`python jai.py -i [image_path] -save [folder_path]`

The saved json file has information on how blurry an image is, the higher the value, the less blurry the image.

```json
{
    "images": ["/Users/demo_user/Pictures/Flat/"],
    "fix_size": true,
    "results": [
        {
            "blurry": false,
            "input_path": "/Users/demo_user/Pictures/Flat/IMG_1666.JPG",
            "score": 6984.8082115095549
        },
    ],
    "threshold": 100.0
}
```

This is based upon the blogpost [Blur Detection With Opencv](https://www.pyimagesearch.com/2015/09/07/blur-detection-with-opencv/) by Adrian Rosebrock.

![Blur Mask Demo](https://raw.githubusercontent.com/WillBrennan/BlurDetection2/master/docs/demo.png)
