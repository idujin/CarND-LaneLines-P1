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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I blured the grayscale image. Next, I found the edges of the image using Canny and set ROI in trapezoidal shape at bottom of the image. Finally, I made the lines using Hough transform and drew the lines.   

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by fitting the lines which is found in previous process.
At the fitting step, I divided the lines into two groups according to the sign of slope to seperate right and left line.




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when wrong lane is found.
In that case, the wrong lane affects the line fitting function, draw_line(), and the result of draw_line would not be the true lane.   
Another shortcoming could be happen when there is no lane for a while. 
In that case, the lane could not be estimated in this algorithm. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to set tolerance between mean of the line slopes and current slope at the fitting stage. By removing the points with a slope outside tolerance at the fitting stage, the effect of incorrect line on the fitting function could be minimized.  

Another potential improvement could be to use temporal information of the image. In this algorithm, Only one frame is used for estimating lane. However, if the estimated lanes of the past frames are considered, there would be some improvement when the lane does not exist on some frame. 

