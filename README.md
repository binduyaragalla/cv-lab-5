LAB-5: Bit-Plane Slicing


Aim:
To implement Bit-Plane Slicing on an image to separate it into 8 individual bit planes and analyze the contribution of each bit plane to visual perception.


Description:
Bit-Plane Slicing is an image processing technique used to decompose an image into individual binary bit planes. An 8-bit image contains 8 bit planes, from Bit Plane 0 (LSB) to Bit Plane 7 (MSB). Higher-order bit planes generally contain major visual information, while lower-order bit planes contain fine details and subtle variations.

Libraries Used:
OpenCV (cv2): To read and process the input image.
NumPy: To perform bitwise operations and extract bit planes.
Matplotlib: To display the original image and extracted bit planes.


Input Image:
<img width="387" height="516" alt="image" src="https://github.com/user-attachments/assets/f30a3e5f-025f-4b85-b5b3-abd3598af4a8" />


CODE:
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("/content/mikasa.jpg", cv2.IMREAD_COLOR)

if img is None:
    print("Error: Image not found.")
else:
    plt.figure(figsize=(12, 10))
    plt.subplot(3, 3, 1)
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
    plt.title("Original Image")
    plt.axis('off')

    for i in range(8):
        bit_plane = (img >> i) & 1
        vis_plane = bit_plane * 255

        plt.subplot(3, 3, i + 2)
        plt.imshow(cv2.cvtColor(vis_plane, cv2.COLOR_BGR2RGB))
        plt.title(f"Bit Plane {i}")
        plt.axis('off')

    plt.tight_layout()
    plt.show()

    Output Image

The output displays the original image along with its 8 extracted bit planes (Bit Plane 0 to Bit Plane 7) in a 3 × 3 grid.
 <img width="959" height="990" alt="image" src="https://github.com/user-attachments/assets/f800e982-e8f7-4bb9-8107-b077768e6565" />


 

Result:
Bit-Plane Slicing was successfully implemented, and the input image was separated into 8 individual bit planes for visualization and analysis.

Conclusion:
Bit-Plane Slicing helps identify the contribution of individual bits to an image. Higher-order bit planes generally preserve the major visual structure, whereas lower-order bit planes represent finer details and intensity variations.
