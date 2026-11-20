# edge-detection-opencv.git-6

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** Kanishka V
- **Register No:** 212224100030

---

### Original Image
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('tiger.png') 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
### Output
<img width="516" height="372" alt="image" src="https://github.com/user-attachments/assets/1ba5b5f1-b94a-47ca-9a73-e69693edd629" />


###  Sobel Edge Detector
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```
### Output

<img width="516" height="372" alt="image" src="https://github.com/user-attachments/assets/f690d0eb-0076-43d5-ba7e-d828dbc08655" />



###  Prewitt Edge Detector
```
image = cv2.imread("tiger.png")
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
kernelx = np.array([[1, 0, -1],
                    [1, 0, -1],
                    [1, 0, -1]], dtype=np.float32)

kernely = np.array([[ 1,  1,  1],
                    [ 0,  0,  0],
                    [-1, -1, -1]], dtype=np.float32)
prewitt_x = cv2.filter2D(gray, cv2.CV_32F, kernelx)
prewitt_y = cv2.filter2D(gray, cv2.CV_32F, kernely)
prewitt = cv2.magnitude(prewitt_x, prewitt_y)
prewitt = cv2.convertScaleAbs(prewitt)
plt.figure(figsize=(6,6))
plt.imshow(prewitt, cmap="gray")
plt.title("Prewitt Edge Detection")
plt.axis("off")
plt.show()
```
### Output
<img width="485" height="351" alt="image" src="https://github.com/user-attachments/assets/f25fc646-153b-4714-8086-d9435b742669" />

###  Roberts Edge Detector
```
image = cv2.imread("tiger.png")
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
kernelx = np.array([[1, 0],
                    [0, -1]], dtype=np.float32)
kernely = np.array([[0, 1],
                    [-1, 0]], dtype=np.float32)
roberts_x = cv2.filter2D(gray, cv2.CV_32F, kernelx)
roberts_y = cv2.filter2D(gray, cv2.CV_32F, kernely)
roberts = cv2.magnitude(roberts_x, roberts_y)
roberts = cv2.convertScaleAbs(roberts)
plt.figure(figsize=(6,6))
plt.imshow(roberts, cmap="gray")
plt.title("Roberts Edge Detection")
plt.axis("off")
plt.show()
```
### Output
<img width="485" height="351" alt="image" src="https://github.com/user-attachments/assets/d29db794-1e82-42d0-a7de-61500b81324b" />



###  Laplacian Edge Detector
```
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
```
### Output
<img width="516" height="372" alt="image" src="https://github.com/user-attachments/assets/c8b580ca-1c6d-4729-b1da-2e0361adb008" />

###  Canny Edge Detector
```
image = cv2.imread("tiger.png")
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray, 100, 200)
plt.imshow(edges, cmap="gray")
plt.title("Canny Edge Detection")
plt.axis("off")
plt.show()
```
### Output
<img width="516" height="372" alt="image" src="https://github.com/user-attachments/assets/0f74c363-8a09-4878-a103-6793dafc3e4c" />


---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
