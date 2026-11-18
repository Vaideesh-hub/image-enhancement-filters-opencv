# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** Vaideeshwaran G 
- **Register No:** 212225240178

---
## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
```
# Read the input image
image = cv2.imread('cat.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) 
```
```
kernel = np.ones((5,5), dtype = np.float32) / 5**2

print (kernel)
```
## Output
<img width="352" height="113" alt="Screenshot 2026-11-18 154718" src="https://github.com/user-attachments/assets/daa6699a-b0ba-498b-a883-bb0091c41e14" />


## Program
```
# To Perform Convolution 
image = cv2.imread('cat.jpg')

dst = cv2.filter2D(image, ddepth = -1, kernel = kernel)

plt.figure(figsize = [20,10])
plt.subplot(121); plt.axis('off'); plt.imshow(image[:,:,::-1]); plt.title("Original Image")
plt.subplot(122); plt.axis('off'); plt.imshow(dst[:,:,::-1]);   plt.title("Convolution Result");
```


## Output
<img width="1510" height="401" alt="Screenshot 2026-11-18 154826" src="https://github.com/user-attachments/assets/6598007c-65d4-41c9-baa0-4b830da9df2a" />

## Program
```
average_filter = cv2.blur(image, (30,30))
```
```
# Display the images.

plt.figure(figsize = (18, 6))
plt.subplot(121); plt.imshow(image [:, :, ::-1]); plt.title('Input Image')
plt.subplot(122); plt.imshow(average_filter[:, :, ::-1]); plt.title('Output Image ( Average Filter)')
```
## Output
<img width="1506" height="445" alt="Screenshot 2026-11-18 154856" src="https://github.com/user-attachments/assets/365ceec4-bd92-4f59-a2fe-9bf6c921fb0a" />

## Program
```
kernel = np.array([[1,2,1],[2,4,2],[1,2,1]])/16
weighted_average_filter = cv2.filter2D(image, -1, kernel)
# Display the images.
plt.figure(figsize = (18, 6))
plt.subplot(121);plt.subplot(121); plt.imshow(image [:, :, ::-1]); plt.title('Input Image')
plt.subplot(122);plt.imshow(weighted_average_filter[:, :, ::-1]); plt.title('Output Image(weighted_average_filter)');plt.show()
```

## Output
<img width="1473" height="432" alt="Screenshot 2026-11-18 155034" src="https://github.com/user-attachments/assets/801ac232-eaaf-43d8-a3e9-b76775afa5b9" />

## Program
```
# Apply Gaussian blur.
gaussian_filter = cv2.GaussianBlur(image, (29,29), 0, 0)
# Display the images.

plt.figure(figsize = (18, 6))
plt.subplot(121); plt.imshow(image [:, :, ::-1]); plt.title('Input Image')
plt.subplot(122); plt.imshow(gaussian_filter[:, :, ::-1]); plt.title('Output Image ( Gaussian Filter)')
```

## Output
<img width="1487" height="461" alt="Screenshot 2026-11-18 155110" src="https://github.com/user-attachments/assets/09b8ace3-0755-4386-ab41-b3410f6c9982" />

## Program
```
# iv) Using Median Filter
median_filter = cv2.medianBlur(image, 19)
```
```
# Display the images.

plt.figure(figsize = (18, 6))
plt.subplot(121); plt.imshow(image [:, :, ::-1]); plt.title('Input Image')
plt.subplot(122); plt.imshow(median_filter[:, :, ::-1]); plt.title('Output Image ( Median_filter)')
```

## Output
<img width="1476" height="441" alt="Screenshot 2026-11-18 155211" src="https://github.com/user-attachments/assets/52020713-169d-425f-9119-1a2210f231dd" />

## Program
```
# i) Using Laplacian Kernel (Manual Kernel)
laplacian_kernel = np.array([[0, -1, 0],
                             [-1, 5, -1],
                             [0, -1, 0]])
sharpened_laplacian_kernel = cv2.filter2D(image, -1, kernel = laplacian_kernel)
```
```
# Display the images.

plt.figure(figsize = (18, 6))
plt.subplot(121); plt.imshow(image [:, :, ::-1]); plt.title('Input Image')
plt.subplot(122); plt.imshow(sharpened_laplacian_kernel[:, :, ::-1]); plt.title('Output Image ( Laplacian_filter)')
```

## Output
<img width="1482" height="447" alt="Screenshot 2026-11-18 155358" src="https://github.com/user-attachments/assets/d8e0d901-377f-43f0-bb34-96c036e05d47" />

## Program
```
# ii) Using Laplacian Operator (OpenCV built-in)
gray_image = cv2.cvtColor(image, cv2.COLOR_RGB2GRAY)
laplacian_operator = cv2.Laplacian(gray_image, cv2.CV_64F)
laplacian_operator = np.uint8(np.absolute(laplacian_operator))
```
```
# Display the images.

plt.figure(figsize = (18, 6))
plt.subplot(131); plt.imshow(image [:, :, ::-1]); plt.title('Input Image')
plt.subplot(132); plt.imshow(gray_image, cmap='gray'); plt.title('Gray_image')
plt.subplot(133); plt.imshow(laplacian_operator,cmap='gray'); plt.title('Output Image ( Laplacian_filter)')
```

## Output
<img width="1501" height="357" alt="Screenshot 2026-11-18 155449" src="https://github.com/user-attachments/assets/b3287c4a-a32c-49b3-8a2c-e36638f8fb3e" />

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
