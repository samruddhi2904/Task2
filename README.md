# Task2
from PIL import Image

def encrypt_image(image_path, operation, value):
    """Encrypts an image using the specified operation and value.

    Args:
        image_path: Path to the image file.
        operation: The encryption operation (e.g., 'swap', 'add', 'subtract', 'multiply', 'divide').
        value: The value to use for the operation.

    Returns:
        The encrypted image.
    """

    img = Image.open(image_path)
    pixels = img.load()

    width, height = img.size

    for x in range(width):
        for y in range(height):
            r, g, b = pixels[x, y]

            if operation == 'swap':
                pixels[x, y] = (b, g, r)
            elif operation == 'add':
                pixels[x, y] = (r + value, g + value, b + value)
            elif operation == 'subtract':
                pixels[x, y] = (r - value, g - value, b - value)
            elif operation == 'multiply':
                pixels[x, y] = (r * value, g * value, b * value)
            elif operation == 'divide':
                pixels[x, y] = (r // value, g // value, b // value)

    return img

# Example usage:
image_path = 'your_image.jpg'
encrypted_image = encrypt_image(image_path, 'swap', 0)
encrypted_image.save('encrypted_image.jpg')
