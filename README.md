# EVA-Session-14-15A

**Dataset Link:**

**Datasets:**
**Complete Dataset:** <br>

https://drive.google.com/drive/folders/15ZgDJ-4PpYAtNZRkTRlRmXulN6UOoZZq <br>

**Dataset 1_80K: ** <br>

https://drive.google.com/drive/folders/15ZgDJ-4PpYAtNZRkTRlRmXulN6UOoZZq <br>

**Dataset 80K_160K:** <br>
https://drive.google.com/drive/folders/1WAfa6rctCX6lAG_XXgXyBF8uAXlD6cJw <br>

**Dataset 160K_240K:** <br>
https://drive.google.com/drive/folders/1WAfa6rctCX6lAG_XXgXyBF8uAXlD6cJw <br>

**Dataset 240K_320K:** <br>
https://drive.google.com/drive/folders/15ZgDJ-4PpYAtNZRkTRlRmXulN6UOoZZq <br>

**Dataset 320K_400K:** <br>
https://drive.google.com/drive/folders/15ZgDJ-4PpYAtNZRkTRlRmXulN6UOoZZq <br>

**Depth:** <br>
**Depthset Part1:** <br>
 https://drive.google.com/drive/folders/1d_X6jRnQ7vC-CpaM1J0UFbv6I2_ZTTyN <br>

**Depthset Part2:** <br>
https://drive.google.com/drive/folders/1ooDlcLX7CwpDYVOyW9Abw8hX_70vvfvO <br>

**Depthset Part3:** <br>
https://drive.google.com/drive/folders/1CroRGYI7FUJt7Lp9jRutNj9vhgi70f-I <br>


**Depthset Part4:** <br>
https://drive.google.com/drive/folders/1TsOKE4meT-oV2yb1CSsd12lUUCkOGl9j <br>

**Depthset Part5:** <br>
https://drive.google.com/drive/folders/1o8BsQynEXUu4XpdexLtz2JPaqtDyLmXy <br>


**Dataset Components**
1.	Background Images:
   <img src = "Dataset_Images/Background_Images.jpg">
 
2.	Foreground Images:
   <img src = "Dataset_Images/Foreground_Images.jpg">
3.	Foreground Masks:
   <img src = "Dataset_Images/Foreground_Mask _Images.jpg">
4.	Fg_Bg Images:
   <img src = "Dataset_Images/Fg_Bg_Masks.jpg">
5.	Depth Images:
   <img src = "Dataset_Images/Depth_Images.jpg">



**Dataset Statistics:**
1.	Kind of Images: <br>
   a.	Foreground (Fg) Images: 100 PNG Images of size less than 148*148. <br>
   b.	Background (Bg) Images: 100 JPEG Images of size 224*224 <br>
   c.	Fg_Bg Images: 100*(20*5)*40 JPEG = 400, 000 Images <br>
   Note: (20*5 is Fg images are taken 20 as a set and 5 such sets) <br>
   Foreground Images are Randomly placed in 20 positions on Background and then they are flipped) <br>
   d.	Masks Images:  100*(20*5)*40 JPEG = 400, 000 Images <br>
   e.	Depth Images: 400,000 Images JPEG <br>

2.	Total Images of Each Kind <br>
   a.	Foreground (Fg) Images: 		  100 <br>
   b.	Background (Bg) Images: 		  100 <br>
   c.	Fg_Bg Images:             		400,000 <br>
   d.	Masks Images:  			          400,000 <br>
   e.	Depth Images: 			           400,000 <br>

3.	Total Size of the Dataset:  		400000 + 400000 <br>
4.	Mean and Standard Deviation Values of Fg-Bg and Masks: <br>
   a.	Mean: ['0.306218862533569','0.287717372179031', 0.269325882196426'] <br>
   b.	Standard Deviation: ['0.214562639594078', '0.213071450591087', '0.213857620954514'] <br>



**Dataset Creation:** 

**How were Foreground (fg) created with Transparency? <br>**

Using the GIMP Tool, the foreground (fg) images were generated. The process is listed below: <br>
   1.	Open the image <br>
   2.	Add the Transparency Layer i.e., Alpha Channel on it <br>
   3.	Using the Free Select Tool, Select the Image Portion (for which transparent image has to be created) <br>
   4.	Then Select Invert <br>
   5.	Using the Edit Toolbar – clear the Background <br>
   6.	Reset the size of image to the require size using Scale Image <br>
   7.	Export the Image to PNG format (which has 4 channels – along with 3 channels RGB, it has additional Alpha Channel). The alpha channel allows for transparency in an image. Not all image formats support it, but PNG is one of the most commonly used image formats that does. <br>


**How were masks created for Foreground (fg) Images? <br>**

While generating the transparent foreground images, we can also create the mask for that foreground image. The process is listed below: <br>
   1.	Open the image <br>
   2.	Add the Transparency Layer i.e., Alpha Channel on it <br>
   3.	Using the Free Select Tool, Select the Image Portion (for which transparent image has to be created) <br>
   4.	Then Select Invert <br>
   5.	Using the Edit Toolbar – clear the Background <br>
   6.	Reset the size of image to the require size using Scale Image <br>
   7.	Edit – Fill the background of the image with Black Color <br>
   8.	Then Select Invert <br>
   9.	Edit – Fill the foreground of the image with white Color <br>
   10.	Export the Image to PNG format  <br>


**How did you overlay the fg over bg and created 20 variants? <br>**

To create the Fg over Bg images and also the Fg over Bg mask images, we will place the fg images on top of bg images at random positions, 10 times, and do this with flipped fg images, in total we will have <br>

(100) BG x (100) FG x flip 2 times (2*20(Randomly placed 10 images plus flips)) = 100 * 100 * 40 = 400,000 images <br>
BgFg + BgFg Masks =  400,000 + 400,000 = 800,000 <br>

Implementation Part: <br>
1.	Creating a directory. <br>
!mkdir OverlayDir <br>

2.	Creating subdirectories for BgFg and Masks for it. <br>
%cd OverlayDir <br>
!mkdir BgFg <br>
!mkdir BgFgMask <br>

3.	Keeping Foreground and flips randomly on Background. <br>
4.	Keeping Foreground masks and flips of masks randomly on Background. <br>

path = '/content/gdrive/My Drive/EVA4/fg_bg Images/' <br>
start1 = 1 #  Choosing numbers of images to be generated <br>
black = np.zeros((224,224)) <br>

for i in range(1,101): #1 background images – (1 – 100)

    	  bg = Image.open(f'{path}/BackgroundMall/bg{str(i)}.jpg')

    	  for j in  range(1,21): #1 foreground image and masks - (1 – 20)
          fg = Image.open(f'{path}/ForegroundPerson/fg{str(j)}.png')
          mask = Image.open(f'{path}/Mask/m{str(j)}.png').convert('1')

      	for k in range(1,21): # Placing flips (1 – 20)
             r1 = random.randint(1, 120)
             r2 = random.randint(1, 120)
             bg1 = copy.deepcopy(bg)
             bg2 = copy.deepcopy(bg)
             fg1 = copy.deepcopy(fg)
             m1 = copy.deepcopy(mask)
             black_img1 = Image.fromarray(black,mode='1')
           black_img2 = Image.fromarray(black,mode='1')

           flipfg = fg1.transpose(PIL.Image.FLIP_LEFT_RIGHT) #flip image
           flipmask = m1.transpose(PIL.Image.FLIP_LEFT_RIGHT) #flip mask
         bg1.paste(fg1,(r1,r2),fg1)
        	bg2.paste(flipfg,(r1,r2),flipfg)

        	black_img1.paste(m1,(r1,r2), m1)
        
        	black_img2.paste(flipmask,(r1,r2), flipmask)

        			 bg1.save(f"/content/OverlayDir/BgFg/bgfg{str(start1)}.jpg",optimize=True, quality=30)
        				 black_img1.save(f"/content/OverlayDir/BgFgMask/bgfgmask{str(start1)}.jpg",optimize=True, quality=30)

        	start1+=1
        					 bg2.save(f"/content/OverlayDir/BgFg/bgfg{str(start1)}.jpg",optimize=True, quality=30)
        			 black_img2.save(f"/content/OverlayDir/BgFgMask/bgfgmask{str(start1)}.jpg",optimize=True, quality=30)

        start1+=1
        print(start1)

5.	Saving into Corresponding Directories and Zip the files.

How did you create your depth images?  <br>
1.	Cloned the pretrained model from link Ialhashim(shared in the canvas 15A): <br>
https://github.com/ialhashim/DenseDepth <br>

2.	We get modules from the pretrained model and run here in colab. <br>
Modules : <br>

   a.	From Keras / Tensor Flow loading the model “nyu.h5”. <br>
   b.	From Layers importing Bilinearsamplingup 2D <br>
   c.	Load Images <br>
   d.	Save Images <br>
   e.	Predict function to do predictions. <br>


**#Keras / TensorFlow**

os.environ['TF_CPP_MIN_LOG_LEVEL'] = '5' <br>
from keras.models import load_model <br>
from layers import BilinearUpSampling2D <br>
#from utils import predict, load_images, display_images <br>
from matplotlib import pyplot as plt <br>

**#Custom object needed for inference and training <br>**
custom_objects = {'BilinearUpSampling2D': BilinearUpSampling2D, 'depth_loss_function': None} <br>

print('Loading model...')

**# Load model into GPU / CPU** <br>
model = load_model('nyu.h5', custom_objects=custom_objects, compile=False)

print('\nModel loaded ({0}).'.format("nyu.h5"))

**# Input images**
div = 200
num = 236801 #Generating sets of images (3200) batchwise(Batch 3)
for i in range((240000-236800)//div): 

   inputs = load_images(path ="/content/OverlayDir_Sample/BgFg/", start=num,end = num+div )
   print('\nLoaded ({0}) images of size {1}.'.format(inputs.shape[0], inputs.shape[1:]))
**# Compute results**
  outputs = predict(model, inputs)
**# Display results**
  display_images(outputs.copy(), inputs.copy(), start = num)
           num+=div

print("done")


3.	Zipping the Depth files into a separate directory inside DepthModel.

**Colab Links:**

  1.	Dataset(pynb):https://colab.research.google.com/drive/1gVyUY93azAIvZVuts5Pm1J1WG76rYgoA <br>
  2.	Statistics File (pynb): https://colab.research.google.com/drive/1hCZLKH8f-dheNitM7nw_qz6n605N3KGY#scrollTo=PUnyrvrum-b3 <br>
  3.	Depth Creation (pynb) : https://colab.research.google.com/drive/1BvpvWvAAWcUBBtRws20h5am1DiLQsTG3 <br>
