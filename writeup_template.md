# **Finding Lane Lines on the Road** 


### Goal
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

![alt text][image1]
---

### Reflection

### 1. Pipeline

My pipeline consisted of 5 steps as mentioned below:

1. First, I converted the images to grayscale.

[//]: # (Image References)

[image2]: ./writeupImages/01grayscale.png "Grayscale"

![alt text][image2]

2. Then I apply gaussian blur to the image and pass it through a canny edge detector to identify the edges in the images.

[//]: # (Image References)

[image3]: ./writeupImages/02canny.png "Canny"

![alt text][image3]

3. The output of the canny edge detector is passed through a region of interest filter which selects only the area where lanes might be and applies an image mask to that.

[//]: # (Image References)

[image4]: ./writeupImages/03regionofinterest.png "Region of Interest"

![alt text][image4]

4. This image is then passed to a hough line filter which applies a hough transform on the input image and figures out the lines in the hough space returning both hough lines and an image which has lines drawn. The lines are drawn by using draw line function which is modified to use the slope and intercept equation of line to figure out the left and right lanes

[//]: # (Image References)

[image5]: ./writeupImages/04hough_lines.png "hough lines"

![alt text][image5]

5. Last but not the list I add the image with hough lines to the original image with the help of cv2.addWeighted function

[//]: # (Image References)

[image6]: ./writeupImages/05weightedimage.png "Weighted Image"

![alt text][image6]


### 2. Shortcomings of Pipeline

I think one of the major short coming of this pipelines is it's inability to deal with the curved roads. 
With the introduction of curvature the region of interest changes and this algorithm is not capable of handling that.
Also with the addition of curvature the lane lines also form a curvature and since this pipeline extrapolates lane lines
using the straight line model, it limits it's abilti to detect the curved lane lines


### 3. Possible Improvemen to the Pipeline

Utilizing a lane line model which is able to consider the curvature of lane lines will help a lot in imporving the pipeline.
Also utilizing the camera parameters and feature matching algorithms like SIFT and SURF could provide a potential improvement to the algorithm.
