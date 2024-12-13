from PIL import Image, ImageEnhance
import numpy as np

image = Image.open('Times Square 4.jpg')
image_array = np.array(image)

red_channel = image_array[:, :, 0]
green_channel = image_array[:, :, 1]
blue_channel = image_array[:, :, 2]

gray_value = np.dot(image_array[..., :3], [0.2989, 0.5870, 0.1140])
green_channel = gray_value
blue_channel = gray_value

# Uncomment the following line if you want to boost the red contrast:
# red_channel = np.clip(red_channel * 1.5, 0, 255)

modified_image_array = np.stack([red_channel, green_channel, blue_channel], axis=2)

modified_image = Image.fromarray(modified_image_array.astype('uint8'))
modified_image.save('red_only_image.jpg')

image = Image.open('red_only_image.jpg')
enhancer = ImageEnhance.Contrast(image)
image_enhanced = enhancer.enhance(2.5)  # Adjust contrast level as needed

Brightenhancer = ImageEnhance.Brightness(image_enhanced)
darker_image = Brightenhancer.enhance(1)  # Adjust brightness level as needed

darker_image.save('enhanced_image.jpg')
darker_image.show()
