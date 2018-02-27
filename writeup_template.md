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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...


right_line_x=[]
    right_line_y=[]
    left_line_x=[]
    left_line_y=[]
    
    for line in lines:
        for x1,y1,x2,y2 in line:
            with np.errstate(divide='ignore', invalid='ignore'):
                slope=(x2-x1)/float(y2-y1)
                center_of_line=(x1+x2)/2
            #print(slope, center_of_line)
            if (0.5 < slope < 2.5)and center_of_line>horizontal_center:
                right_line_x.append(x1)
                right_line_x.append(x2)
                right_line_y.append(y1)
                right_line_y.append(y2)
                
            elif (-0.5 > slope>-2.5) and center_of_line<horizontal_center:
                left_line_x.append(x1)
                left_line_x.append(x2)
                left_line_y.append(y1)
                left_line_y.append(y2)
    
    
            cv2.line(img, (x1, y1), (x2, y2), color, thickness)