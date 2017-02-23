#**Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

### Reflection

The pipeline is divided in six major steps:

1. conversion of the image to the gray scale.
2. application of a gaussian kernel in order to smooth the noise. After several trials, a kernel size equal to 7 resulted a good choice. A kernel of size 5 was already enough for the pictures. For video I set the kernel size at 7 due to the higher level of noise.
3. application of the cv2.Canny(...) method to the image in order to get the edges. The application of the gaussian smearing helps during this phase since it cleaned up the image from all the "smaller edges" (noise). This enhances the sensitivity of the canny function to the edges that correspond to real lines in the image.
4. application of the mask to the canny image in order to retain only lines inside the ROI
5. conversion of the edges into lines by their mapping into the Hough parameter space.
6. overlay the detected lane lines to the original image. The helper function weighted_img(...) overlays the lines on the original image with a specific tarnsparenncy. 

The results from each of the previous steps are shown in the following pictures:

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/gray_scale.png "Grayed image")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/blur.png "Filtered image")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/edges.png "Edges")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/edges_roi.png "ROI")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/lines.png "Lines")

![alt text](https://github.com/fvmassoli/fem-CarND-LaneLines-P1/blob/master/outputs/final_result.png "Pipeline final result")

Regarding the step 5) I modified the draw_lines() method in order to draw the lines on the pictures and on the video. Following the suggestions given in the udacity tutorial on slack and from some hints found on the web I evaluated for each sample of lines coming from the Hough function an average value for the slope and intercept. Right and left lines are distinguished from the value of the slope (not averaged).
In order to properly take into account the difference characteristics among picture and video I rewrote the draw_lines() method. In particular the in the video I evaluated the "on-line average" i.e. the line end points are evaluated by averaging among the last ten available values of line points themselves.
The ptm parameter set the number of points to consider in order to evaluate such average points.

###2. Identify potential shortcomings with your current pipeline

A potential shortcoming would be the inability to recognize the bend lines.

###3. Suggest possible improvements to your pipeline

A potential improvement could be to tune the pipeline in order to recognize bend lines.
Another improvement would to use some machine learning to tune the parameters that I used as input for the Canny and Hough functions.
