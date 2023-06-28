import cv2

def image_to_pencil_sketch(image_path):
    
    image = cv2.imread(image_path)

   
    gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

   
    inverted_image = cv2.bitwise_not(gray_image)

   
    blurred_image = cv2.GaussianBlur(inverted_image, (21, 21), 0)

    
    pencil_sketch = cv2.divide(gray_image, blurred_image, scale=256.0)

    return pencil_sketch


image_path = 'path/to/your/image.jpg'


sketch = image_to_pencil_sketch(image_path)


cv2.imshow('Original Image', cv2.imread(image_path))
cv2.imshow('Pencil Sketch', sketch)
cv2.waitKey(0)
cv2.destroyAllWindows()                                                   
                                                               
