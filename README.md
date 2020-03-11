# **Finding Lane Lines on the Road** 

---


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteRight.jpg "Lane lines"
[image2]: ./test_images_output/solidWhiteCurve.jpg "Lane lines"
[image3]: ./test_images_output/solidYellowCurve.jpg "Lane lines"
[image4]: ./test_images_output/solidYellowCurve2.jpg "Lane lines"
[image5]: ./test_images_output/solidYellowLeft.jpg "Lane lines"
[image6]: ./test_images_output/whiteCarLaneSwitch.jpg "Lane lines"


### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied Gaussian Smoothing to the grayscaled images with kernel size equals to 9. At the next stage I used Canny transformation to detect edges, after that I did region selection in the shape of trapezoid to remove not relevant to the lane lines edges. Last step was using the Hough space transformation to identify the lane lines.  

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by averaging the coordinates of the line segments identified by the Hough space transformation. The line segments were classified based on positive or negative slopes. After finding the averaged begining and end points, I used np.polyfit to find the slope and intercept of the line going though these averaged points.   

Detected lines (white)     |  Detected lines (yellow) |  Detected lines (yellow)          
:-------------------------:|:------------------------:|:----------------------:
![alt-text-1][image1]      | ![alt-text-2][image4]    | ![alt-text-3][image3]   
![alt-text-1][image2]      | ![alt-text-2][image5]    | ![alt-text-3][image6]   
