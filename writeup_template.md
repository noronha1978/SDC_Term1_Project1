# **Finding Lane Lines on the Road**

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./output_images/01_grayscale.png "Grayscale"
[image2]: ./output_images/02_gaussian_blur.png "Gaussian Blur"
[image3]: ./output_images/03_canny_edge.png "Canny Edge"
[image4]: ./output_images/04_roi_image.png "Region of Interest Applied"
[image5]: ./output_images/05_houghxform_lines.png "Hough transform for edge segments"
[image6]: ./output_images/06_final_merged_image.png "Final merged image"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps.

* First, I converted the images to grayscale
  ![Figure 1:][image1]
* Then I applied the gaussian blur
  ![Figure 2:][image2]
* Then I ran it through a canny edge detector
  ![Figure 3:][image3]
* Then I filtered out a region of interest
  ![Figure 4:][image4]
* Then I ran a hough transform (probabilistic)
  ![Figure 5:][image5]
* After which I then overlay the resulting image from step 5 onto the original image
  ![Figure 6][image6]

#### draw_lines function explanation
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:

1. dividing the line segments on the left and right based on their slopes.
2. Based on whether the slope was positive or negative I classified the points as right or left points.
3. Then I fit a line through the points using np.polyfit
4. Then I calculated the intersection of the lines within in the region of interest.


## *NOTE:*

1. Output images are in the ./output_images folder

2. Output videos are in the ./output_videos folder



### 2. Identify potential shortcomings with your current pipeline

The algorithm that I applied was simple - fitting a line through the points.
What I could have tried that might have helped was to maybe see if they could be calculated off the centroids of the line segments instead.
There were other variations that were more advanced that I explored but did not get a chance to implement


### 3. Suggest possible improvements to your pipeline

My pipeline currently is sensitive to noisy inputs and I can stabilize it further by using

1. denoising the input better
2. choosing color thresholds to pick out yellow
3. accounting for shadows
4. more advanced segment fitting techniques
