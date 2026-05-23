# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

## Ex. No: 03
# Histogram Equalization Using OpenCV (Grayscale & Color Images)
### Name : RAJA GOPAL V Reg. No : 212223240134

#### Write a Python program using OpenCV to perform histogram equalization on the given grayscale image "parrot.jpg".

```
# Import required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

```
# Read the image in grayscale format

img = cv2.imread("parrot.jpg",cv2.IMREAD_GRAYSCALE)
# Display the grayscale image.
plt.imshow(img,cmap="gray")
plt.axis("off")
```

```
# Plot the histogram of the grayscale image
plt.hist(img.ravel(),256,range=[0,256])
plt.title("Histogram")
plt.show()
```

```
# Perform histogram equalization
equalized_img = cv2.equalizeHist(img)
plt.figure(figsize=(10, 8))
```

```
# Display [1] the Original Image (Gray Image) and its Histogram, and [2] the Enhanced Image and its Histogram using a 2×2 layout in Matplotlib.
# Original Grayscale Image
plt.imshow(img, cmap='gray')
plt.title('Original Grayscale Image')
plt.axis('off')
```

```
# Plot the histogram of the grayscale image
plt.hist(img.ravel(),256,range = [0, 256]);
plt.title('Original Image')
plt.show()
```

```
# Enhanced (Equalized) Image

plt.imshow(equalized_img, cmap='gray')
plt.title('Enhanced (Equalized) Image')
plt.axis('off')
```

```
#Plot the histogram of the enhanced(equalized) image
plt.hist(equalized_img.ravel(), 256, range = [0, 256]); 
plt.title('Equalized Histogram')
```

## Write a Python program using OpenCV to perform color image enhancement through histogram equalization in the HSV color space on the given image "parrot.jpg".

```
# Import required libraries

import cv2
import numpy as np
from matplotlib import pyplot as plt
```

```
# Read the given color image "parrot.jpg"

img = cv2.imread("parrot.jpg")
# Plot the histogram of color image

colors = ('b', 'g', 'r')

for i, color in enumerate(colors):
    hist = cv2.calcHist([img], [i], None, [256], [0, 256])
    plt.plot(hist, color=color)

plt.title("Histogram of Original Color Image")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")
plt.show()
```

```
# Convert BGR image to HSV color space

hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```

```
# Perform histogram equalization

h, s, v = cv2.split(hsv)
v_eq = cv2.equalizeHist(v)
hsv_eq = cv2.merge((h, s, v_eq))
```

```
# Convert back to BGR format

enhanced_img = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)
```

```
# Display
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
enhanced_rgb = cv2.cvtColor(enhanced_img, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(10, 5))

# Original Image
plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

# Enhanced Image
plt.subplot(1, 2, 2)
plt.imshow(enhanced_rgb)
plt.title("Enhanced Image")
plt.axis("off")

plt.tight_layout()
plt.show()
```

##  Output

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
<img width="592" height="418" alt="image" src="https://github.com/user-attachments/assets/b333e0c5-0ab6-4704-a2b0-2c4f8fa783d9" />

- Histogram of original grayscale image is plotted  

<img width="778" height="498" alt="image-1" src="https://github.com/user-attachments/assets/c8c75b0d-5b2a-4a1e-b047-e21b0d4050dd" />


- Enhanced image after histogram equalization is displayed 
<img width="625" height="417" alt="image-3" src="https://github.com/user-attachments/assets/de38eeab-4935-4d33-ae79-8852c0e063f6" />


- Histogram of enhanced grayscale image shows improved contrast  
<img width="758" height="488" alt="image-4" src="https://github.com/user-attachments/assets/5e9054b5-c59a-4d9e-a1ed-4f7533527819" />






### Color Image Histogram Equalization

- Original color image is displayed  

<img width="564" height="416" alt="image-6" src="https://github.com/user-attachments/assets/18ed523d-06e3-45e1-b2ce-86fde86dfac9" />



- Histogram of B, G, R channels is plotted 

<img width="750" height="514" alt="image-5" src="https://github.com/user-attachments/assets/580b67ee-27b5-40ce-8f50-a7bee02523f1" />




- Enhanced image after HSV-based equalization is displayed

<img width="573" height="400" alt="image-7" src="https://github.com/user-attachments/assets/836be316-4af3-4619-ad4a-e10d9ecfa331" />






- Histogram of enhanced image shows better intensity distribution  
<img width="740" height="506" alt="image-8" src="https://github.com/user-attachments/assets/9e1e6c0e-d1f8-4f6c-a174-646a851f7ba1" />



---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
