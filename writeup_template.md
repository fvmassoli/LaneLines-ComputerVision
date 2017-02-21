#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

The pipeline is divided in eight major steps:

##1) Identification of the mask vertexes. These are points that confine the polygon describing the image ROI. 

##2) Representaion of the image in the gray scale by calling the helper method grayscale(image) where the argument "image" is the original input image.

##3) Applciation of a gaussian kernel of size 7 in order to smooth the noise. 

##4-5) Call to the helper methods canny(...) and region_of_interest(...) that find egdes into the image and select the ROI, respectively, based on the vertexes defined in ##1).

##6-7) Call to the methods hough_lines(...) and weighted_img(...) that find lines in the image and overlay them on the original image with a specific tarnsparenncy. 

In order to draw a continuos line I modified the draw_lines() such that it evaluaes the coefficients of a line from two points of the given line itself.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][outputs/gray_scale.jpg]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to use linear regression to extrapolate the line coefficients

Another potential improvement could be to tune the pipeline in order to recognize bend lines (actually I tried but after the first time the notebook kernel started to crash everytime and I have been unable to test the code again)