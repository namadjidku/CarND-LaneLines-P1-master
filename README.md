# **Finding Lane Lines on the Road** 

---


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteRight.jpg "Lane lines"
[image2]: ./test_images_output/solidWhiteCurve.jpg "Lane lines"
[image3]: ./test_images_output/solidYellowCurve.jpg "Lane lines"
[image4]: ./test_images_output/solidYellowCurve2.jpg "Lane lines"
[image5]: ./test_images_output/solidYellowLeft.jpg "Lane lines"
[image6]: ./test_images_output/whiteCarLaneSwitch.jpg "Lane lines"


The detection pipeline consists of 5 steps. First, the images are converted to the grayscale and smothed using Gaussian Smoothing with a  kernel of size 9. At the next stage the Canny edge detection was applied. After that to remove not relevant to the lane lines edges, we masked the images with a mask of trapezoidal shape as we assume that the lines are located in the lower half of the images. At the last step, we used Hough space transform to get lane lines segments. The function draw_lines() averages the coordinates of these line segments for both left and right lines (segments were classified based on the positive or negative slopes). After finding the averaged begining and end points, np.polyfit was used to find the slope and intercept of the line going though these averaged points.   

Detected lines (white)     |  Detected lines (yellow) |  Detected lines (yellow)          
:-------------------------:|:------------------------:|:----------------------:
![alt-text-1][image1]      | ![alt-text-2][image4]    | ![alt-text-3][image3]   
![alt-text-1][image2]      | ![alt-text-2][image5]    | ![alt-text-3][image6]   
