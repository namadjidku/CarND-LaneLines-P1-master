# **Finding Lane Lines on the Road** 

---


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteRight.jpg "Lane lines"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied Gaussian Smoothing to the grayscaled images with kernel size equals to 9. At the next stage I used Canny transformation to detect edges, after that I did region selection in the shape of trapezoid to remove not relevant to the lane lines edges. Last step was using the Hough space transformation to identify the lane lines.  

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by averaging the coordinates of the line segments identified by the Hough space transformation. The line segments were classified based on positive or negative slopes. After finding the averaged begining and end points, I used np.polyfit to find the slope and intercept of the line going though these averaged points.   


![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming is that we adjust shape of the mask almost manually to remove edges we do not need to consider.

Another shortcoming is that if a lane line is curved, then it cannot be extrapolated with a polynom of first degree.

The last shortcoming is that in order to consider small parts of the lane lines (when the lines are doted) we decreased the param min_line_len, which led to identifying more edges including the horizontal ones we do not need.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to using a polynom of second degree to extrapolate curved lane lines. 
