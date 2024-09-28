# Implementation-of-filter
## Aim:
To implement filters for smoothing and sharpening the images in the spatial domain.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step 1: 
Import necessary libraries (cv2, NumPy, Matplotlib) for image loading, filtering, and visualization.

### Step 2: 
Load the image using cv2.imread() and convert it to RGB format using cv2.cvtColor() for proper display in Matplotlib.

### Step 3: 
Apply different filters:
1. Averaging Filter: Define an averaging kernel using np.ones() and apply it to the image using cv2.filter2D().
2. Weighted Averaging Filter: Define a weighted kernel (e.g., 3x3 Gaussian-like) and apply it with cv2.filter2D().
3. Gaussian Filter: Use cv2.GaussianBlur() to apply Gaussian blur.
4. Median Filter: Use cv2.medianBlur() to reduce noise.
5. Laplacian Operator: Use cv2.Laplacian() to apply edge detection.
    
### Step 4: 
Display each filtered image using plt.subplot() and plt.imshow() for side-by-side comparison of the original and processed images.

### Step 5: 
Save or show the images using plt.show() after applying each filter to visualize the effects of smoothing and sharpening.

## Program:
### Developed By   : LISIANA T
### Register Number: 212222240053
```
import cv2
import matplotlib.pyplot as plt
import numpy as np
image1 = cv2.imread("dog.jpg")
image2 = cv2.cvtColor(image1, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")
```
### 1. Smoothing Filters

i) Using Averaging Filter
```
kernel = np.ones((11, 11), np.float32) / 121
averaging_image = cv2.filter2D(image2, -1, kernel)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(averaging_image)
plt.title("Averaging Filter Image")
plt.axis("off")
plt.show()

```
ii) Using Weighted Averaging Filter
```Python
kernel1 = np.array([[1, 2, 1],
                    [2, 4, 2],
                    [1, 2, 1]]) / 16

weighted_average_image = cv2.filter2D(image2, -1, kernel1)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(weighted_average_image)
plt.title("Weighted Average Filter Image")
plt.axis("off")
plt.show()

```
iii) Using Minimum Filter
```Python
min_filter = cv2.erode(image, np.ones((5, 5), np.uint8))
min_filter_rgb = cv2.cvtColor(min_filter, cv2.COLOR_BGR2RGB)
plt.imshow(min_filter_rgb)
plt.title("Minimum Filter")
plt.show()
```

iv) Using Maximum Filter
```
max_filter = cv2.dilate(image, np.ones((5, 5), np.uint8))
max_filter_rgb = cv2.cvtColor(max_filter, cv2.COLOR_BGR2RGB)
plt.imshow(max_filter_rgb)
plt.title("Maximum Filter")
plt.show()
```

v) Using Median Filter
```
median_filter = cv2.medianBlur(image, 5)
median_filter_rgb = cv2.cvtColor(median_filter, cv2.COLOR_BGR2RGB)
plt.imshow(median_filter_rgb)
plt.title("Median Filter")
plt.show()
```

### 2. Sharpening Filters
i) Using Laplacian Linear Kernal
```
sharpened_image = cv2.filter2D(smoothed_image, -1, kernel2)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(sharpened_image)
plt.title("Sharpened Image (Laplacian Kernel)")
plt.axis("off")
plt.show()
```
ii) Using Laplacian Operator
```
laplacian = cv2.Laplacian(image2, cv2.CV_64F)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian Operator Image")
plt.axis("off")
plt.show()
```

## OUTPUT:
### 1. Smoothing Filters
</br>

i) Using Averaging Filter

![img](https://raw.githubusercontent.com/Girithickrohan/Implementation-of-filter/refs/heads/main/1.png)

ii)Using Weighted Averaging Filter

![img](https://raw.githubusercontent.com/Girithickrohan/Implementation-of-filter/refs/heads/main/2.png)

iii) Using Minimum Filter

![img](https://raw.githubusercontent.com/Girithickrohan/Implementation-of-filter/refs/heads/main/3.png)

iv) Using Maximum Filter

![img](https://raw.githubusercontent.com/Girithickrohan/Implementation-of-filter/refs/heads/main/4.png)

v) Using Median Filter

![img](https://raw.githubusercontent.com/Girithickrohan/Implementation-of-filter/refs/heads/main/5.png)


### 2. Sharpening Filters
</br>

i) Using Laplacian Kernal

![img](https://raw.githubusercontent.com/Girithickrohan/Implementation-of-filter/refs/heads/main/6.png)

ii) Using Laplacian Operator

![img](https://raw.githubusercontent.com/Girithickrohan/Implementation-of-filter/refs/heads/main/7.png)

## Result:
Thus the filters are designed for smoothing and sharpening the images in the spatial domain
