# **Finding Lane Lines on the Road**

## **Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 10 steps and an optional step:
1. Convert the input image into grayscale.
2. Apply a gaussian blue kernel.
3. Apply histogram equalizater.
4. Apply Canny edge detection.
5. Create Region for interest for the lane.
6. Clip the Canny image using ROI image.
7. Use Hough transform to get lines on the image.
8. Filter the output lines:
    i. Split the lines to left and right.
    ii. Neglect near horizontal lines using line slope.
9. Average the left and right lines independtly.
10. `Optional` for videos use `deque` to store a window of five slopes and use the average of the window.
11. Draw left and right image using averged sloped with ROI `Y` values.

Apply Histogram equalizater before `canny()` using `cv2.equalizeHist`.

For 8, 9, 10 points, I add a new function called `filter_lines()`.

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

- Change of the light can easy saturate the pixels value.
- The slope is not accurate.
- Missing of side lines is not handled.
- Snow or desert can easy hide the lines.
- Preformance of the pipeline can limit the speed of the car.

### 3. Suggest possible improvements to your pipeline

- use Adaptive histogram to handle the lighting.
- use auto exposure for lighting problem.
- use last slope if current slope is missing.
- May use `kalman filter` for missing slope.

