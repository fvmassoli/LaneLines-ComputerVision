#**Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

### Reflection

The pipeline is divided in six major steps:

1. conversion of the image to the gray scale.
2. application of a gaussian kernel in order to smooth the noise. After several trials, a kernel size equal to 7 resulted a good choice. A kernel of size 9 was already too high since it caused some lost in the line recognition.
3. application of the cv2.Canny(...) method to the image in order to get the edges. The application of the gaussian smearing helps during this phase since it cleaned up the image from all the "smaller edges" (noise). This enhances the sensitivity of the canny function to the edges that correspond to real lines in the image.
4. application of the mask to the canny image in order to retain only lines inside the ROI
5. conversion of the edges into lines by their mapping into the Hough parameter space. In order to draw continuos lines to recognize the lane liens I modified the draw_lines() such that it evaluates the coefficients of a line from two points of the given line itself.
6. overlay the detected lane lines to the original image. The helper function weighted_img(...) overlays the lines on the original image with a specific tarnsparenncy. 

The results from each of the previous steps are shown in the following pictures:

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/gray_scale.png "Grayed image")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/blur.png "Filtered image")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/edges.png "Edges")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/edges_roi.png "ROI")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/lines.png "Lines")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/final_result.png "Pipeline final result")

###2. Identify potential shortcomings with your current pipeline

A potential shortcoming would be the use linear regression to extrapolate the line coefficients

###3. Suggest possible improvements to your pipeline

A potential improvement could be to tune the pipeline in order to recognize bend lines (actually I tried but after the first time the notebook kernel started to crash everytime and I have been unable to test the code again)
