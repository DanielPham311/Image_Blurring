# Image_Blurring
A project created to blur an image of choice using K-Means algorithm with Python.

## Abstract:
In general, an image is treated as a multi-dimensional array (or a matrix), in which a pixel is represented by an array of three values corresponding to three color channels in the RGB color system. The way this program works is practically rounding the pixels' RGB values to some sort of median value so that the image can be reduced in size via the deduction in the number of colors presented on the image, at the cost of the deterioration of the quality itself. The more clusters (number of colors) are used, the better the quality of the image. A self-implemented version of the K-Means algorithm is provided in this project but you can used pre-written ones of any module.

## Techniques:
### Libraries:
<ul>
  <li><b>Numpy</b>: conducting tasks relating to numpy ndarrays, including multiplication, inversion, addition, etc...</li>
  <li><b>Pyplot</b>: displaying images for visualization and comparison</li>
  <li><b>Image</b>: mainly for saving the image into the desired format (pdf or png) (can be improved to other formats of choice)</li>
  <li><b>copy</b>: for copying array objects to ensure nothing happens to the original array</li>
</ul>

### K-Means algorithm:
I'm not an expert but I'll explain this algorithm according to my own understandings and its role in the project:
<ul>
  <li><b>Definition</b>: the data provided will be clustered into <i>K</i> groups. It allows us to cluster the data into different groups and also a centroid based algorithm, in which each cluster is associated with a centroid. In this project's perspective, each pixel of the image will be asscociated with a certain centroid (either randomly generated or selected from the image itself). From there, the Gaussian blur algorithm is applied with a certain number of iterations and the process of centroid association continues until we receive the resulting image.
  </li>
</ul>

## Project Ideas: 
The program's functions are divided into three steps:
<ol>
  <li><b>Step 1: Getting user input and image pre-processing:</b></li>
    <ul>
      <li>Getting user’s input on the image name, the desired export format (pdf or png) and the way to initiate the centroids (random: generate a random set of centroids // in_pixel: the set of centroids is selected from the pixels available in the image)
      </li>
      <li>
        Converting the image from an Image object to a numpy array then reshaping it to (height*width, num_channels). The initial shape of the array is stored for the reestablishment of the image after we finish processing with the K-Means algorithm
      </li>
    </ul>

  <li><b>Step 2: K-Means algorithm implementation</b></li>
  <ul>
      <li>Depending on the number of clusters and the way of initiating the centroids, an array containing the centroids is created, in which a centroid contains information of 3 color channels: R (Red), G (Green), B (Blue) respectively.
      </li>
      <li>
        Calculate the distance from each pixel to the centroids, select the one with the smallest distance and and save the centroid’s index in the labels array in the
position equivalent to the pixel’s position in the image.
      </li>
      <li>
        For each centroid, update the centroid by calculating the mean of the pixel vectors belonging to that centroid based on the labels array.
      </li>
      <li>
        <b>Check for stopping conditions:</b> if the number of iterations exceeds the max_iter parameter or the difference in value is acceptably small considering two sets of centroids created in two consecutive iterations, then the algorithm stops and returns centroids and labels array; else it returns to Step 2 and carry on with the new centroids.
      </li>
    </ul>

   <li><b>Step 3: Image reconstruction and export of image file in the desired format</b></li>
   <ul>
      <li>From centroids and labels arrays, for each index in the labels array, we assign the centroid with the corresponding index. The resulting array would then be
reshaped in to the initial shape stored earlier and then converted back to an Image object.
      </li>
      <li>
        Based on the information about the image’s name and desired export format, the image is then created and saved in the same working directory.
      </li>
    </ul>
</ol>

## Results Demonstration:
![image](https://github.com/DanielPham311/Image_Blurring/assets/95340260/e214b519-b709-435d-8dd2-c15c58b936a0)
![image](https://github.com/DanielPham311/Image_Blurring/assets/95340260/2f079d54-774a-49fd-aed8-5d4fd8c1bb83)
![image](https://github.com/DanielPham311/Image_Blurring/assets/95340260/4cc852b6-7705-41d4-9863-195961e15216)
![image](https://github.com/DanielPham311/Image_Blurring/assets/95340260/bdb79224-a703-457f-8c9e-7767f0b124cb)
![image](https://github.com/DanielPham311/Image_Blurring/assets/95340260/48ba74fc-beb3-40fc-9024-f265878b5ffc)

As you guys can see, the images get clearer and clearer as we use more clusters. P/S: I'm a Peaky Blinders fan. Anyways thank you for visiting 😸





