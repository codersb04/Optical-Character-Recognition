# Optical-Character-Recognition

This repository include file related to my Optical Charater Recognition(OCR) practice.

### Library used for OCR techniques are:
- [Pillow(PIL)](https://pillow.readthedocs.io/en/stable/installation.html#basic-installation) : Used mainly to know about the image. Installation in windows: **pip install pillow**
- [OpenCV]( https://pypi.org/project/opencv-python/): Used to trasform the image or process the image before extracting the information. Installation in window: **pip install opencv-python**
- [Tessereact(PyTesseract)](https://pypi.org/project/pytesseract/): Extract the information or perform OCR on processed Image. Installation on window:
  - Download Tesseract, from [GitHub Repo](https://github.com/UB-Mannheim/tesseract/wiki )
  - Install Tesseract to the system and add it's path to the environment variable.
  - Type **tesseract --version** on power shell or command prompt to check whether it is properly installed
  - Install 'pytesseract' on Anaconda prompt using the command: **pip install pytesseract**
  - Extra guide for Tesseract  https://guides.library.illinois.edu/c.php?g=347520&p=4116757
 
## Pillow Library
Uses:
- Load the image
- Know the format and size of the image

## OpenCV
Task than can be achieved by openCV

-Inverted Images: Bitwise NOT operation is performed on the pixel value of the input image. The white portion converted to black and vice a versa.

-Rescaling: Resizing the Image

-Binarization: Convert the image to Black and white. To achieve this, the image is 1st tranformed to grascal image then binarize the image using threshold function

-Noise Removal: Remove the pixels that doesn't hold any value. This is achieved by following steps:
  - Create a kernel(empty matrix)
  - Dilate the image, which increses the white portion of the image
  - Create new kernel again and Erode the Image using new keral. Erode Reduce the white portion
  - Apply a combition of Erode and Dilation.
  - Blur the Image

-Dilation and Erosion: 
  -  Can be used to make the font thinner or thicker. But the most most important step is to invert the image first, so that text would be in white. Erosion used to Thin the text while Dilation can be used to thicken the text.
    
-[Rotation/ Deskewing](https://becominghuman.ai/how-to-automatically-deskew-straighten-a-text-image-using-opencv-a0c30aed83df): 
 1. Covert the Grayscale
 2. BLur the Image using Gaussian Blur
 3. Apply Threshold to perform binarization
 4. Dilate the image using the kernel
 5. Find the Contours
 6. Find the largest contours and surround in the min area box
 7. Draw the minimum area rectangle on the image
 8. Get the angle of the rectangle
 9.  Rotate the image to that angle
    
-Removing Borders: Get the largest contours and extract its cordinates. FInally crop the Image coresponding to the coordinates.

-Missing Borders: Create border using function **copyMakeBorder**

-Transparency/ Alpha Channel

## pytesseract
Used to extract the information from the Image. To get the best result image should be processed.

- **Extracting the Index from Image using pytesseract**: Steps Followed
    - Convert to Grayscale and subsquently Blur the Image
    - Binarize the image using Threshold
    - Dilate the Image and Get the contours
    - Get the contours only for the long rectangle box and draw them on the image
    - Get the first item on the image and replace any non-alphabetic character to empty string
    - Finally sort the list
- **Extracting the body part footnote and side notes from the Image**
  - Image processing steps are similar to the above
  - Dilation is done with different kernel size based on the part of Image, need to extract</br></br></br>
 

Reference: 
1. OCR in Python Tutorials, Introduction to OCR (OCR in Python Tutorials 01.01), Python Tutorials for Digital Humanities, https://www.youtube.com/watch?v=tQGgGY8mTP0&list=PL2VXyKi-KpYuTAZz__9KVl1jQz74bDG7i&index=1
