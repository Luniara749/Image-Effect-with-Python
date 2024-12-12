import cv2
import numpy as np
from PIL import Image, ImageDraw, ImageEnhance
import random

# Step 1: Apply motion blur to the bottom third of the image
image = cv2.imread('Sedney.jpeg')
height, width = image.shape[:2]
start_y = 2 * height // 3
end_y = height
kernel_size = 5
motion_blur_kernel = np.zeros((kernel_size, kernel_size))
motion_blur_kernel[:, kernel_size // 2] = 1
motion_blur_kernel = motion_blur_kernel / kernel_size
bottom_third = image[start_y:end_y, :]
motion_blur = cv2.filter2D(bottom_third, -1, motion_blur_kernel)
result = image.copy()
result[start_y:end_y, :] = motion_blur
cv2.imwrite('motion_blurred_bottom_third.jpg', result)

# Step 2: Convert the blurred image to grayscale
image = Image.open('motion_blurred_bottom_third.jpg')
bw_image = image.convert('L')
bw_image.save('bw_image.jpg')

# Step 3: Add grey ashes effect to the grayscale image
bw_image = Image.open('bw_image.jpg')
draw = ImageDraw.Draw(bw_image)
width, height = bw_image.size
for _ in range(150):  # Adjust the number of ashes for more density
    x = random.randint(0, width - 1)
    y = random.randint(0, height - 1)
    radius = 1  # Uniformly very small particles
    color = random.randint(128, 200)  # Ash in shades of light grey
    draw.ellipse([x - radius, y - radius, x + radius, y + radius], fill=color)
bw_image.save('grey_ashes_filter.jpg')

# Step 4: Lighten a fire smoke image
image = Image.open('Fire_smoke.png')
enhancer = ImageEnhance.Brightness(image)
lighter_image = enhancer.enhance(0.5)  # Adjust brightness
lighter_image.save('Fire_smoke_lighten.png')

# Step 5: Blend the lightened fire smoke image with the grayscale image
orange_light = Image.open('Fire_smoke_lighten.png')
base_image = Image.open('grey_ashes_filter.jpg').convert('RGB')  # Convert to RGB
orange_light_resized = orange_light.resize((50, 50))  # Resize to 50x50
x_offset = 0
y_offset = (base_image.height - orange_light_resized.height) // 2
base_image.paste(orange_light_resized, (x_offset, y_offset), orange_light_resized if orange_light_resized.mode == 'RGBA' else None)
base_image.save('Lighted_image.jpg')
base_image.show()
