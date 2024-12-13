# Image-Effect-with-Python
This README provides an overview of two separate Python scripts designed for distinct image processing tasks. The purpose of creating and saving each processed image at every step is to allow independent viewing of each stage, ensuring a clearer understanding of the image editing path.

Pipeline 1: Sedney Image Processing

Description

This script applies a series of processing techniques to an image named Sedney.jpeg, focusing on motion blur, grayscale conversion, ash effects, and combining an orange light overlay. Each step of the transformation is saved as an individual image file.

Process Steps

Motion Blur

Applies a vertical motion blur effect to the bottom third of the image.

Output: motion_blurred_bottom_third.jpg

Grayscale Conversion

Converts the blurred image to grayscale to create a black-and-white version.

Output: bw_image.jpg

Ash Effects

Adds random ash-like particles to the grayscale image for a textured look.

Output: grey_ashes_filter.jpg

Orange Light Overlay

Enhances the image by overlaying a resized orange light effect on the middle-left side of the grayscale image.

Output: Lighted_image.jpg

Requirements

Python 3.x

Libraries: cv2, numpy, PIL

Usage

Run the script in the directory containing Sedney.jpeg and supporting overlay images. Ensure all required images (e.g., Fire_smoke.png) are present.
