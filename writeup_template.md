# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg 

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied a gaussian kernel with filter size 5, to smooth the image and improve 
robustness to noise. Next I applied the Canny edge detection algorithm followed by a Hough transform to get a clear outline of the lines drawn in red on the image. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by clustering in the space of lines. Since horizontal and vertical lines won't
be lane lines we are interested in, I excluded them. This enabled me to work in the space of lines without switching to polar representation of lines. For lines with positive slopes, I calculate
the average slope and intercept and picked a line that was closest to the average slope and average intercept. Closeness was measured using Euclidean distance in the space of lines. I repeated the same thing for lines with a negative slope. This gave me two representative lines one for the left, and one for right lane.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
