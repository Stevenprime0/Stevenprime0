from PIL import Image

# Carga la imagen
image_path = 'ruta/de/tu/imagen.jpg'  # Asegúrate de poner la ruta correcta de tu archivo
image = Image.open(image_path)

# Convierte la imagen a RGBA para manejar la transparencia
rgba_image = image.convert("RGBA")

# Carga los datos de los píxeles
data = rgba_image.getdata()

# Define el rango de gris para reemplazarlo con transparencia
new_data = []
for item in data:
    if 50 <= item[0] <= 70 and 50 <= item[1] <= 70 and 50 <= item[2] <= 70:
        new_data.append((255, 255, 255, 0))  # Hace el píxel transparente
    else:
        new_data.append(item)  # Mantiene el píxel

# Actualiza los datos de la imagen
rgba_image.putdata(new_data)

# Guarda la imagen con fondo transparente
output_path = "nissan_gt_r_transparent.png"
rgba_image.save(output_path, "PNG")
