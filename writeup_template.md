## Project: Perception Pick & Place

the numbers within the brackets mean the corresponding code lines in project_template.py

#### 1. Complete Exercise 1 steps: (53 -> 100) 

1- Downsampled my PCL cloud using voxel grid filter with leaf size 0.01m

2- apply 2 path-through filters one in 'z' axis and, the other in 'y' axis, the 'z', and 'y' axes' parameters were as follow for 'z' min = 0.6 and max = 1.1, for 'y' min = -0.45, max = 0.45 I picked these parameters such that just the table in front of the robot appear

3- apply "Statistical Outlier Filter" with, 

3.1- the number of neighbors to analyze for each point equal to 50. 

3.2- standard deviation multiplier to 1, setting this parameter to a smaller number was giving me a better cloud but it can remove some items e.g. in test 3 it excludes the glue.

4- Perform RANSAC plane fitting to identify the table with max distance threshold to 0.01


#### 2. Complete Exercise 2 steps: (102 -> 135) 

1- apply Euclidean clustering on the objects I extract from RANSAC Plane Segmentation with parameter cluster tolerance 0.02, min cluster size 50 setting this to higher number was causing the test 3 world to fail to cluster the glue, max cluster size 1500 

2- Create Cluster-Mask Point Cloud to visualize each cluster separately (default code)

#### 3. Complete Exercise 3 Steps: (136 -> 168)

sensor_stick package url :: https://github.com/JafarAbdi/sensor_stick

1- Capture training examples I picked the number of examples to be 100

2- training a model after filling features.py using train_svm with kernel = 'rbf' because in my case it gives a better model

![](https://github.com/JafarAbdi/RoboND-Perception-Project/blob/master/misc_img/accuracy-1.png)
![](https://github.com/JafarAbdi/RoboND-Perception-Project/blob/master/misc_img/accuracy-2.png)

3- predict the objects in cloud_objects 

### Pick and Place Setup

#### 1. For all three tabletop setups (`test*.world`), perform object recognition, then read in respective pick list (`pick_list_*.yaml`). Next construct the messages that would comprise a valid `PickPlace` request output them to `.yaml` format.

1- test 1 world,

video :: https://www.youtube.com/watch?v=oqSZwFTcNBs

yaml file :: https://github.com/JafarAbdi/RoboND-Perception-Project/blob/master/output_1.yaml

1- test 2 world, 

video :: https://www.youtube.com/watch?v=bwX_P-74qa0

yaml file :: https://github.com/JafarAbdi/RoboND-Perception-Project/blob/master/output_2.yaml

1- test 3 world,

video :: https://www.youtube.com/watch?v=UsrrXHhaEF8

yaml file :: https://github.com/JafarAbdi/RoboND-Perception-Project/blob/master/output_3.yaml

My thoughts on my code and what next ::

1- I think my code isn't optimal as you can see in the test 3 video sometimes the glue disappear and it can't detect very small objects

2- my plan is to continue and try to finish the optional challenges.


