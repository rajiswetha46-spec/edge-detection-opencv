# edge-detection-opencv

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

- **Name:** SWETHA R 
- **Register No:**  212225100055

---

## Output
### Original Image:

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('flower.jpeg') 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
<img width="663" height="520" alt="Screenshot 2026-08-17 201342" src="https://github.com/user-attachments/assets/2bf07bb6-1bfc-4c13-8387-b5d58f3e6d17" />


###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map

```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```

<img width="664" height="515" alt="Screenshot 2026-08-17 201447" src="https://github.com/user-attachments/assets/ca08de94-6fb0-44c4-a3f2-fa92100ef615" />


###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges

```
image = cv2.imread("flower.jpeg")
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])
prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])
prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))
plt.imshow(prewitt, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
```
<img width="664" height="517" alt="Screenshot 2026-08-17 201741" src="https://github.com/user-attachments/assets/503fdeb0-d589-45e6-86c6-8ec9586f2d8e" />



###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

x = np.array([[1, 0], [0, -1]], dtype=np.float32)
y = np.array([[0, 1], [-1, 0]], dtype=np.float32)

gx = cv2.filter2D(gray_image, -1, x)
gy = cv2.filter2D(gray_image, -1, y)

roberts_edges = cv2.magnitude(gx.astype(float), gy.astype(float))

plt.imshow(roberts_edges, cmap='gray')
plt.title('Roberts Edge Detection')
plt.axis('off')
plt.show()
```

<img width="659" height="473" alt="Screenshot 2026-08-17 201841" src="https://github.com/user-attachments/assets/c1420cec-4e38-48eb-b927-591ee030ab3e" />


###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

```
import cv2
import matplotlib.pyplot as plt

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)

plt.imshow(abs(laplacian), cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```
<img width="650" height="474" alt="Screenshot 2026-08-17 201934" src="https://github.com/user-attachments/assets/af255771-feb3-464b-9ac2-179e55de84f8" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

```
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```

<img width="645" height="468" alt="Screenshot 2026-08-17 202024" src="https://github.com/user-attachments/assets/5cd6943a-d851-4cb8-93eb-f208605e769a" />



## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
