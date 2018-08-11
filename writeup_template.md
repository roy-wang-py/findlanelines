# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
1.Make a color mask, which will select white & yellow.
2.Convert the image to grayscale.
3.Make gaussian_blur.
4.Edges detected with cv2.canny.
5.Make a region mask, which select the special region contained lane lines.
6.Get lines using HoughLinesP.
7.write lines at original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. Lines are divided into two groups using slope, left with slope less then -0.3, and right with x axis greater than 0.3.To drop some noise , i select slope threathold -0.3 & 0.3 instead of 0.  Then fit left & right lines with Least_squares.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


1. Wrong lines displayed when on the curve. 

2.Crosswalk may be identified as lane lines.

3.While my pipeline did not work well when trying challenge.There are too much noise in challenge images.

4.Night would be another challenge.

5.Other vehicles which are white or yellow would be noise.


### 3. Suggest possible improvements to your pipeline

1.Function curve_fit could help when on the curve, sometimes straight lines couldn't fit well.

2.RGB did not walk well when lighting change, HSV may be helpful.

3.Region selected could be improved.
