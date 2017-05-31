# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[original]: ./report/original.jpg "Original image"
[gray]: ./report/gray.jpg "Gay image"
[edges]: ./report/edges.jpg "Edges"
[masked_edges]: ./report/masked_edges.jpg "Zone of interest"
[line_img]: ./report/line_img.jpg "Lines on an empty image"
[line_img_extrapolated]: ./report/line_img_extrapolated.jpg "extrapolated lines on an empty image"
[lane_lines]: ./report/lane_lines.jpg "Original image with lane lines added"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. given images like the following

![alt text][original]

1. First, I converted the images to grayscale

![alt text][gray]

2. Then I applied gaussian smooth on the gray image, and...

3. I used edge detection to extract the edges from the image

![alt text][edges]

4. I delimitted a zone of interest on the image

![alt text][masked_edges]

5.1. I used hough transformation to extract the lines from the zone of interest and draw them on en empty image

![alt text][line_img]

5.2. I extrapolated the extacted lines uning linear regression before drawing them

![alt text][line_img_extrapolated]

6. I supperposed  the image with lines to the original image

![alt text][lane_lines]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the car reaches a curve. The linear regression might behave
poorly.

Another shortcoming could be what would happen when the car reaches an obstacle (another car in front), the current version
cannot distinguish lanes from obstacles


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to improve interpolation to fit curves. I will for example try to use [polyomial regression](https://docs.scipy.org/doc/numpy/reference/generated/numpy.polyfit.html) instead of linear regression.

Another potential improvement could be to try to elimiate potential obstacles from lane detection. I will for example
elimiate the zone staight in front of the car from the interest zone.
