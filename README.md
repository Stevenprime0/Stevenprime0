from PIL import Image

# Load the new image uploaded by the user
image_path_3 = '/mnt/data/8f2e633f2aaeb20d4072f07808856ff8.jpg'
image_3 = Image.open(image_path_3)

# Convert the image to RGBA to handle transparency
rgba_image_3 = image_3.convert("RGBA")

# Load the pixel data
data_3 = rgba_image_3.getdata()

# Define the range for the gray background, then replace it with transparency
new_data_3 = []
for item in data_3:
    # Check if the pixel is a dark gray (specific to the background shade)
    if 50 <= item[0] <= 70 and 50 <= item[1] <= 70 and 50 <= item[2] <= 70:
        # Replace gray with transparency
        new_data_3.append((255, 255, 255, 0))
    else:
        # Keep the pixel as it is
        new_data_3.append(item)

# Update the image with transparency where the gray background was
rgba_image_3.putdata(new_data_3)

# Save the modified image with transparency
output_path_3 = "/mnt/data/nissan_gt_r_transparent.png"
rgba_image_3.save(output_path_3, "PNG")

output_path_3
