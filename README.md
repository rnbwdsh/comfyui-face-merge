# ComfyUI Workflow for merging faces

Demo video @ [https://github.com/rnbwdsh/comfyui-face-merge](youtube).

## Setup instructions

First, read [https://github.com/cubiq/ComfyUI_IPAdapter_plus](the IP Adapter Plus doc), as well as basic comfyui doc.

Then use comfyui manager, to install all the missing models and nodes, i.e. the Clip VIT H from ipadapter, the sdxl vit h ipadapter model, the big sdxl models, efficient nodes...

## Parameters to adjust: 
* IPAdapter weight: Makes the face / style copy from the top image stronger
* Unclip conditioning strength: The 2nd image is encoded into a CLIP prompt, but you can use additional text to modify the images, i.e. make them smile.
* The KSampler Adv. (Efficient) has:
  * a "start at step" parameter, the later you start the closer the image is to the latent background image.
  * an amount of steps depends on your model. SDXL turbo works fine with 1, the others require 10-20
  * the cfg-scale, i.e. how "strong" your model should be. Too high and you get "deep fried" / "burnt" images with too high contrast. turbo works fine with 1, the others work best with 2-3.
* On top there are disabled XY plot nodes, so you can run multiple parameters in one batch
* For faster runs, reduce amount of steps and the resolution of the latent (therefore output) image. SDXL only performs well on very limited resolutions.

## Usage
To run the whole grid, press the "queue full grid" button. The node emits outputs from 1-N, but the index of load image batch expects 0-N, so you have to insert a dummy 0th image.

Try to pre-crop your images to a square and 1024x1024 with the face close to center for best results.

## Performance

For my 13700k / 2070 super, creating 1024^2 images takes roughly 7 seconds for sdxl turbo (1 step), 13 seconds for sdxl fae (10 steps) and 21 seconds for sdxl base (20 steps).

## Example images

All of the following images are licensed CC0, do whatever you want with them with or without mentioning this repo. 

### SDXL Turbo

![SDXL%20Turbo%2C%20kickl.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Turbo%2C%20kickl.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Turbo%2C%20kickl.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Turbo%2C%20kickl.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Turbo%2C%20kickl.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Turbo%2C%20kickl.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Turbo%2C%20macro_pogo.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Turbo%2C%20macro_pogo.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Turbo%2C%20macro_pogo.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Turbo%2C%20macro_pogo.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Turbo%2C%20macro_pogo.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Turbo%2C%20macro_pogo.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Turbo%2C%20macro_pogo.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Turbo%2C%20macro_pogo.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Turbo%2C%20sebastian-kuraz-frontal.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Turbo%2C%20sebastian-kuraz-frontal.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Turbo%2C%20sebastian-kuraz-frontal.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Turbo%2C%20sebastian-kuraz-frontal.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Turbo%2C%20sebastian-kuraz-frontal.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Turbo%2C%20sebastian-kuraz-frontal.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Turbo%2C%20sebastian-kuraz-frontal.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Turbo%2C%20sebastian-kuraz-frontal.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Turbo%2C%20vdb.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Turbo%2C%20vdb.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Turbo%2C%20vdb.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Turbo%2C%20vdb.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Turbo%2C%20vdb.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Turbo%2C%20vdb.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Turbo%2C%20vdb.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Turbo%2C%20vdb.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Turbo%2C%20kickl.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Turbo%2C%20kickl.jpg%2C%20kickl.jpg_00001_.png)

### SDXL Faetastic

![SDXL%20Faetastic%20v24%2C%20kickl.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20kickl.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20kickl.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20kickl.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20kickl.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20kickl.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20kickl.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20kickl.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20macro_pogo.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20macro_pogo.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20macro_pogo.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20macro_pogo.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20macro_pogo.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20macro_pogo.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20macro_pogo.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20macro_pogo.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20sebastian-kuraz-frontal.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20sebastian-kuraz-frontal.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20sebastian-kuraz-frontal.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20sebastian-kuraz-frontal.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20sebastian-kuraz-frontal.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20sebastian-kuraz-frontal.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20sebastian-kuraz-frontal.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20sebastian-kuraz-frontal.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20vdb.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20vdb.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20vdb.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20vdb.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20vdb.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20vdb.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Faetastic%20v24%2C%20vdb.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Faetastic%20v24%2C%20vdb.jpg%2C%20vdb.jpg_00001_.png)

### SDXL Base

![SDXL%20Base%2C%20kickl.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Base%2C%20kickl.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Base%2C%20kickl.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Base%2C%20kickl.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Base%2C%20kickl.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Base%2C%20kickl.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Base%2C%20kickl.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Base%2C%20kickl.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Base%2C%20macro_pogo.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Base%2C%20macro_pogo.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Base%2C%20macro_pogo.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Base%2C%20macro_pogo.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Base%2C%20macro_pogo.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Base%2C%20macro_pogo.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Base%2C%20macro_pogo.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Base%2C%20macro_pogo.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Base%2C%20sebastian-kuraz-frontal.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Base%2C%20sebastian-kuraz-frontal.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Base%2C%20sebastian-kuraz-frontal.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Base%2C%20sebastian-kuraz-frontal.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Base%2C%20sebastian-kuraz-frontal.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Base%2C%20sebastian-kuraz-frontal.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Base%2C%20sebastian-kuraz-frontal.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Base%2C%20sebastian-kuraz-frontal.jpg%2C%20vdb.jpg_00001_.png)
![SDXL%20Base%2C%20vdb.jpg%2C%20kickl.jpg_00001_.png](SDXL%20Base%2C%20vdb.jpg%2C%20kickl.jpg_00001_.png)
![SDXL%20Base%2C%20vdb.jpg%2C%20macro_pogo.jpg_00001_.png](SDXL%20Base%2C%20vdb.jpg%2C%20macro_pogo.jpg_00001_.png)
![SDXL%20Base%2C%20vdb.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png](SDXL%20Base%2C%20vdb.jpg%2C%20sebastian-kuraz-frontal.jpg_00001_.png)
![SDXL%20Base%2C%20vdb.jpg%2C%20vdb.jpg_00001_.png](SDXL%20Base%2C%20vdb.jpg%2C%20vdb.jpg_00001_.png)
