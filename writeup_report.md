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

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I converted the images from RBG to HSV, by which I was able to filter on colors I wanted, such as white and yellow, in case the color of road is complicated like it in "Challenge" video, and I combined grayscale images with filtered images, next I dealt with the combined images by Gaussian Filter, and put the blurred images into Canny Edge Detection, once I had the images of edges, all I need to do is preparing a region of interest for next step, at last, the outputs of last step were transformed through Hough Transformation.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by seperating left_lines and right_lines through their different slope, getting rid of those lines which slope are far away from the mean value, turning lines array into points array, fitting these points with np.polyfit(), and drawing one left line and one right line on lanes.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when it works at night.

Another shortcoming is that it can not deal with curve roads.

The third sortcoming is that how it would work when there are more objects on the roads, such as cars, human or animals.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to add methods to detect lanes no matter they are strait or curve.
