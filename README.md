# EXP1 - Image_Handling_and_Pixel_Transformations_Using_OpenCV_Completion_requirements
## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
# NAME : DEEPAKKUMAR S 
# REG NO : 212225230042

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```

import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('Eagle_in_Flight.jpg', 0)

```

#### 2. Print the image width, height & Channel.
```
h, w = img.shape
print("Width:", w, "Height:", h, "Channels: 1")
```

#### 3. Display the image using matplotlib imshow().
```
plt.imshow(img, cmap='gray')
plt.show()

```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
cv2.imwrite('Eagle_in_Flight.jpg', img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
color = cv2.imread('Eagle_in_Flight.jpg')
color = cv2.cvtColor(color, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
print("Color image shape:", color.shape)
plt.imshow(color)
plt.show()

```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
``
crop = color[100:400, 100:400]
```

#### 8. Resize the image up by a factor of 2x.
```
resize = cv2.resize(crop, None, fx=2, fy=2)
```

#### 9. Flip the cropped/resized image horizontally.
```
flip = cv2.flip(resize, 1)
plt.imshow(flip)
plt.show()

```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```
apollo = cv2.imread('Apollo-11-launch.jpg')
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
h, w = apollo.shape[:2]
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
size = cv2.getTextSize(text, font_face, 1, 1)[0]
x = (w - size[0]) // 2
cv2.putText(apollo, text, (x, h-20), font_face, 1,
            (255, 255, 255), 2)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
cv2.rectangle(apollo, (100, 50), (400, h-50), (255, 0, 255), 2)
```

#### 13. Display the final annotated image.
```
plt.imshow(cv2.cvtColor(apollo, cv2.COLOR_BGR2RGB))
plt.show()

```

#### 14. Read the image ('Boy.jpg').
```
img = cv2.imread('Boy.png')
```

#### 15. Adjust the brightness of the image.
```
matrix_ones = np.ones(img.shape, dtype=np.float64) * 50
matrix = matrix_ones.astype(np.uint8)
```

#### 16. Create brighter and darker images.
```
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
for x in [img, img_darker, img_brighter]:
    plt.imshow(cv2.cvtColor(x, cv2.COLOR_BGR2RGB))
    plt.axis('off')
    plt.show()
```

#### 18. Modify the image contrast.
```
matrix1 = np.ones(img.shape, dtype=np.float64) * 1.1
matrix2 = np.ones(img.shape, dtype=np.float64) * 1.2
img_higher1 = cv2.multiply(img.astype(np.float64), matrix1)
img_higher2 = cv2.multiply(img.astype(np.float64), matrix2)
img_higher1 = np.clip(img_higher1, 0, 255).astype(np.uint8)
img_higher2 = np.clip(img_higher2, 0, 255).astype(np.uint8)
img_lower = cv2.convertScaleAbs(img, alpha=0.8)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
for x in [img, img_lower, img_higher1, img_higher2]:
    plt.imshow(cv2.cvtColor(x, cv2.COLOR_BGR2RGB))
    plt.axis('off')
    plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```# 20. Split B, G, R channels
B, G, R = cv2.split(img)
for x in [B, G, R]:
    plt.imshow(x, cmap='gray')
    plt.axis('off')
    plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```
merged_rgb = cv2.merge([R, G, B])
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis('off')
plt.show()

```

#### 22. Split the image into the H, S, V components & Display the channels.
```
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
H, S, V = cv2.split(hsv)
for x in [H, S, V]:
    plt.imshow(x, cmap='gray')
    plt.axis('off')
    plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.merge([H, S, V])
merged_rgb = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(merged_rgb)
plt.title("Merged HSV Image")
plt.axis('off')
plt.show()
```

## Output:
- **i)** Read and Display an Image.  
- **ii)** Adjust Image Brightness.  
- **iii)** Modify Image Contrast.  
- **iv)** Generate Third Image Using Bitwise Operations.
