# Setup instructions

First, read https://github.com/cubiq/ComfyUI_IPAdapter_plus.

Then use comfyui manager, to install all the missing models and nodes, i.e. the Clip VIT H from ipadapter, the sdxl vit h ipadapter model, the big sdxl models...

Interesting parameters to adjust: 
* IPAdapter weight: Makes the face / style copy from the top image stronger
* Unclip conditioning strength: The 2nd image is encoded into a CLIP prompt, but you can use additional text to modify the images, i.e. make them smile.
* The KSampler Adv. (Efficient) has:
  * a "start at step" parameter, the later you start the closer the image is to the latent background image.
  * an amount of steps depends on your model. SDXL turbo works fine with 1, the others require 10-20
  * the cfg-scale, i.e. how "strong" your model should be. Too high and you get "deep fried" / "burnt" images with too high contrast. turbo works fine with 1, the others work best with 2-3.
* On top there are disabled XY plot nodes, so you can run multiple parameters in one batch

To run the whole grid, press the "queue full grid" button. The node emits outputs from 1-N, but the index of load image batch expects 0-N, so you have to insert a dummy 0th image.
