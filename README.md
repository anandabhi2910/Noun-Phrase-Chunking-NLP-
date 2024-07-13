# Noun-Phrase-Chunking-NLP-
### In this repo, I will create a recurrent neural network for noun phrase chunking in given sentences with POS tags.

## To install the requirements <pip install -r requirements.txt>
## Python version needed Python 3.10.4
## To run the code, follow this command <python main.py> 

### Description if code:
In this code:

1. Canny Edge Detection is applied to detect edges.
2. Hough Line Transform is used to detect line segments.
3. The lengths of the lines are converted from pixels to millimeters by multiplying by 0.1.
4. The angle between the two longest lines is calculated if at least two lines are detected.

#### Use Case Explanation
> The combination of Canny Edge Detection and Hough Line Transform is particularly powerful for detecting and analyzing straight edges in images, which is useful in many applications, including this one involving pencils.

##### Canny Edge Detection: This step helps to preprocess the image by detecting edges and reducing noise, which simplifies the subsequent line detection step. The detected edges highlight potential lines in the image.

##### Hough Line Transform: This step uses the edges detected by the Canny algorithm to identify straight lines in the image. In this specific use case, it helps in detecting the pencils by finding the straight edges that correspond to the pencils.

#### Application in the Code
1. Edge Detection: The image is first converted to grayscale and then edges are detected using Canny Edge Detection (cv2.Canny).
2. Line Detection: The edges are then processed using Hough Line Transform (cv2.HoughLinesP) to detect lines in the image.
3. Line Drawing and Measurement: The detected lines are drawn on the image, and their lengths are calculated. The lengths are converted to millimeters assuming 1px = 0.1mm.
4. Angle Calculation: The angle between the two longest detected lines (representing the pencils) is calculated.


##### Length Calculation
The length of each detected line segment is calculated using the Euclidean distance formula. Here's a step-by-step explanation:

> Extract Coordinates: For each detected line, extract the coordinates 
(𝑥1,𝑦1) and (𝑥2,𝑦2) of its endpoints.

> Compute Length: Calculate the Euclidean distance between the endpoints using the formula:

> ```length = root((𝑥2−𝑥1)^2 + (𝑦2−𝑦1)^2)```
 
> Convert to Millimeters: Convert the length from pixels to millimeters, assuming 1 pixel equals 0.1 millimeters:

> ```length_mm = length × 0.1```

> This process is repeated for each detected line, and the lengths are stored in a list.

##### Angle Calculation
The angle between the two longest lines (assumed to represent pencils) is calculated as follows:

> Extract Vectors: For each of the two longest lines, extract the vectors representing the lines. If the endpoints of the lines are 

(𝑥1,𝑦1) , (𝑥2,𝑦2) for the first line, and 
(𝑥3,𝑦3) , (𝑥4,𝑦4) for the second line,

then the vectors are:

```vector1 = [𝑥2 − 𝑥1 , 𝑦2 − 𝑦1]```
```vector2 = [𝑥4 − 𝑥3 , 𝑦4 − 𝑦3]```

> Normalize Vectors: Normalize these vectors to unit vectors:

```unit_vector1 = vector1 / (∥vector1∥)``` 
```unit_vector2 = vector2 / (∥vector2∥)``` 

​
 
> Dot Product: Calculate the dot product of the two unit vectors:
```dot_product=unit_vector1⋅unit_vector2```

> Angle Calculation: Use the arccosine function to find the angle between the two vectors:
```angle=arccos(dot_product)```

> Convert to Degrees: Convert the angle from radians to degrees:
```angle_degrees=np.degrees(angle)```
