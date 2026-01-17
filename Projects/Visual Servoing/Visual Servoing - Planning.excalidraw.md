---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Purpose:  ^MYCXjLgz

Skills learnt:  ^GFD18gJf

Step-by-step plan: ^W95lacO1

learn how a manipulator can avoid occlusion in harvesting through object detection using depth camera and path planning ^x5PlBKAY

path planning (MoveIt2), object detection ^5RQt3G0a

Spawn a manipulator with gripper and depth camera and a mango as an object of interest ^NqcHOV5M

Spawn an apple (differentiate based on color) and an orange (differentiate based on shape) and apply object detection to identify the mango ^CaUmdNrU

Spawn a basket. Make the robot pick the mango and drop it in the basket ^WqO2blom

Add obstacles like leaves (that the manipulator can go through) and trunk (that the manipulator have to avoid) to get to the mango ^xIYV8YWJ

Spawn a wheeled robot at the bottom so it can move around to pick all the mango on the tree ^G15ZEtZV

Convert pixel coordinates (u, v) from camera to 3D coordinates (x, y, z) from the depth data ^OlxKmlGV

1. Visualize the arm with URDF in RViz //
https://automaticaddison.com/create-and-visualize-a-robotic-arm-with-urdf-ros-2-jazzy/#Add_the_Meshes /
2. Add arm to gazebo
3. Render a mango as an object in Gazebo ^Jy6S5OCX

Finish MoveIt2 tutorial // ^yqfRDLdH

Attach depth camera at the gripper ^GRd8irzz

Planning Scenes Service ^ifoeV7Ij

In ^YOmPJ3RI

* Estimate surface normals *
- Each point in the cloud: estimate normal by 
fitting a plane to its k-nearest neighbors
= setKSearch(normal_estimation_k)
- Store computed normals, index match with the
individual point clouds ^tfJNWxxa

* Identify support surface candidate *
- Differentiate floor and walls with vertical normal
- Group points with ~ vertical normal
- Do Euclidean clustering on grouped points to get
support surface candidate; store candidates ^NH2xwJvB

[[Clustering Method]] ^CLcAczwY

* Process each candidate *
- RANSAC to fit plane model
- Accept model if all conditions are true:
  + If plane is in cropped area (enable_cropping == T)
  + plane_center.z < z_tolerance (close to ground?)
  + dot_prod(plane_normal, up_vector) > angle_tolerance
(acceptable tilt) ^LLz0s5Th

computed normals ^eRbJQ9uu

Clusters ^XwmkNZSA

[[Model Fitting Algorithms]] ^Fu9AhR2r

* Find best fitting plane as support surface *
- Sum factors below with weighted scoring:
  + Inlier count: Prefer higher inlier_count = more 
supporting points
  + Plane size: area of 2D bounding box of inlier points
projected onto plane; Prefer larger planes
  + Distance to z=0: z_distance = |plane_center.z|
  + Orientation: higher dot_prod(plane_normal, up_vector)
- Select plane with highest sum ^Yk1QkAXT

Fitting planes ^ehEjnwx0

Out ^9mL37bSC

segmentPlaneAndObjects ^hmaAd9Vo

* Create point clouds*
- Extract all inliers into support_plane_cloud
- Add to objects_cloud if:
  + Above best_plane_model
  + In crop boundaries (if enabled) ^0PYJHyLR

- best_plane_model
(for object
segmentation) ^YqXrU2Yt

best_plane_model ^W2fTocv7

- support_plane_cloud
- objects_cloud ^W5jMUMK8

plane_segmentation.cpp ^8J19Ej4o

In ^tPsgOK03

Measured
point cloud ^kjuj0sgv

Out ^YqQhPCyi

estimateNormalsCurvatureAndRSD 
for each point p: ^tOo1Ize6

normals_curvature_and_rsd_estimation.cpp ^jmQgT6lG

* Find neighbors *
- Form neighborhood of p with k_neighbors (input param) points
- Boundary point if #neighbors < k_neighbors 
=> Adjust neighborhood size to smaller value down to ^qYyIKbBk

* Roughly estimate normal vector as starting point and fallback *
- Capture how spread out is the neighborhood with Principal Component Analysis:
 big eigenvalue = more spreadout
- Smallest eigenvalue is the normal value estimate ^zBAUqGij

Neighborhood ^4kGKI5Dn

* Fairly estimate normal vector with MLESAC *
- Start with the rough normal vector estimation to refine estimation
- Fallback to rough estimation if MLESAC fails ^tXPQFkiv

[[Principal Component Analysis]] ^rp35BrCb

Rough normal estimation ^YCJfZpQO

Questions for deep dive ^NmevsYIG

1. Why do we need to find the uncertainty with covariance matrix after MLESAC? ^feECCpos

* Find weighted covariance matrix for model's uncertainty *
- Inliers: weight = 1
- Others: weight = 
d_j: Euclidean distance between the query point and neighbor j
mu: average distance of all neighbors in the local neighborhood.
- Reduce influence of outliers by giving them less weight ^YQVvz5xy

Fair normal estimation ^JMqZwXvQ

* Accurate estimate normal vector with PCA on weighted matrix *
- Smallest eigenvalue is the normal value estimate ^JmbVXK44

Weighted covariance matrix ^FfuXTcmp

* Find curvature value with formula (  is normal estimate) * ^EnwYxrMm

Notes to fill in afterwards ^gk6Hv66O

1. Surface variation based on the eigenvalues
2. Radius-based Surface Descriptor (RSD) ^ctxSTD9K

where ^Jsp4uJ4k

Accurate normal estimation ^YAKRH9ug

* Calculate Radius-based Surface Descriptor (RSD) *
- Use pcl::RSDEstimation to find min & max surface radius 
that fit the neighborhood
- Determine if point belongs to linear or circular surface ^rJGXUFhv

Measured
point cloud ^yrBaH1kh

* Generate output point cloud with *
- The original XYZ coordinates
- The RGB color information
- The estimated normal vector for each point
- The estimated curvature value for each point
- The RSD values (r_min and r_max) for each point ^zUbKayNi

Calculated
point cloud ^UzMXZTz9

XYZ & RGB ^HojWjMwS

Normal estimate ^Vtw5sfZr

Curvature value ^dCNElV8k

RSD values ^oW8lPjTL

cluster_extraction.cpp ^3oIgHa9V

* Create KdTree object for efficient 
nearest neighbor searches * ^QDkGguQH

* Extract normals from the input cloud into 
a separate pcl::PointCloudpcl::Normal object * ^XcDdSZvB

Process ^eS1VW7dv

* Create RegionGrowing object with parameters:
- Min & max cluster size
- # nearest neighbors to consider
- Smoothness threshold (angle threshold for neighboring normals)
- Curvature threshold ^u8c0zSPh

KdTree object ^qJrVpUFO

Normal ^ZvSrdKEM

* Execute region growing algorithm to extract clusters * ^LRE6RYtb

RegionGrowing object ^8FlNZKl2

* Output extracted cluster with: *
- A new point cloud
- Copy points from the input cloud to the new cluster cloud based on the extracted indices
- Set the cluster’s width, height, and is_dense properties ^nkzBgv0s

Questions for deep dive ^9bJHRKcU

1. What is the role of extracted indexes? ^CQmu9pbK

Notes to fill in afterwards ^qRN3ArJS

1. Region Growing algorithm ^RgnNc4Bz

Extracted clusters ^kaLj1dnV

Additional Features ^sEDhv94D

The implementation calculates and logs various statistics for each cluster:
- Cluster size
- Centroid coordinates
- Average RGB color
- Curvature statistics (min, 20th percentile, average, median, 80th percentile, max)
- Average RSD (Radius-based Surface Descriptor) values ^kD0PyKqH

Key points ^CtvFebO0

- Purpose: Reduce the search space for subsequent segmentation by grouping nearby points
- Note: In cluttered scenes, objects that are touching or very close may end up in the same cluster
- Uses both geometric properties (normals) and curvature information for clustering
- Smoothness threshold is converted degrees -> radians ^CfemCCGP

Out ^vpiTWANL

Extracted Clusters ^pgywC5nV

Problems ^82hxYCjM

1. How to define coordinates if the camera is 
constantly moving? ^CExsyB2X

object_segmentation.cpp ^9hUavjjx

Outer Loop: for each point cloud cluster ^WwnaCynf

Questions for deep dive ^MFKbctNh

1. What is the role of extracted indexes?
2. For a point cloud, does it know it iterate until it finds the best shape? ^PHHK32j5

Notes to fill in afterwards ^XXv7JhYZ

1. Region Growing algorithm ^JaBJlinZ

Key points ^dJKLTQpo

- Purpose: Reduce the search space for subsequent segmentation by grouping nearby points
- Note: In cluttered scenes, objects that are touching or very close may end up in the same cluster
- Uses both geometric properties (normals) and curvature information for clustering
- Smoothness threshold is converted degrees -> radians ^Bggmd75F

* Project cluster onto the surface planes *
- Project each point onto the plane (in this case z=0; by removing z coordinate) & maintain mapping to the 3D point index
- Set properties of the projected cloud:
  + width: # points/ row
  + height: # rows; 1 = unorganized (for standard KD-Tree search methods; > 1 for faster neighbor searches)
  + is_dense: true = no Nan/ Inf value; skip validity check
- Create copy of projected point cloud to run different inner loop iterations ^36kvkpAi

* Initialize 2 parameter spaces *
- Measure range of projected points & dimension for Hough space: 
- Create a vector for models for Hough transform using HoughBin struct: 
  + Line: rho, theta, votes, & inlier count
  + Circle: center_x, center_y, radius ^jjppQWCr

projected cluster ^TnC82RVV

** Inner loop (repeated num_iterations times w/ new copy of projected cluster every time): RANSAC model fitting ** ^lQjefEuT

Parameter spaces ^mqRlR5ZA

* Model fitting *
- Line: fitLineRANSAC(); Circle: fitCircleRANSAC()
 ^vgq2CL6F

Functions ^iHPy2E92

fitLineRANSAC() ^5yoSkAiG

- Initialization:
  + Setup output containers (inliers, coefficients)
  + Random device & uniform distribution generator for unbiased sampling
- RANSAC loop:
  A. Hypothesis Generation (Random Sampling)
    1. Select 2 integer indices 
    2. Check if they are distinct (if not, skip to next iteration)
    3. Compute coefficients (a, b, c) that pass through the 2 points with
formula                               then normalize

  B. Verification
    1. Initialize inlier set
    2. Loop through every point and calculate distance from a point to the
line found in A3.
    3. distance < threshold => inlier & store original index
  C. Model Update: choose model with most inliers (vote) ^n5evVv0H

fitCircleRANSAC(): similar but with 3 major differences ^q3MZjRJ0

1. Sample 3 points
2. Math:
  - fitCircle(): linearized version of the circle equation
  - distanceToCircle(): 
3. Sanity check:  ^toIJvltR

* Filter inliers *
- Line: fitLineInliers(); Circle: fitCircleInliers() ^v5GqZSTD

fitCircleInliers() ^6DI6EM6v

1. Euclidean Clustering: 
- Group inliers into clusters
- Accept models with max 2 clusters (= 2 circles/ visible arcs of a cylinder)
2. Heigh Consistency (only 2 clusters): if height diff < height_tolerance
- True: move on; False: return empty PointIndices
3. Curvature Filtering: skip points w/ low curvature
4. RSD Filtering: skip points w/ |r_min - circle_radius| > radius_tolerance
5. Surface Normal Filtering: skip points w/ angle > normal_threshold ^dQC5Vf7B

fitLineInliers() ^NyrfEhnO

1. Euclidean Clustering: accepts only 1 cluster
2. Curvature Filtering: skip points w/ high curvature ^aOqN3t7O

fitted models ^lojWAUpb

* Model validation *
- For both circle and line: keep model if # remaining inliers > inlier_threshold
- Identify model: compare # remaining inliers between circle and line; keep the type with higher count
- If there is no valid model, quit inner loop
- Create data structure for the indices of the inliers from the valid models ^JIVVTkS1

filtered models ^W1ZOWAVo

* Add model to Hough Space *
- Circle: 
  + Calculate indices for circle Hough space and make sure they are within bound 
  + Add a vote to the 3D Hough space (center_x, center_y, radius bins)
- Line: Add the line model (rho, theta, votes, inlier count) to the line models vector ^4ks9U0DY

* Remove inliers & loop back to inner loop *
- Remove the inliers of valid models from the working point cloud and continue the inner loop until 
insufficient points remain or no valid models are found. ^qiOh7uGI

Valid model ^IdM6dOJc

data structure of inliers ^iLCl7Wkr

* Cluster Parameter Spaces * ^gKpmogEM

clusterLineModels() ^6h2NaC6z

1. Clustering: iterates through every line model; for any unprocessed model,
it is chosen as the fixed element (in this case index `i`). 2 lines are 
clustered if               and 
  -    : difference in their perpendicular distance to the origin
  -                                : handles the cyclical nature of angles;
ensures that a line at  is correctly grouped with a line at 
2. Aggregating Votes: Merge neighbor into cluster
- Add : `votes` & `inlierCount` to cluster's total
- Store   and   in list to process later
3. Computing Representative Parameters
- Sorts   and   then selects the median for each (least affected by outliers)
4. Sorting by Confidence: sorts all the resulting clusters in descending order 
based on `votes`. Index `0` is the best hypothesis. (sorted list is HoughBin) ^4Nu2lhFj

## Element Links
sZg69Ply: https://www.youtube.com/playlist?list=PLNWNEEf8BvG6lbOxH9AiXNetYcVgcJeWk

ITaf5iOc: [[Parameter Spaces#Hough Space]]

CLcAczwY: [[Clustering Method]]

Fu9AhR2r: [[Model Fitting Algorithms]]

rp35BrCb: [[Principal Component Analysis]]

## Embedded Files
55aa498380109ed6e2b7f0a2ae94e65da78086e3: $$e^{-\frac{d_{j}^2}{\mu^2}}$$

8fc16a6e3bc0d99827cefb2ce311146211deb3ee: $$\frac{\lambda_0}{\lambda_0 + \lambda_1 +\lambda_2}$$

6e4553c9a60d4ae18bdedcdbf3ac443665008532: $$\lambda_0 \le \lambda_1 \le \lambda_2$$

0299dd9ea862870dc89f50c31ecb99e7aeba9791: $$\lambda_0$$

57bd3386328b60794804d7692fc02f7191351c11: $$houghMaxDistance = projectedXRange^2 + projectedYRange^2$$

c520f92652f044d0f7fbece166815f671a02ad0d: $$ax + by + c = 0$$

7bf763d48b4bb0dc8eca027a9cb2781aa3d3ef39: $$a = y_2 - y_1$$

136c176cee9d106c8b134b2637e92073d2e80eb4: $$b = x_1 - x_2$$

a863f92ce0ae73b1c29c5398632e5f342225594c: $$c = x_2y_1 - x_1y_2$$

3af93051ac1aa316c15812513d8a5934eb8702f7: $$Distance = \frac{|ax_0 + by_0 + c|}{\sqrt{a^2 + b^2}}$$

f7e60fbd5080a132c92e221691ff59342da094cb: $$|dist(point, center) - radius|$$

9fd936ef4e70952deb4a88319174709dc237f357: $$0 \le radius \lt maxRadius$$

28e7ed86b9fe13358b1650650bca2da268724369: $$\Delta \rho$$

decf9b9d736fd8e49013c782262d17b38d974c10: $$\Delta \theta \lt \theta_{threshold}$$

2815751be12b8bae18252ee8732aede3a9fd8b2b: $$\Delta \rho \lt \rho_{threshold}$$

055e49b2aa51583237056de124966a662b29f7ad: $$\Delta\theta = \min(| \theta_1 - \theta_2 |, \pi - | \theta_1 - \theta_2 |)$$

b127542845c121da61244d4c8d78681ef24b5c6c: $$1^{\circ}$$

01cd82443fe4f6f77c30adf7f201e186465e93f4: $$179^{\circ}$$

6385ac85ca279be0096cff3059b89e64c7dbad8b: $$\rho$$

d4a900993bff3d1c37c0fd2b84684716ba03369e: $$\theta$$

d1082db5482d991d92761178213be6a36846d206: $$\rho$$

6205dc7c2b2c06e26fc77beaf7d0fedb776bf57d: $$\theta$$

%%
## Drawing
```compressed-json
N4KAkARALgngDgUwgLgAQQQDwMYEMA2AlgCYBOuA7hADTgQBuCpAzoQPYB2KqATLZMzYBXUtiRoIACyhQ4zZAHoFAc0JRJQgEYA6bGwC2CgF7N6hbEcK4OCtptbErHALRY8RMpWdx8Q1TdIEfARcZgRmBShcZQUebQBGAE4EmjoghH0EDihmbgBtcDBQMBKIEm4IAHVEgFZ8XGwAeXjUkshYRAqoLChW0sxuGoAGIf5SmG54gDZRwsgKEnVuAGYa

qe1lxMSAdgAOIZ5t5YAWZe2aschJBEJlaW5ji7mIa2Vg7lm2iGYoUjYAawQAGE2Pg2KQKgBiABmQ122BGfUgmga/2UfyEHGIILBEIkv2szDguEC2SREGhhHw+AAyrB3hJBB5yT8/oDKotJNw+M9WQCEHSYAz0EzypcIBi7hxwrk0PFxWxidg1BM5SNxejhHAAJLEWWoPIAXXF0PImV13A4Qmp4sIWKwFVwy3JGKx0uY+qtNt5CAQxEmQ2O2x2gam

23FjBY7C4aESywjTFYnAAcpwxAHto9ElMprsnl9CMwACLpbr+tDQghhcWaYRYgCiwUy2X1RvFQjgxFwZcm2xzj12yx4JyO4qIHH+lut+DHbGwgPLqEr+Grz26mF6EjpCDgzk0MGcPx3qB81mQLsoABUehVt7v94funAT/UOOeTZwoDTCEZxKhllMH7ZAAYrg+hUqqqC7OK65QAAgkQygxugwTQr0CakFA5gEAhtzIdAirkno2S4HaTAWmgXozs84

K3HaBDXhut5PnuB5Hs+p5vuSuBCFAbAAErhD+f6/EICBjmRAASNx3JuqDxNoPD5qUkihIxUAADJ2pOFZVgghQAL5jMUpTlBIACyACaQIABoAFYacoRjkh0f7QDe4oDGgwyfOM3DOMcvnzJyva7AkWy7IkQzxAB2zxLs5zitctz3Ggjziq8wpBd8vz8ji4JQrC8KIjWqKapi2KggV+LkBwRIklk6HPJS1KCsK3ygmKvK5eyIVoDyXx8oCbVuaK/ri

pKkjuvq8o0UqKoBtl5U6nq+RzJANn6OZ2AaUWFAIPQABqAAKmB2YkNKVAA0gAqs4kk2RAczGs1ZoIBRqBUba9peeguDHIdLp1sQ01Tt6g2+ou8RBkMNSJDwMUYUmyHDokSPRqmHDpmliTxDU8RDDmaPPIWJbBD2ukruJzy1hVjYZI1rYvV8HZdhT8l9lMA5c8MxyAc8446Z906zvOfrcMuq5fLBFTHSIcBsGEEgTVeN4SHLpAK0r6BAV+wkrPzXz

Qp+oHgfgkHQWuPS4UhFSoU1XyRlh7g2/hfFwERn6kdKpAfV9NGkHRHAMWr6Aa1rCDK88PF8YJrC/twonU1844INJKVyQpSlJWpPRaROEt6YZxkk4uECYDUx34AAQldcGWS58BuTLnncDm2wJPFXdJGsUwnOKkHOMs2ULMQSxysPxNfMlsncspkCZX+2VDcCVV4ugkLxAgW9b+SKLzuVWL5ev0C1fVpIO6ULW0vSo2deN3VsggHJj1y/XiivI0VGN

QN+FNMqTAVPNWAi0NQYhWq2daEBNrbV2vtI6p1zqXVuvdR6z0TRvT9iLEmP1HQ1F/m6ABlFsEQ3FnKXYUweA5hzIcdGnAHjhmeJGZGmNsa8HiDwaKywAJhltMWUsZClx6RrMDemzYcj5GZqUVm3ZBHxE5tzR4gZ54QEFmDaiKc5wLkLlTGCodVEhFIBwVAkg2AUFQLgVA+hrCEDgNabs4JUB4GMbgegbASCoDnNgXwyNUB2hMSSRgPw7TKFQOoSa

njNB2QQNgKAqBiAIG6LE6MqAhCsA4KEhJcB1BOLAkwSx1hiAnm7JIF81gOAhIvBQdSdtDHGNMeYyx1iKl2PqHxUguSXFuI8V4nxKT/GqVIEErCGSwmSAiXYaJsT4mJJiVhTgqT0mZJ3DkvAmRyAWKxMUnJnEKkZPJMbbI34E79WyocqApsILcEttLa2iF8L23JE7bC+BXZdEIuKYiUQyK+0XP7L4tF/AhyYhIYIJJ6lmIsVYmxrSHEdOcRY7pRTe

lpP6fUwJ4QRmhPCcIO4kSplxISUk+ZxjUWjKyasvJGzCnbNKbsypGVeICSEicsJpAxISWlOnWecpFIqNUswdS+chaS30iUIyhQTKQDMugAA4sBIs8VlAACloSN06PiDyzxfo+QHoMZIQxsznDitsPsSR4izS+KPcevBszaC2IkXY0xIqPGWBw/lMlUqoHStHDJWUP49VXriQqcIERDD3mVV0lVg01UJMSC+ByqQ3yFHfZkAan4vxtQNUon9b7f3v

r/KURD5JAIaAtNUS1wG6kgW0SAcBCAUDYACGo2AhD/GhJIGyQJthwTssdZMN04JPTaFIyApo8lYPBqZXBEhcBTAISDYt/yc2Q0mDUPssUCaMMdomaMkwgx0I4Kwv8eNoYjEJjUeMJN+Hk0EaKkRdMmyM0ke2TssioYKJqBQqYFq4qcqFsuyAYIxaLnvVbEF6AaT/CTcwVAYKjFQCjl8cg1T9FQZg3BupiGdbNU/Mcv8AFdaXPNtcvRG43mgoQGhJ

5TBnY4Xue8j2nyvY/MnRo0ogL6L4BqVuaD1JYPweyEh0oMdmXxxEuy5OpRU7cq9VnflucNzCp0WEYukrS4VBqPxAAilAZYsqhi4HVc3LVXxfrBgUgTWGNQeCOrjIaw2fk0BTANUa9d8izW40taUa1b9vX4ySp6uS2dfVvCXumvKa8oQ723kgUqB8o3Hy6GfeNjVE2tTzYyAtEXeqv25DlgUmWRTZeeJNUGcpS3KhARWsBWpq1rVrRAetjbm2tvbZ

27tvb+2DuHSUUdFJMF/JIdOhJv0XjbAXeV4WU6BCrrlHFeGbqf1T1KMwvdaAEqHuPZMLmzrcxxj4WTWZoHhE01EU+lsL7ngyPZvI/sX6cy/u80B7S6jRbaMplLUoMsJDEh2a+PZoSAAU5k2CMG1FAHgABKag+K5kzOJXulWqGINNZKWUjggPUAg7B+9SHMO4fTKJXMpHuGjn61OURsCVyNtkfggxyj1GMJ0deQz9A7tPYkVY0NmbEBOPB24/ov7d

KAchOx6D8H+PYeTPh8T5J9DGWxxZRJjlAspJBcmHynOgq86vc+2KsAEqShSrKGXfQwErqSAAI5CGOPdY65khBAg4NsNgVvEj1jstgYzFRAixMXuSHVbrtA2aOH3BGpqhimr1f1OGilTjHCDNsWzQ5Tjil89yXYYVOGE2WFn/YQ4dhXunhruUBMMp+vC4/SLMaN4xd3vFtEiWouxrqqlskJok1fyy2m6vuWs0Fe78V3vyHcX/w9B8Sr5b5LqmeMte

raA2yvQnTz9j0qZ1/V2JN4tUr2hNxWHMI3K65FhkdfFFzz2GC7vofNlbkA1spjTCevuQZ4ajmvUd9mYGvi0wbBdiRi+60u+e+Gq7OpmjWMqEAyYVu2AkkjQh0NQ5kvW4qlwRQ600qZc1cNkRgdkywkgxwwEsqAAWodFMI0JUNEqQFdIkN2EiN9vvrOqQH8FQOtEfsbugabhUM4NXPoMqsBEMEQZeEQdppgIQNCNpkYP8PxJJHZEIJeHQSAW5CSMw

cgYbqgcAZwRIJtIajULXJUEMJgF2EkI6tKEYIdNqAodAAwX9EwWYqoQZOgtdm+rdn2Mng5sGI8JfmosQrzsBh9kIros8AKkKnrgEapigepgWGXNAbAfAYgT7pqkxK3N5KcNoJQn2LsFQuuglFQjHrwFzPHicEninjwGns8Bnv1FzIFhnKAqFv6n3kGtVHXrFg3jTJGsDElq3ufGlp3hlimvmiPjmoGpmn5tmgIIGkPh1IMZAGVsWtlIqGWtVjPpW

nVqtIvv1uOuaKvt9KNo6IkNvhPj4Wvt8HNvJDUMcDsInk6sXqttfijNwltk/pMFFCMGGIcDcdKjesdiplJsiOdgzJdusa+mzHIq4ZwkaokJ4f+m9gLFoneqdrcqjjSMSBQC4tCi0vYu0qgAsOoAADoZKBxwCIAdI0oUqlJrL5L4k0pNKvBsAWKwbWCE5QD4lsDQh+LZBMCYpVI8aQYolonNK2KYmOI4mlLoi2LEmbJFJkm5LrIFJbI0kZJ0mhCbJ

MmeJsl2jdCBA/AHJ4YU68BnImzU4ka07gb054QVBiAckQjM4vIUboDgTEDEDvDMZc4+wfQQDm6W42526SQO5O4u5u4e5e7kj87ApyQQDImUD8kwpCkdIimoBilElMCSkzLZLklUpylFIKnKBKkMnGIy7TKsnsmalcmK5iZ6lJycppyl7yRa5BGKaaShGipqbsFREVAcAKqJArjxBGD1x2TMCaA8A2REGSRwRTAIDVwJHoB+5RCV6B7cBn7aD7DDh

9y7CnBOo8A3JOa8A1A1BpFDBnC4yPBrBRRrnp59T/hx4AQcJRTHkLZ35SA1kxQqIB5oDLyBqdHNExYRoJYdEt7s4pYNQd7NRd5FZTFdSDTDEXljE5RPyTE/wTRj5TbzHAKQRWa1YdgL4GgbGDYwkFgb4vBDqIUVRTa75WGgHLCH4fynGZFBj4yTyHqTB5iPFYwEbrmZilEfFlBfFf4ImlC/7EBiLPqAG1oaGuRdDgFtkSBAi4A3T6DEDJikA3T2H

qEcGQFYE4F4EEHEGkHkGUHUG0GoGKGOi2EsG1psFoG1oYEVCJBwRDDabWSSBGDKBkH8SSAAQ2TJhFj8T8TyFGXkVKGmX2GOEszOGgn9hTBrC2bHAhYpyhGAaqJwknaBHTwNnKb64tmWWmRlwyVyUKVKVTnuRJHaoLl2rHCDgjBRRxRvFbmQCQRUJDD7mHnQy7kuZwjHDnl5ZoDcLZQzxyaxUiZzlvkFafkQCbwtFxZtG/kVSjUEht5AWXxjqgX9E

94QVDEZrQWD5gUIWlZIVzFT5LHoVz5VprHYUYIr54UjYOizpwSAzEWEKHHTbHFhByJwywx8zyIPkP73EqLfXbZl4JQJR55wyHYCLJVfZ/GPoAkAFnVOEgkfr3ZxiBSBSOYvYFxHHvbwkpXfZoZ8kqm4BEnBDY6ODQjQicnZBWDdD4kohhDIrGJ6C4hQ4pmMngivAID4lA4k1k0XyU0ICoA01+ieLGLMCqSIBQ5UnymE0wCqly4kphJsD4kkCNRiH

S3qB83NI5ncm41Rn42E182c1iHc3K2yL82hCC0LIM3ghM3Un5m1TKD61c3k1YQm0C102oAi0E0IDW2S0+DS0FmEqzLy7GJ8R+IJIU3Qiq3XDoma26z4bcgGkgRGkWx052kQCWmak0aYS2ls4ekkBOmTVfBfLezkRlwdlFhdnMA9l9kDlDkjljkTkhmBxAqC5Il42MkE0+AO2G1O282m201C1OJrze1Zm21s3E3d080u1m1u0e1i3M1S0y2B1y0h1

K3h2R3q20ncRMpxwVmSZVmyaZx1mpU65KZNlFwRGtnZUVDKBgSWQR31xAj8THTaZwSyr/DxD0DQg8DQhIEwTWEShzIB7JHyQUKNWbA3nnG5gwyo0QD1UzAJC5gEyZHxTHDxSrCdU2p8xxDnExWrClEjCrAeo1ETxhQbqHCwxuFbpcWvmoDvlPyjXjXfmN6HzRpNGnxxoLXpbJrtQ7WQUbVdW8BbUrXD5rUzF7WPUoWLFoWz5fDz6nVL5Gy4UY04K

7GzpFgHH6hkXiXdVUU+hyLDwX6oPBiMWx61VX5RiP6sWTBuoJTnF7DbqmQ8VY0Q0QACVCWAkGhAEcHaNgHFVWWaHoCVBW6NA8CaBgj6AqVeP+OQHYAAD6/wcE9YQIkgQwUA1cjqVuNkGkRgjw3BjQlhPjLwQVrBql0TZcx0QIPAh0sqQIzgFA+AxwmgyeQIQI2oHANQMAQwXI/lhTyhdhrBIV0iYVCNXMkVfchDHVau6NT1mN4NvxUgaVZ9VMmVJ

ukBQTITYTBghVLcJV5CpqCDJwMUcIa5WekzXwkEw8xwIeFxmYqwgYuDDjwUAjMVD5fVckwwFeYWk+DRDD9eBd/F7RM1/57D81CavR3DqaojsF/IIx+WDR8FJWo+f8yFB10jKxmF8jOFF1yj+Fqjf0RYd1u1JFS6w2s2gikUWwNzX1dxc8jz5jLCTxco5VMwdjm2H+YNPxD6f+0NTMwJ76vYEVaw3Cu5Zz0m8VpLiVIGnLppt4bdfdgIUA2gqA5ku

AgIYyfNfwtYcS9a846r+JGtSpWyZAioficS/iat8riSWtrdOtliNNCrSrKrarFrmrbA2r5g/w6r0dhrUpfwz4ag7JXr9rVrsdepnCVOZsydppqd6dTAmdLOqdDp+dnO3ybpZcN9+gd9MAD9T9L9b9H9X9P9jdQcYZsrtrlriryrqrfNLrdgbrJ4HrXrBrKZxr/rZrwdUdwbi1Lw29yuice9Uz1ZxDtZA1Vwiz0zzZF9WV1lEg0INkFAiQcAsTkO/

EuACASEcA5kFAQw1c9Akgylf9oBAD/uc5wDSkMU9q5VkJm5cMg4FCeRpRcQg4eD5wMwA4gYGDfmX6yQuYl6B5RMHC8U1RPKZxVzqMeYP6pwFqkJZjNDdDNebDjDsWP5Tef5teIL3RwFRsy1PDiL61MLm18L21eHYjyL+1c0UjtRsjJ1vLy+Wxl16+eLLwwEGj3AWj1hlFbQbBJxgiDVSDYYv1NL/UtCTCdx/1vAfMSNFCl+pMHL+uXLgl/+NabQY

l/9OzZTFQmA2olkh0uwlklQyqkTolalZccTCTSTKTaTGTWTOTNQeTBT/9fTZlXHpTEB0R2wHARBdkV02wwEtlnaoEN0x09AuARYlkhnPTjnxT5lgzkAN24Vozu5Rwbq2U3hMzsJUr8n9ZJ9jZE759ahkRV9EgWnOnenBn2zkl5cc8m5ikuMcMknpwWwKi9VmR2grqx54e0Uewn7gwP6wHXqiUdRVefDCHJ8SHrRP+gLR8wLc1mH3b18CL0x0L/eo

xQjuHS3sxEjqLVHpQcjtHij2L6XuL11f0wEhLSLD1noErL1i4MwlVoedL313Im5LFbCSQIwfMhq7+BYTjczCn7jMNCjQz8NAriX663C5eUzAGErfhzj8zP26AcEjpkSPwDQwQAmhAarYKQS2O6g3YTbMZbSjizi+JOZYyk0w9bKmInrQOePcSFrApsKWJqkjA8tVJSKTNId9t9PdJDPm9yOPJEASPyK9gUQ3i4QcGmPfN2PEvtPqk9PUdjPsZnSC

ZvP4yY+lPokE4uP8vBPGJRPHSLPNbSpHP8tCZiSZvfPipOp5OrK4bZOFySdpG0bOdsb1ponWdLsOdSbzpzwRd3OFQc7C7S7K7a7G7W7O7e7B7AcJbLd4ZwvKPYv6PkvWPIQOPcv+PVvgpBvKvZPOKf8mv7K2vGfCvG9+vcKASrPIdri7ixAnPdJ3Plviv/P0cvb4m/bqucVXKT5R9Kk47Iq+XR+qzZc5kx0yqNIFTyY8QFAVup0NIsTGkjQNIMAU

w2o0f0s/9M5QDuz/4N72gwYye4P0Ut7D7Jw+5MUWeuMIY+ePXaAcUYUUVz566LxuRQRT5LmaRd2cU5VoDX6MFcHI1YFuN3+bIgpurDE+LN3bzzccOkLB+CNxW5wt4BhWYRuBTgGlBNu+oSRlVjRYYUIEV2A7vRxxZXUxsuASSKxzQDscKKujUhIuDjDf96KXFJ7uQjMZ/VGW8kShG6myIPlZOt6P7mdihriJlOl9Dfke3U5ucKgsqPGEQXrBQASC

RnFTiZwqDJgPOXnHzn5zggBdZKwXULuFwc5HsnOwVEdHyxcKCtweKXaEkQKAxJVpWx9EInl2WZTth+EgqQTILkGHsTMfjfoCsE4HaAo8g4JSIagJhNcH2kJNrgTB4ClF+w0UIDuUQvI5heqNZD5kN2+ZIDfmE1FDiw1mqAUwWIFPoutyhYrxYW78IjigN4boDxGmA7bjVmOqrF9uV8JRkd2IGOhJIsqcgY0LJZQwlITqcHqO3pbrYQGjAsTmwIRi

blBwJ5LijwO+JZcf8/xQQfgOB78t5spg5LpDy77Q9fC1g6YTjRtaokoUFAa4OkCKSus4kmfTtm6z4j6B3adJANgin0C44LEUaNnhwB1aesCA+APXmTwWQWtfgvoa1uGUjK7DLE+w30MECOF1sThpffmucIMBXDTWKvO4azxJDAwzeLwixNSA+F0kvhUdH4SAIpC6k7eCdR3pG2d6IkzStsCQG73jbZ1zSEgH3riP95psKgo/cfpP2n6z9MA8/Rfs

v1X7r8OMTdLjILwBFolgRhw1AMcIsSQitWFw2ETcMZIIi+aSIiqCiMbZvCMRA9b4YEFxGiYd6rKSsoOwPqa5ehwRXXPYPCIFdhBATCABpVwL4FCCJBMghQSYAGVu2vTIKsAydQdxzgMVKzMPGHgHk8ibqZYEuW2CwwuYkJNYIGGhi392Be5YcBcS8wHlL+/cN/sOw7hKQsGTXK4oTD7ifN6iqQoAX8wyHN50OkAzhuC0W4FCoKAjGCrmlKEkcJQF

QlIRxlQo7dIAe3eYWOgaEJU7QTHXABYXuqLpHqlAv8DwGoHH5FwCMAcJuWhiX4mBZxR7kMKsbzZzUHhB4uy14E2D+Ksw4SrDVCog8lhbhCEo8BgppcEqsPPgV8AVgakhBYAAoFZSCglAhg60UdLePQLTBYxJwLYBakTGRRkxVlNMZA1sy1AsxOYTjiOli45QSQaTHsZUgoFQJ0g4id0p6Wty257cjuZ3K7ndye5vcqBD0mwASQVA7QDgEAUtUwB+

hjo7iMkCJVrSNUtgnAmKFkQAilFE8RlRqhcUezH9IqFqF/LsGfFjjIAWQYgNXBgn7I4JjWBCY1HdJl0K6VdSyP2UHLDlRy45ScrhLuEESJAREpWnQQpCEAyJxACiRqQaw0TfBB5YeFQlsxeiIhBeUVm0DYl5gTgZwWzBHhWF8SXO3UKCXBFMrXBcA2xZ4IJM8nMFvJZcAweKCCC1h9oF40oPKPMgkADJLYDkOoAB6bix2OXdKmEQNxD8NMFI+Jok

2SapN0muwTJtk1ybVx8m7gkyioTPbcIgxcYXcsPBDF5hCYAY4eL4KuJoNNg0UC9NGOmAGoYoqDBGAwNsz9c5IbEribc32C5hzgow3McN3w6Ag0hTDKaqhyBYljshPRXIRCwGKVj+GA+EofkLQGkci0W3CjtgNbEQB2xQJOju9F8nHcSBGkNocOO5D8SeOUMNYGuVNRDhBOFjFGC5le4noLiZ6PsOulBobithkNblnMMul7jFhHMN4joVqDwwbJqi

cVhsMy7pTxQV4jxneLaDYzbJrE58agVxklAepvgvqYB0Gl35HxbXMaeuUJi2NRhrkvrAGignCSsQsE1AGRQknZB3SGbLNjm2fqv136n9b+r/SgRqS3I4ITQGoG0mUg9JcUuSETLACNVhgHCKhG6jihWSIh88KmRcQShh5Miesr/tsEZnmjSggk1mY4FEkcz4J/+d0kH0XbLseAq7dds8Ij67t922k8WRUElnSzcJss8iZRIVnoFnAjVEYNByKJ8x

PCw4eKMnlYkh5cwlCGYBrLzBHBhwJs7jqj0wgBSzEQUhjhgCxDZzgRPkiqXYVCn4BwpcPcUNFNimBzmACUyQElLBkLNUpSzM0ZlKkroBlBnnbzr53842RAu2gsLhFzXBRdKpO/FLgpEHBxhIqUeaGC92eAXNOE+/H9NFCij4xIO5xbqWuX35eZagyeSDhwjpZvNJgCkVOaalOA2MUGlCGaU2PGL0MCx6Q5hsWLYalich2HPIbAJZBVjdpSAisQdI

bFkdjpAKFsdUOo61COxA2Q7t2IIq4BRZF3QcZoygQ+NRxbkmgdchipHA9gv0j3sjBPlIzWBS4mfPIinkVUQZUw9GfwIhk7igecXYZqDyDClFMw2YE8SjOOLnjkpTWWuUZJKCKyHxSsgmetEVkoMd50HddFQhnEicrKFqffkOHPkQ8nUa5ShCbP6yZzoJbMq2ZzNtllx7ZIfJ2WH1dnbt3ZvIqKfhLciaSCJfs3SQHMMnUTbJ9qbMLUEoTKJDgA4D

4lTOGA2ZVgG6N6YnlNTpzQpWIC2ezM0XQ13SzIifkCCn4z85+C/JfivzX6ezTFhEuqFpMsVyzA53CqmWHLxjZgFFUUFzJQlDxxz10cUVYKMx6pxhoY/i9yVnK8khAbpZsguXUuLmMEx5XwMKWYkrnPBq5+k2ufXMbkULbBJogfg4NNlOCJAjQOCMwGOi7ADM/wYCCOQQDaY2A9YQ6FbiBDaZJI908qRIC36nsd+0MR4BsBGB7BIG8UO9g+x/QbBI

qeYGKgXhgYVFbUQY98XCE4S5g1y0MGBsfLlCHBqZ9U3GDMAAhwwYGAAn5g/MWmTdpq03VaRwzflXwYBW0/+YUMI6/ziOG3RscNROnT4jqYCjFnUM7FQKJWPYk7i8GTAPSkFHHZ6TdwDD4wtgw4NcTum+mTAEYf0vBTDDokTDfuHCtxkp0yWqdRBklIrugEaD4BMAV0fQPgFlSAwSmUTcQRIFsr2VHKzlVyu5SmCeVvKvlPQYFRUIyrjOGndWJU2q

a1N6mjTZpq03aadNum3jUef0xi5GC4aMMu7Ilz7gcJUGFg9oZK38Lf4++Lc00RlJLgdyIAIqsVRKqlUVdPBkAX6C1SuZ55uEVCdiZcxgb1VzgvgovHGF/5lErU0FQbiXmHY4rBqXzTFfmPQ7ACixaHF+WtKw7wqP5iKr+TtNW57TP5xFI6ZUKxWHUZGu3GjhAs2LXS85xKkgWVKJaXc851K/qL+i5gHBcYJjeSHnlZWnIIeeMICWQt4rY1wZinHl

hAvi4jM+YUVQcHzHdVnjNhgy7YeGRBAcAnYDbMie8L0DghLZsiZgBzSECw56ATNU0DCIpIbIQ6ywIsPiRvWkA713QWDEDkwCw4YAsOIwOLQ4BvrLhFraUmzCMwC99EZ6i9fWivWD1b19EQDdjifWoAX1S4P4JcI/WWIv1RYdDf+sw2y8QNqAMDagAg34aYRsGlZKUng0289YBIiNjTiggp1XejUONjaS940j7SedX3oXRYyMiJlUymZXMoWXSRll

qy9ZZsu2Ux9m6gvZDbRkvVBAyNAG2Xjhrw3QaZS+SM3t+q00UagNVGmjXRv02Ma0y8SbsAhtb5K52+aAPUV3yHYgd5M2uOwSMrbkBqhVEABVQ5WSbKrGgblDyl5R8p+UR5+gt0Qcu4RhQXMf7KhpOIDFJBjl15c4Hc3v4qJHlFqIMbuX2A5Lgww4GzGY2+Xeo0idzBGITAPIZFgZyQotXNMaJjdCxT88tRAMrXQCa1q1JFd/IbWoq6x6KwBa2uAW

UdQFna8BVDPqGErec/ax0MdHJWNZkFVK04onjOCRUjgs4oTqgEvRzr5IfMeqYakdTLqulMwgQdQv6xbr6FyeIMBcTq1rC857CpuZjMB6CL0CfCp8bWhfFCKL2+W4/jsEWwlajKVzPuMMCq2Aratxsz7RBNUVBKNFNs0JaXU7LdleyckmuopProqSxZSSjSSkosVQJ/ZvSmxZ43vH2LAxh8xBh8piEk6gw8UDxSDuGAhhE81S9pYEpEnKA2O8OxCW

XEmXTLZlQweZYsrk1rKNlWyxJepPQDmKSJOk9JUTt4W+DhwcUc4njFXkbokgtVHWVFE12GptdWuvuMzqGIeTmlDSgSU0sCn1KS5VAMuRXMimQAel8suuWoAbn/4OFxo0+n6pWZZSw4hqmpnUwaZNMeALTNph0y6aFUQpByo4FczswzB5EqwRPK/3OYrBbMMi0otDHhiBCtg3U1BtcqdS4NUG7ErPMNO5AbB5E+MWGMPHOXnFSiN8hrXfNG7RZH5S

0zITNw61cM/5dagjtWLW5NqiWLa2+XzhAXLFcBWFGhZAsIEerZts6bTAtpEEjjltr1R1Hc0/HTr72OCjGGwK3RazNynKz/Cdq3FnasZF2uhUsOdXCtdyB6mHkeu9V1ouFti18fePxmfbCZb4rPQBBz1xjU97yoys4DiDqzS9iWrPJXuODKLmZmEWHezrEntKtFFQHnVJv50yallKy4XYprF1mLcdUugnfLMyVKz7UWeOeU5IuLRCC9b2kPABFIN9

xyDZBlBeBNQWNKhJbOjneJKgMSBeZ99ayLm0FkFsRZKB5JcRJllWLCdVE4ncZIPKeEEot2mKvGvkRxzyqH1GzKcBmC1AGd+u8YobrN0tKPV/ko3RbvJAdKIpHCu3X0sd0DKr9zcrzT8Q92BrlUK/GkDUEaC2Rw13bHVBcQ2Cbkf00wahHzDMaQRfFS5BQ0pCYknAbMDyi8rlq4plb81C8IarQ0AElqWtje5+e1thXrT35m07re3oQHFD+t+0wtOP

mG3NjRtg+moXiu7VdiiVMC/iG0ISqjrUA5wQcE4q+m4K0oma24t9PE49S154DbgVyqbk8qN1t+jQpAW4K8F+CghYQqIXEKSFpCshSLf41dE6q7VTMh1SYJoTnERgl6FRKeIv1oyTDCPCAApFQCHRCwQgAgMJC9YkhLh8ZG6PxCLDARA2/EQ40YFQBKB8S0gWQPICUCiZrEdGR0oWE4C6ADACgbAIEFkTOBCkzgMwMwGONEBfwoJ5wMcPMCgnSA+g

Opo7ucAiBiA0IOE4rG/3OA7IuAIwEYBgAKBIQwvZdtcFibmRwg1wWDAoHxJxBUACfc42bxvq/haw+JIMagEEj2gSS3rekiqX9qBtZU+JhALWD+EVB9jhxyEycd/BnGkT2JR3agCuM3G7jDxp47SY4CvG5AigBQJ8e7DYQfjggDgP8cMBAmQg3QUE1iHBNHHpTCAWE/CewCInkTIpNE/+sxN/BmAOJvEwSaJMknHSZJhABSapMS91T9Jxk3Ka57Cm

2THADk1yYSQ8nm2ypFmlEnhz+IhTrJtgKxrjqU4HexGKNqSNTqPJ+N9GQTQRCYx+8xNJdPOaGTj7imlWkpqE6cYtZMnLj1x24/4nuM/g1TLxmQFqY+NMovj+pxwIaeNOAngT5psExCYbMwncAWJrVgifOMon1ALpjE1iY9M8BcT+Jwk8SdJNq1AzItYM3SaVZhmYNDfSMwrWjNKtYzyZbMrmX5PJnpkqZs81vUc271O+Yrbvnmt74pSzDGVRwZ7o

gBDG+CAhIQiITEISEpCMhOQqHpi1mY24uYPlITGiouZMidLC5gUUsllKPCBMLio8qfYIzb2ZwKDrSsL0bZ1gawGKlAyYXTAfUXwUFcWsQ5xHIVy06FRWqSNVqlqXWkRj1vrWIDGtbe5tbkb70LFTpY2tsV2sm0Eqx90C3sTSGn30FQCVB02R0LbjwxWqUJVfTfl4C9CCFbCLPC6oKXZRJhK6lxr0chm7iFhJgp1LjEnguYWF0zQ9dsb4rX7rxmS3

hQ/vtW1pFZeFuGARduanpKZYAChPHIovvSAZPMYAzUrUWWzwD1sxgwjoqDITvSaE/0phKDI4Ssd4usoGgb4My7BDcum7YFAMaJ54oEQ6qnHIRnnKz8AEYq3sGUP5y6D6imKyEq50VArDUwGw3YceiqTsdEu7K2kusV5XiDW6fGPsCOCZFN9eMOOSIfXTZELMZ+R4HVdUWFzc5lg+q8tfN2tLS5fk8uZ0pt14TGAMUgQzkH6XO6m5ru3Lt5v9WFcZ

26ANgJgAlVGBMAzgHYLgFiZwRJI/EYCPxCMA2RJImAMszPt9yAN9lsFtAM4EigKQiYlVaPQxIfZ5hSZMwChHFA4QJRgjzzWoAkBGva7TghwSISReWJ8oCthqBGI6njHV7ojYK2Iw3qYtN6YVoLZI9WtSNcX0jz8FFXxbRVQsMBQlgfREfOniXzLkl3tatYn1/QZj5Q4lkOIpVUCaDyluUHDG4Sn4WVGl5CHnhgo6W/w1xZPKpbpZGXd9a6gHjeP5

UeDFqfmmAFbmhDXGNIxAMgbqoUH6r0AN0ZgFdHwD6AiC0IZQKGtiZsA+YsTXYAgCujOAp9kXaLfMa44QTLtB48Eu3FwPn7UZXqpy6YeGXmG/zgas2xbaLBW2yBOy3xo4f8j2NU1KXYYB4T3kBiIhaRJRPDHkRWToo0Y1w/jd6F0XGtC05Dq1pWmsX6b7FnSZxdQEs2ihgjRtbWoEsos21OAoo3gIkuj6hb4+mBcYoAXDrVr1R5Ln/0TzUsmV3VeP

S0YZaEKuhFCKKG6mO17XTL524weFUPHh5MwZjTY3Hb1tFVwywEO0IWFKQS48cPAMJEykDgEA1TYpiQPfYqQi1lWuOCHK/agDv2rA7wpQJmbDaEjczJIk9TG143u9GVCbb3sJvpEVnfk3s+6/gEevPXtgr19659e+u/X/rxbFTfol/uP2AHkuYB6A8/sQOyyOolXPMxkw98jR/fZO2Mv/PMAiCLlRIFXAmDZ2MA+gTQH6C7BhNcRv0Z6/FA2D1SMx

OSqogvIeDTAEgSkRhSK1XJmNHlEY/G5wPJvwd5pzeti9233jMXwByWIx63o5vcWO9P89mwNs5sYqKbI2kS4UdxXj2Bbk9tjDsRJW4AurQ6hBQwcBs6MZbL07kFZioTpF8FW21BjA3VsLlgan1XhOuPIUmGj7B+k+wjSovTAeqdLNLlIB7PvGFAFAYp9oBgDCAQHIjkc6eCFCFgoAAAfiIA/AAAvMdA0jJhKgyYesPWGhC7Bd2sqKYOXMaCYBJItl

QgJ5USSWRsAh0ZQNgGVTPxJwszDhcwHcB/giZz2MAPEAgnnW0pk7Th4GvwCxNDoFcUE/gEaA3RYmczuALKigDahkwPAcyFwEEd7KvmwDZwNBxDxzyt0FeqQ4o9jwdxgVqN7MPImhiaOLyMVK5oGFor7zrtQYMI0+SDCprL0VCbMJejdTlU9HMRhi9TYBZQqzHXRKAZY/sfWOMj/drI93qRa96a9/ego7zYukeOe1XjlRj44bgDjSKUtgjHPqhgUI

VZPMBo/0POW7bOEwrU1BQm31ydj1+t3lf0etUCqI1fm2VPxGIC7BCApAAk/IOEF+bHbzt12+7c9ve2pgvt/24Ha1XaHbbGrm69An0A6E9CBhIwhFFMLmETXm15zuKnDtH7YZZ984DNdjtsLL9Cd7Z63KusWjICCrpVyq7VeCOxBka/yKEIINwgGpNmFPFxQubSOuYjwZGqtomnRjCL9dl8lEf0dNb69EKnF6Y6yEWPyxVj3u2zdr3DRK3Q98js4+

xUdqxLE2+l6UZm0wKdOlR67qcU+V54wwNzaddhd22iKCDyeHW90YleuNtx6TpY6fajupzBwPrxZ03N2NwQZADQZjUxoM3UpIRiZYkt/cR4bvsAW7mzURolFet93fGh3lmf1IcbjSXGl3iWcpFFnWcJZukSm2LoYPQUhz45wQDOcXOdw1z25/c8efKaBR+idd2L1PeUpZSF7i1le8QciY2+r55h+rk/NsPfVl1iw5q6dsu23bHtyVV7Z9t+2A7Qdq

Ldqq2ug3UAQ8R1MvPOKKHlEpN5qWFAPLZg4ttQLPLDFrvwXz2m5IMCnL5g5qVINZZWUi5hi2Zohow6hvm8xfNbsXoA3F2W47udambPdgrH3ZrETE63PewS1S+EtNv0W7jkfQy+N1ZXex9m+BWy8W3WFFLGc04umPYlR5Bha9vbSwMXFvcJpETtYBO532H2Z3gPQ/fuI9cLuhwZ5KHg9r9errOFLl2/W5be0CLPL6BKhNnnxj8fTlmYATsUvE8hjJ

PFqaTxFcgosz6DEBs2UwdutYOcHL1t6x9a+s/W/rANr4F7Jx28H+rR1rA7ROAny3Mi5xVqhamKWjCQxb+bXYOGmB1XzZJX2K5Afis/ujndnf9+c8ufAe7nDz7gxIB9km3pdA1oOdTp3WQMRgm5YcIGEebuLL0ieS9FsBNQJbNnUOkJ0ta0OrXNDah4KTBbK/W79DuOQ6/bpOvQ0Xd7D383s783aFagNrwwrgGMK7AHX/Yij9obPZbB7UZweqV+ij

ziKk1ievcpsAoROSRwReJGbhbP4XyPMdzS73CHxtXNgVyeSKGGGoTy2MXlNrF8W8U+lvDHKnwl9kY0/VvluyA9n7p+HuNv21Rn4fViyktlHexmgOS8ZX6icuwnLi5F3y80vDvlbbRwmNk75iRUD73KgL/iogAR2Qv7hcMXZfWG+vHL0X57TePi/3jEvOM5LwT4h4fSGd1/L/eT6NSbkjUNPuMIV4N2gHJvzVySWXAOdzeTnAHpbzc5W9gfGszX3q

61/x38HMDt+7A3ZhyUQ3b2dXGyTrIUNnAfI56c9IpbACGhnpE3xq4E7K8zf7SFuFCT6T9IYTAy2Etb1H9SUx/crO34Q4am5dR5TU4zBfdl+YURC95jqfBmBL6xUqogtS573nKe85yNrNhNpW992sfeDrNc68T9/ER/esPHD9uX5rEJsAEAh0bYNqDsgOH5yYNyEpPIYmgTpgjCrwyfLij78xDjizhKg39GxDnmu5DYJd6SDDgDZ7qMn3m8LVOOm7

QAooqrAW+K3YsWiRqz4VuRLlW6d6A9mkb1uQCvkYuOtLvzYme7bscQi2LwP/JRoU2FUa9uV7JmDRQSToyqNGM6lE6tGbAhuSwwcIFOrJOxlvMxpOgXhk4Csr7EjYHA+6hF6rWj2lO67GVcOUhi4NIJaQS8NIEwBmA6YIhqo4vAZjj8BggbBjCBQyOYC4i5yLe6EYOZk7wmk+ZjnSFmHvMg4lmHOC6SpslZqtbVmgvJIFY4AgVkBCBIgQoHPm5ZLq

IDsrmgaK8omHj+bpSOHu0D6IgALwbgALM7eQHkBAgPiJqRi4lJuoD4ShoIaCQO7GqoHEi6gXA6aBVGN2zPIAmuSLs4HyP+ZAgGkNgBwQFgBQAsuMPokS52YNu4asekVKgxI034hcR5E8iAeT78B/Pxx9+dLLhZfo1MoaiZ+ubnT70W8noz6uMYAsp5zcbPm5CqQJ7iIC4iyKgIyX4tYjz4UueniWgj2Z0tgEksvONUaHATitOpRQI7vsATS1VGYy

6+d2FZZ9SJ5DBS62e1nS4j6DAYbaKCEgNpySA5kP8C4A/EJgD1gBgGRKJA5kB5xrskkMcBOu0/raph2Hlu+ZCwEAL4H+BaSIEGjIwQaYjEAYQeSBcBJhqZ55yDIoYEeqxgZ4E+BfgQEFMAQQYkgQhUIeIHhkQIeiGBwYIViGhB4QfvSsOL5Ch52Bb5oxw+OETJ5pJ2APhv4WuVwTcF3BDwU8EIALwW8FpwnwYI5h61Hs9Zx4qetk554+Sui6/OHM

DVw+Q2YO1ScIh3tGKNc9qHVIoMNmIGBrGZPnEBBCUeAJwAypyu0EABVNl0EmOtNu3Z9BkAZMGNamnl3qD2vPg26IBhnkPqYs51CL4duvYhmasuO+Oy5PSd3r26SeW+jZir2JAeVQueW9m9wjgBweKE/cfnpr776jAXO4I0ewYEYuYuTqworuU7mb6uWb2u5aLGSXlZTf6LUucAEwSQAngo2B6MHIxUCQNrquEDHsQo1AVvjwrlhmwEqGXoKoQ/7q

hwcqUSKQMeh4oAyrvmnK3eOYV75RWwSpzp++SgpJA8AmABQDKo9AJjoR+PVllbR+jWBgYZK8fo1R4wmwEaifSORJcSo0VMpBxeKlCKgw4M15ON6s6RfqV4CS5XhADpBmQdkG5B84ZlYbeOVtt4deHzl+gcUG4arbrO2BjIbuoewGr6fUtOotYj+8EA94aGpupP7qGRTDP5Xh73k3IGGS/kYanWU7gG7u6KdieoVA3gb4Gg4CSO8L32MgGLgIQOZI

HDqA+gMwA4hN7lA73ueZrEElmWgUg7UiyQaWbkgkBMBBCA/nPxA8ASHpL452R/jR7uGQYvfxYMPMAQbJu8dAUQlK3Eiyy0U2bqsDNBdAkQwgcDdrJ70+nQS3bxGbWuY4QBG0pMSDBGgIEDQBNqOMHaeUAfAEzQVQq47i289h6rVG65PsBDukipvZr6hChajDARMIFDbB7rrsHmoSYQdi0BN9icH9YZwXyoXB6ANsD6AdkCMDVwl4ICAW2dkGwBFg

HAIkBCARzsdAkSvETBE/Brrn8Fo0AIThGmK+EWoBYoDJvgAkRjuuRGURmiCb4uMcIatYIh37kiH8iAuILzYReQLhGaaBESVHERtEGREURpIaViqwqOAVF4RqAF1FERZUb1GSAlUQNEOB5IQw59szmvYFNCs6N2xoR2HhhEWuEUVFE7ssUVRj8QCUUlEpRaUbiJzGVHl4KFBrxPajraG8mvI0BCeswKpe0wMWGwwLvgqEpqJVpkR0y1COF65q7mpF

RLk6YjsAQ+7mLByqRHQUW4aRNNgkbaRZobpE6eSAlaGwBzNuZHc2NLs2582rbqgHTa6ATApCAEvgFTehU7LLbyQW+qejvS06n3DZQcTs5hHMfUkjJHBMYVQqzu0MpZa+RjwCGKpcqYRlzx2pvjfpCGDYffoJej+q9p5hhwA/wDuCcmGBXee4WAB54xyj34WogUIGClE9YXfq1oAUB9EGybyt+hQMRlO+KAxDHveQpy8UJ74qG3vheFTeJfi1YSAG

kNkxDAzADUCXgVqo+GoGS4dhxN+b4fcz5KE6nmCQkHFBvZ2Kz0a4p1c+MMMCv6Z4Q1bRWxfleGl+EAOxGcR3EXX584pAFLKbeK4bLrEGceiVZF4lCCC5V6Wcd6KZEucZOJMKUwCBGqGUEWZ4T+Rci96wRGADtZ6GCEZ96L+8UshG/eZ1v96uBm0ZaJk0RgNgDEAbuPxBTON0EhCNAsqKQDAQuwM4BGAYtplHPOImhdECRR3vagbaSQMjbhxlQTwj

2KUHHsAx6vQjloWoCkHCA+eeeLlonK+Nu6h7kxzBGLYW+WkjKN2NboW4SApaqAF4uAFOW7wxZkQ0RIxZLjaFTBfPvaEC+joTeIQAGkBwBXQUqscDJgV0EJLMA2wJgBEEQgIQB2QNIEQTAQE2BBJ1R09r2L0ABMT4yD+9nnIg7AkUKZJEBzkQr5nA1MR54EYMHNQE/OUYeK6pOWvpureRrhADLTAB5P14cBHqjCH+uXcbs5MhlopZCNA+gGPzLA/E

ND5BOfEa87QcjVKjapyeMJmAmoW8YOBpEowj+iy+P6A0EXkBYQ6h6y8MLkrCeVwDWToM9Wv/5PxvzMDHYAPAGWpt24AXDEpG/Fj/Gc+EweS7i2lLhYnUuSARjEnBUCOAmQJh0NAmwJ1cPAmIJyCagnoJmCblGeOZnhgG4AAwB6GPUuAbxyHAewAraBh/QjcojusMH1LH8KiIzE9GLCRPY7B7CV5iAq3CfdqcBUXi4y7GbTIe4QA9SaGx28ZjOcgw

OMQe4HkYcQUzjaBTEW7CpBomq6SIhCVMiGo4TSQ5q2BTDmSEYeCmGv6Mhvmha4wApANXCkC8QP8Aux8lsbb8RbzhHgh4BsjmDryQMlf5MsZ/MCrK6tQMTbR4z/sZFK2f0V6hJCtFuDEGhDPlDEluJoQ4kEu5oe4lPxv8XY4Whh0tMFYCDoWPbD6/iRAlQJMCXAkIJSCSgloJGCcgTC+U9tJY+OAjv444BPboIhoujXOCSUxkYRQlHobAgDIXEpVr

55MJCdiFElJbCQO5eYmXr0JX2xvrzG1J+iJSahAwwcQD4kz2k4hggQgFgFDR4ZCymQmgQOynPCgclynCA/8koHURUQZxpmMsEAWbxBVIkkH9JjXpAANRjLgCjNRpbBZAhAgqX6Acpoqd4jipNgYw4d8aHh+buaX5onZu6G0YD4WupAHBBwQyYD8BXQPAEWDVwGkHBDKAQgNsCuC+mOlbSJyMtKDbJW6Fcz7AcYEpDJ4eeJFCoW1jFcqrijqNLFrk

O2tcl+YCQnmoRp+/Erphgq8sd5gxf/gW7N2E3G8kwx+LmWJfx/yVz6/JT8c4kAJdoZAAGewCSCnyMYKYEnBJUKeEmwpUSQinOhSKaL4+OzkEkmIKNngpbS+zmLmA9UmRCGH8uk6oK7vUl6G4akpoMlO4UpHjqUnUp3ElwleE3MdVGMp8zBmFxeWYcLG5R6sXjJviGaV6LTAIYu9wCeZsZBIWx0cY97nhD6bZGgR61uoYJUNcStYeqCsObA5kyECY

brR6/gsmWiUANCDKo7TpgCYAlnpskSUEalVyXRFYeHgRCtmKDrDgMFGhQXy1ytk606eYLT4ppgwBwhLkkJMGGHadAkjLhGDyQWp5izyepFFpTPu8mwxnyeWnfJlaa4mmRFaVzb6ePNr4koBLaRCkhJYSTCmRJ8KVgloB3jmNiaAJUGikLBz1L6Ha6nik5H34W2lzDue5AYQqFhAHDZga+RSbGHnB9thAA8AsTB2DOAzgLEw8AnIVAD86RYDwCdgx

wNgBFg9YF8FZRLrobhuuwXj5HWWjwC5hcU9KWmE7G+iAABUqAPWDBIXxnzSCplYGICfQ4INYgrgqAAFn4kzgMFmbuJ4KKnmsUdIak8paAJiiEAYWdFlImn9vuCoA+JJSCERoyJYicQxvKaywY/wM4DSgDUD8CfQnqLWAsA+JE07u0iSFdDCBJICe5A4HADFkEAsTDlkDmnAPEyQaSWXSDggfNHoD6AdiGWD5ZsWcwCw4/atChQAJ7vKY5IatIrRs

yZgMQBQmqWRqRipPKbkC4hFQEFkhZWEHlkRZDQHzT9ZBWXFkJZLgMlnrZnKelnTZ3KcQDZZoWSbR3ZsWfzTS0JWcVFi4FWa+BVZagDVl1ZhiJihNZKUC1kPqHAO1lhAUAF1mGIvWb9mDZw2XqajZ/wONmoAk2YECD0s2bxCC06OSuDLZP0KtnrZ8ZFtl7IjgLtn7ZnKZlmrQzSSOLQOagY+4aB9EQqmvuqdHoHlmQyY1EjJmqTWYSA52d9ndA7tC

ICRZt2QNkPZiWc9l0oaWR2zvZ4qV9mXZP2bLn/ZxWVBpA55WRjhg5OQKgC1Z9WVqRxI0oLDngg8OYjmdZ3WaICSAfWbLlDZ4udGBjZ8ufjnTZBgHNkk5suUtnsko2JTmlI1OdcDbZdOSQAM5BqR9knZEySalNyLDjMn0h1qUBnXWt9mdmoAuoMrQR0kuUSTggcSNdlRZziI4Agk8WfLlFgE9MbQS50IGCCOINKBQBvCsGPGSJBn9qTny5E8VqAHZ

LYBtmlIAAH64atGC8gLZBACXl0k9YEIDeIStIyTeIIIRiGjICyMtCC0ZvsyaJI+JJCbZ5mEJLmkA0uZ0iF5siAADc7tO0jTZhSCQD3qEQazk0RsDp0lkiDyNzm9JSqYxisR0RBOFThM4XOEwZ+QcGnHeikHgzEZrvhnoSh74qfKIW2RKVYK60YmIqXxKkfmlyekMXRndBSniz6OJjNnpGbuwwUZF+YJkXBQIxHidMGX4DaaPZWeMmdRSCI4eDMDT

qhYbtrei9mLjAwUa6YmFeZ/kYwlLpJhn4mNYASfxntpQmXCnRJg4ZK59GAsdOx+aLIbcH3BjwfoDPBrwcHA8hTmQYJmuAhRa6GZxmaZnmZiQJZn/A1mbZn2ZjmcHaUeLmRZQDGZcNqBEE/cVMA/ghAEQRYAAIDPzbAh0AgCSAmgCAEyuOhYYI8FgaUb5+ZCdtgkJUaqWZ6jJ4ZEFnp5a9FnkKwa+XnmH5bMkXmPZSWaXmk0PdCbSV5TaCSRbItef

xid5veZ7xN5suS3ngI7eYbnxkPeY3nvCzeU9lFgw+aPkeAIQPTQEhYuLPngI8+bXKL5zJHVAdgwRbnlS5N2VvnH53QHvk/AU2R0UgkUechh8pqeQEVYQmeSvktF6+ZvkF5nRXzSRFqANEVG0FNHEVV5iRUUjJFcWQ3l957gAPn4AWRW3kL5eRWkUs4OxUPnBZZRePmVFU+YSGhINRVqB1F14g0XL5zRTnmTF7RdMUgk3RQfl9FJ+dMkWpDdpSFTJ

TLhJnRQ5IIBnzJyeZAQKFu4EoUWZVmTZnEAdmQ5nQW9cZI4eib/qcxvsvcCvoPRZxPsBtcJ5F+iTppCaC7VitXKNaBi71Cr5aZKYiBzJ46JeVSuqUeADL6hlieCqvJ9GSWkfxOkU4lYFPyWxmYF38bWkIB9adxmC+zaawXgpQSZCmhJ0KRElcF3aVdLqpK0egCSZtiYOkxxhMVL4+hgiG9SiuOKcra9cC4mpmeey2CN5mMhScunFJ/BUbawZJtha

4IA/EJoDKo2mClH4xAzDEm0F7MSeQph9llsa7pGMvzFEyFvjRJqxist/pklznkcyrGP6NSX/iP+qTYbkgUFRa3pMOj76jh3MmXCgZ4GZUCQZ0GSYqZWkui+Htea4W1zgMRjBIYKGFCOwEk6jqLni7kMUOELgkdYQOFKW9VmAYalXMjc6P5k4dOGzhycYWVtecfvwXYGmwKaiQkARn6K0qaftgaVUSQIEbBgqwIXicIkOtQbExd6WBFj+j6cQBvpd

cedFwRc/s3EL+R1g7qJSKEQBkCJg/MBmQEDpU6UulQgPjGRulXJI75K1zHsCZEK8umoPkaFG+yY2y2MRkUWm8vhlLCbQeYkFpbJbAXGhnJRhxMZPJYKWWh/JfyA1p2BYAkil6MWKWgJbBVKUCZspZ2kiZMSZ4V9pwJc6DqlC9qcQAqCaYEbTqJwKpmhhf4HdxYpzFAFH+eumawnuZZSRuluoW6b6XX2e1rsYzZXuUUik5AxegJDFFIp7nE5glT7m

n58dOfkdJt9vA5WkiqcWbMRH7voFfu7pFCUmZZmbCVqF8JYiVaF4Hi1H6I/FRJU7FwlQvAAlpqb8VyYlqWCXdxtqZaJ2xRgA7FOxGyZlFRu8GQJEiGCQCcCHAuMMGCRilQX7H2KE6sczneePnELceNJXJjGJLwE8mslhoeyVwFzPnTaIFHFmp5lCfJTAF/xcAbaHCl3icCluOoKRKWtp0pYJlylXaaJk4x4mRUCSZvIdJnJJGKR+hKJi6t9z4p3A

Lcwju3/NQVDg2mZaUsV0rvpnbR0UXtHxRiUclGpRmAOlHSF0XDLZyFlooYXGFpheYWYAlhVbjWFthfYUzVodsTHzVkBLxCj89mcdB2QUqvamHQbIFbjcIMALEzbV2Ua5kelVKXQXjCy7jzE32uxkFnHQfwGIAegqACEDrZ7xSbRzF/EI6k0gcEECBm8pWfrlWIhUfLlZBYgNkjQ1o0WIRoi16pwCOAJKAyQE5ScMgD4kqAKgAAA1GnlsklWX4iwY

/iECaKgiAFmTAm2OFkC4A4jrEwU1RJGLhNO7WZeCQaeNYTWVZjNQg7aAjxgAA8tGsuygg+SKxTY4hqWEDMmUaHU4c1BNfEhussTHAB/AxAEDjc1pObDgdgsTIwCxIVtKgAAAfJshhYwtcEC1QYgBzQNA8NVEDiOYSFSBQAUOA0kfVX1TKC/VKWQDUS5QNSDVg1ENQGwk14srsVPZcNSsiI1mmsjWqixEOjXRgmNTWySYONcYhy12oMTWg5pNYGxM

1VNQ8IhAtNcHAM1qdSzVs1stVzWg5PNVaR81qAILVGAxtaLVRZQOBLVVZLDDLW41ctYPFQAitcrWq1hderWpIS7NrXtITNAbWLwFdabXs0HAEDgW1KyPTVE0WEPgB210ldmZGwhpNEEc5dEcxEMRLRjoHMRfOYMkGBguRKy+FqeZ9VzgztX9Xpk4RYDXy5wNcmCg14NSHSQ1vtTDUB12AJbXB17wqHXoi4dWoCR16dVTyRwDdYTUJ1UNYWAp1frG

nUNQliEDh012dUA251qAOzU/1+uUXWakJdWXUD11gFXU11UtcDD11cdYTVN1LdfhJt11gAGYd1mtd3W61fdZXjINrFObUP1Y9dbWT109QtFOaX9dZWH0zgQyH2VQiZASLV2ACYWWAK1WtUbVdhQ4UBp/IUvHg2Q4IpBwgq8uGnhilQfnZvKEaeNbXa0YvIlFa04iVZKQuME/53JckJmDXRTEmei1AeeLFWPxXPoWm4ikFVpGlpcKulVIVWVbY7Vp

vJQAqeJQKY2lFV4pV8CYVbaTKUdpwmdwV5+PaUqU0hwJfggkVVsbxF2eRBVDBUJsMPGpGlJAeQa7aKFlHgfc5pZO7MJA1daWOFtpZYSQE87PoD/AyYEQSg1zhf43xhArE9WcxL1Tuk32+6fwXBltkqGXByKjfDBqN41nDCK+/4pHrkGk4joRGNzZauWlNRXvekjhcVjbGdyT+b2Wv5+ZRLKpxvso36vhJZWcBxQ/7D+hrkOuid7YGlCK77jM3Qpr

pBgkce2WXhDcXHFOVLlc7H9lfVvM3Flw5WAxDgk8HPIAQ0Ql+huKM5a6pq6fYO8Qf+mwBXGj+VceP6QRtcbD7bW8EVO6IRbcaeUdxqEReWjKHDWXB5NBTUU1EUeQTIk784Nn2Dl2G6JuGcIz/EFWEZ5ynTKh4FxH+I+YF5EQbaNc8CyWmN4FeY09BCBTBVIFjjaMH2NXPrY1ONgKZZHIBWMXxlYVHBRVV4VLhQRWuhJKpJnzooTSkmLgpBpgoFaV

FW6pK+bAu8pZECMDJxpN5KVaUj6a6Vk4VJXFW4WvVvFUhoEh5lRKCiV6AMCFHgLADPV3u0qQ+6ypdyM+4IOSlW+4qVqDp+4B8lwUYXcNy1RYX/AVhTYWCNpDhB6o4prZqSGt2ootFMN+ovNHZcLgYIlXlZcJZDv02mAkw2Qc8ZqUotAodhZhQmwIniP+u9kxIPsDmCHivRqMNmL/s0YukT12kBdRkJVLyRBW0tqVfS02NjLb1q8WDjXBUApKFQVW

uN42sUa36YCZKVeN5VbhV+NiKYE3mewrVHjduiwQ54Nl7VNeSrB1Zfinicdyj1IcIhliq3ReK6UTL6FFQAdXHQR1SdXnVt1BdVXVN1doWmu5lK5yBqFxMqjHAMgMBCVAFAFMCHQ/ELEzOA2oDZD/AmgMmCJtt1boVuZjqhkRel3mVU3SYNSfDyBZY0T2L800OaVklRJNcqTjFLxaEXF5T2TSBCAlwpFntIsGCI5gg5iPGT7QGcILTLOtEBkix1nN

WnkcARAMmR6AmINhifVVGMmSSAKUMmR2gVHaQCM1dYHEjtZdwgTlPFq+XB21ysDZIHhZwkGgAgNapLwCkaAlGLi1gmABJ2sdhAMmRm+HKX8AEo5tNkB0klWXvn0d3NHBgkg9tB0iVZ8OeR2l5qPGLUh0RgE05DAaAOXVDms5FFntZAAD7c1bvHzWOdsDY0CBwjUFjlvgJiMx0dIODUrV4NatbLka1XdXMhW0buekDTIJNfGRMddwNDmQmdIYNEo4

fhZB1bIIjo1mwdYuPB2wYiHSEVtFUWXMVodGHQ0BYd0Hbh2pFBHbJBEdegNcVkd8dZR2Kd8KJx1oAOnYx3+d7JGx0cdtHagDcdvRXx0tFOXYJ1YNqAMJ3u0onenWWIRZK6lQiFUDJ13W8nU11KdI3UF1qddNCHRadY3YEC6d9QKQAGd+ucZ1y1pnfZ1VZlndZ1C1dnSg180TnS5281RgO52jdnnYp0kQJKGgDxd1wAF0K1QXSrUhd92WF1a1EXaQ

C45wgcEAxdSdXF3MdjWUl0Wt9vHPWJ0C9Ta1dJXOT0mMRd+fiADJpQN4VVmwuYLxBZv9kUiZdcSNl2jIuXUEVIdhXbMVu56HUIg61LABV2Qo+HUFi1dJHcoANdv9ct0tdtHW107dHXQl0dICnUwA9d2QH13Q1vHU0X8dw3deJCdSdeJhidNNTN1SdwMAt1ydRZIL2Gdq3ap1zI6nZt2g52nbz0dIe3Qd1GdsDSd3XdZvOd02dsTFd1i1t3YXWudD

3R51edr3dGDvdnXYF2t1f3bFkA9JDcD1RdYPdqwQ9Cph92Jd6HcalhtLmu+ZuaNlaw2J54JcG5lwu7fu2nVR7QCCXVywNdXIle5Z5Xg2hMDIrxQCafkrix+bWXagM8hkOAxQdXN1L78k4m8pcJUeOHFHyNZHiX5KR5EDTRQAnpS0rwZjXYlgBjGWWmwVFaUy19afySxmcZXiXgVnSLBR439tZVThW+NCpQQK9pQrcCVCN1kQE5HNS2tqVQwznijT

Jh06gniJNgQvGrZgfVek3MxL2nqrDpWyf5TXlDcnZAcAFAJgDho7pS4WelnmeugYxvmbq0cKtTUGWHplviLG5htaKfK191WilznANWkZQt9hMG31HAHfbVYtlKiqBGHNYTcc1jNYCfbGOx5zd1YFllzcuGx+q4Tc0bAtRiagHkrhuMzTltEgYzryKXLmCTiBzWmWjNY4RIDxt8QIm1wQybRc3ux8Kp7GLNyeBEJDgsTQngboU1kIPwDRYbmDRCji

j80blfzVuU7lQLZAYgtJhmC3HW7cSv6dxcyew2xtFQLYWe4j/c/2H+rzlnhPsyNlniihTJfm3DAS5BfyKRewI6gklxkYBXktseF30fk1Lb33vx0FQP0MtbbaxnZVo/f/HIVdaZ234F3bcZ7ctA7fP3ylVVS6G4xTHJJn7EYrU1XPEsiu4bGMBpd1Q0Wi7evpqhqMP4Zn9qrRk3qtVKZq2bpIHVYI1R4HajjjRpPaDmGtKGILx1DoSEZ2w9bOYj3c

adrYpU85KDo6SLxqqeg7ukSfUWDHVKfedVp9J7f61GVtQ7rmtDDQ+H2MNkfWjTR9LDbMnRtl5RCWYE+ADUCaAN0KQD8QFAIdCHOuAJZDAQl4P6TkELov/Spw2ybGr2oIwBVSkZsUFvE5gaRORbRUbzfdEktAjGmnuaqjkRkIwTEmuQ3a7g/fKJVtbfAX1tvg423+Dw/S20stjjeP0uN4Qy249t/BX22lV2FT42xD+FWJlAltVUMBItBBZLbX9RMa

2XVGOStFBHeFQVkPyQDZbtrww4eIFCKZ3FNGE6ZF/dr4atHCVq2VDnqjU2BlosTRLZhgzdb5CxUigCORQQI5QggjmYCmUoDk3h+lPp7MlUavp4EUqPbl6oxKw/pMAH+mr+GwzC26D8qvoAaQZwJoA0gQIMYOotDkvYrI2HUpAybAzXNYxOoaRBYO3slPiC4Kh6wMYRn4+2K6jf+0VXJBmJjyVAVqRUIAgBcJbqF4O9BDbV3YZV9YvCOZGQQ7lVCl

eRqhU+J6FZkqYj7Bd42cFlVXiPVVBIxICSZUzXPYb9tkQ55RQRYbGpUVs6nK2uRTw5GmGoRQxu1qtQXgB3rpnCZxV8jfCdF67GjQLxANJA4/Nz4iI4q0nz1MqV0PL1N+Wj3KVyqS63iaTUbHyC8w44sOoezDYaLrDbDTG1bDFQJZCZMSlDwCWQ1w7K4FBNHtvE7ANCMlxJyMVEFUJQq8SVYRiSaXilPMxkUdqBjHVb/5VtVLRCM0tUI6aGxjC3E2

08WSY620cZjjiiNT9vGSVU5jg7Qv1xDy/QkPjtloykNTtciJI0n+m5HE39CRSvWNvcWYq6hR4LYyZZtjTAQeIAy7TVUE9jYHXThcE0HT8CK1hdX7Uc0xsB0j+0y+euziIPnfbWnZEgEllE9jEwQ2xMzE8PWsTTJBxMe23nSSg8TVEZEHw9RIpONPu046j2r1fSfflqVrrUuNkOqOPxOYogk9KDCTd9UDhiT7E3VCcTUk9GAyTtFpZVLR1IYGmrDm

4wnkXWSeQn3eyuwMqiyoNIMQCaAzgBbjz8PDkMDagwEMcA0g/EAs7ItzmdskxOvgomWrkyPgwnbkCMFniKQCugTDKhMjUBWShNQaUSRQpem+VXJrg+whkWGWiMJnoxVl+OzS1bWNwRjZOtGN0tMI3GOstiY96jWhKYyEP5Vk/aJaYx6I0TLZjPLbmN8tw7QE1xJBFJJnqMoTY9Jala5ZSNyG4LlPKrBuYBQXXkqDGcDKt7I/1WcjrFR2NUW9XI5L

UT1QwGWxedTQAMhlQA2KMgDZdonhfcQNIm6PsX+nGCVhPVJ5EQ2Dio01SKdJaag5TtQFuhZ4BUxrEIwxU0i6AcGbnjDyjxXpbEajqA6qOVxgLQoPgRkU1boHloLS3HHly/mlhaDBoz5q7jEgNNG4ASPIkCHQ7oRFMeVkjgTCBQ7wy8T2YBwM55bxD0yhmI+Hojs1yRpDBFDraEQmMxGipiRVN963fUALf0iQAgCJ4dU9CPWNjU8BM2OI/WBNj9EE

xy08ZXLTBP9TcE7iMCt+I7dKEjBlSSNXcaE7QJJpdzSDR0jlGUpnGlz+M83ju+9kxVMx66mZalDbFZ2O8jPCQ5b+lMrIyDmT2QMJ1wQWII0D3mEiLxMigrs1ADuzns97OGtkqS0myVi9ZfnypKk0bNr184xpOLjQucuP6IYQJJNuzoOR7PEAXswSghtNk+G1zR8eVG3bjmw65MSAQwMdDhckkDAAaQFRo+VwZpM2wEbAMVBehZtyeAlN1U3IHcry

65VA32GNyaVmoCM7kRAXczVLrzO/jwswBMNTQE3CPNtoE4iP+DyI7LOZjvbZ41z9OI/mMqzhY2rPFjQwCxyoTsmeSxYKIYlra1jZAbRULkVQSczET9AWq2yqV7YkA3td7Q+1PtL7W+0ftX7T+1ntzruq57VZcBpCyoK4JdXDkxwBpCXgywBpDQgHwZJD5NRYMPKzGNqn+0PVts09XAdDs36VvVEHUCBjmfNIzmR5cxfWAbg5ANMiqi6vWTUad5PZ

hD6TAZkzmw1yPCHT+0zAIzUfZfiNCDs9DJrWCs8Ak9zUiT5HW0xOIfrHN1YgJIIp1AayNeA2giVkyJWpdqeZgtmm2CxHnipzAHgsELZXSjVddzXaQsh0+Xc3UudH2TQtFIdC8HOML4qcwusLcEOwt80nC0xN31PC/TT8LAlEIuy8oi1nXiL7Q+HNI9V+bUjRz5jLHPqT/OVvWjtu9aLmoAMiybQ4LCi0osEgRC+iIkLxZHSRaLlC0Ys8pei2bz0L

iS0UhiEpi+Yv0T2i1Yt4RsDbwtM1Ai12BedIi2yRiLfoBIsWVL5lSFmpDk04FbjcfToPYz6ANe23tFyE/PPtr7e+2ft37eFPCNr3tG5g2RwD+zScv6Kcp6Wp/Km4nMmYFUEMUmU8fF0xdjDYzvlHCJfHSOibtVq2YYwscxgjdei/GMWxaZY1claVWLPTzIE6S7JjKMXlVpjYQ1BPyzM/ViO8tQ7Yv1Ta8QzVXbzrQhNNehU0xSN4BO6nGBuomSQr

5U6uQ4Qocxk8EVpXz/3FK6ZNcC6eM5NZcJUDf0l4HOD0AfjfdVv9j1V6VXp+007OXigo8AOnpgA8elCKpMuXpLL5yuIpjExMussRCmywvrDAWeGDPDNcOswMZle4wm1Jtc8bboLhA5Vc1Dl+Vn2DPT5+GHivE5VmIZOK0Qm4T0qjA5bG++7K6XPlzyqJXPVz3Aw34EDfA8QPkWQrPFBhya5ANJTWEep/2p6VZTZgxQsg4oNwzm5d8GW6wLUjOqDK

M994aD6M1C3aDO4yXOBMyK6isTYtc2ePg2vyok5qhpQRlM4lK5HuTnet5ICsyGOiWMF9gIFSGPfjo8zW1/jKVRPOizU80P0zzFy1LPBD7baEOdTVkWiORDCs9ENrz/LaKOC2o7RgGSZWdg1Vaz+84uBOoZ6DKObarnn1x4TJ6PsA+eKsWtNkprYyUPtjJguUPdjqCzxUcKuxpYtCTftQ0mTrBk9Oss5MlVa20Rkczxo9Dt+XOMJWzrfHOIhEAK0u

Pzj7Z0uvzPSx/OGVWqSqV6TXC4VFrjNSxuP1LTkzs7Fz07JaKVANQHZDmQN0OZBXQa/e5VPl/kK/r2oqjtTOx6y2A+xZgbXJUpxagUA6gxrWaObOFThs3FWhjEMfssKeyVQxlWNDNrCOZr5y1p4Cl4E0NpoxGYyAlZjK89iN5j5ayO0jTiQ4FOTtDa9Vwwwp6EO4ORHaysCBgjkkOBrt60+f1Wz1CrfN+af8wAvLAQCyAtgLEC8cBQLahbAtkjX8

6/0VrOvlisf9KC1Um8JNE87PoASWfEs6L4qfLmpLTOQ0kabzxRQtabSS09m6bH2a4tLrF+fJXdJCQVsUbrGPSqlp0Qwz4W49+iAZv8dCS9Qumbhi3psMN64xG0FzQyo0vurT65ASSQuALXDbAygOZBEEUwE/kcA77eiDlyQgDXMRTIjYMs0eSuj5UDuaslsAqxoGzYN+CL+M+SRiMG35i+VLhsGA+xN2l+j426LY4PvKBAWGmxyoFdAUvxNUw2Xj

zHyZPMIqbU3Y1+YSMm4m5rbLR20FrnLT1NRDq8+RtDTipVRvjtUm6Rw2Rk07wCjpZxLZhnoxFnSOrTI7uvG4wVloukpOxQ5tOUptsztPjlLW8puOzAo0dP/94o6dMkrZ6QpBrASDBfbnEelrLHOA9W3pa/TnkV9y5+X2ugQVbsinlv9gmYLVvByNUtQFAqlAzluD+eftDoKjEMxKyF+z6dDO/NsMxBGaj1qwjN2rTccjNHlTqxC2aDrq5jNBuoW7

/P/zzAIAtEEwC6AvgLkC9AsLbqbTjsChXMHECnAQ3ojYHAmYEjL1UF3iHicIa5JeMuoCjv3M2oZwJm3gkY5Scx9zInqmKAFqDAlDAu62oxUJrlUz+OIcHW1GNvxMYz1vd2mVQEOYMrU1cupjhG4VURDxVQ8uwTMQ+vNybgrUhPAlV0Pgm2eq231JnxXa/L7IQzqIk3fs4aS+NsjfayRMDrZE7DIVNBwLivXbWMkKNEr92zwUnpJQDngh4U0seHrG

H/urpgANmGkRCrGshzvcSb07WgS7Lhl9zBgMuy81vOBqGkk5KflVgz7NSAyAbDhrK9N4YDZcxXNVzqW67E8G6qx7ELNxA16JTSe9uknEp2stgYvT46QzNiGawLKvPp8q12UVAL62+sfrX68nHPhg5UQP5WEYsMvVh0UP4L6xXYc9vxu5VG9stNFq1qO84n6VP4s7s/njsOrBO4YZE7Lq+eVurj6+MroA7k0kCe4xwETMBpJMzG4Iwvgn2BcJ3Qpf

xfl1jLDDqJOSvZhnxk1plOnAe5HDBF4hyi2Gczw7DkORGSGzRkhoxUOGg679U+mu9bJu/BWBDOa31sjb+a6KXEby87P1kbg0y8uVrc28CVKamsyOqnEZBsmFnA06ghs0xTykrrfsUK5Qo8bLMRZan2PIxUOjrDKeguo43NSnNcTJKLoBEkDSVIf+zPnXIeObocwRgwMbSeznuLUc7ZvpFjrXHN+L6lS5tJzkh4XXSHFk38bYA8h35s3rAW38UNLz

k/H1Pruxm1GfVdoMqDEg7wiCCzZnAI1AMmAuDACsA/URZvyT7SRHPWbKPboc+LDmw/m+4cAKsDVwpAECDi+vq8GnPs9qBwgJaVxDwjHJu/NwjgbKLp/7xqTg+VvBgCka0Efjbg61thjKG0aF1taa5hunL7UPpGoFHPmMHG76ntcuAIswV1PzBjVdrMnylVEO6cHNCdyB3N3oqstlNSwsgsMFjjFxsJ2QUdCt8FW7WFFgJwEMdBQYFqEIBXQzsU5T

KozgF6n8Q5kJUAoTWTTJsLGcm3k6+Bbh1jC2In9t4cKw0oCL0ezBAIEeFgVUaB0HTs2/CHObOPSYfhkrh4SEeH9x57m+HzxwEdBHHxzMTGtgIXkA3HwJ14egnTx3EgvH5sJCezRUfY4EjsFIdUuAlW8yqUOxoJdC1YzHq2scbH79PEDbHux0YD7Hhx8cenH/SyiX+Q34skCouOegcCf9uRxAP4li7kGCTS5Ca+NfsH0eugssF3gQZKR/VJm21AWR

K8qPspPtUfIbX5ElUWN9if314H+uwmNZruG4hVIjMsz0eFr3U8Z6UbfaqNOpMzuyOnb9C5D02PYsTspnsHLG95C1hENocHrtQe8durpCm/sEhiSMt/3VNe1n/3R7j4iKMA7YsU0F4wv7PIjdzpqH9NtALUpOKEWs7W6gIw+e20DOAM1pjYAHdUpCRry+sTVyOjMp+NZNzvEnXuRWqAzPvukRgNXBwQN0FbiyoKCWqt46Gqz3ty656L+Id9zipx4x

n7iukRrkSzYfsMKK5UP4hOKOyM1N7LA9OTxHuhEkcpHGVm7Fd7vA82fEGmwKniV6NWp4pyGU1if53YMMISWjCxZwM0Zyao9asajlqzas6GjcTfZqDJ5U7qQtj+6TtuBlosmCZA9AMwCWQ2oJ8vEzv64UH4Mqat55IuKvmj5NGBwDI4hiYcW9TTACoa/6bhC2EUcbkEp3JCoHiG4mseDJaokDYAAEJoAhNmkaqcYbndhmssZzU9qe1u883qf8+qI4

aeW7OaFMDmQxAOZBQLaSD6nZ53nLKhCAU4TdUITVa6aeQ4tG5E1hOgUF2PNjW20u4On3qNDALlOKxbMcjAh3GGsxp9m9JuG+ShHt6tqONphiQwSJwCwYYkwkjHgdObiJND+iKpc5ZGl0uCOI2l8+C6XFrSoGhHWh1OPX5XiwUW85mPYMMC5AS65sqXalxjUmXAXb6DmXhAIwDXreJ5ieRtQW44dNLpJ2TRJMQIFrBWj6bezP2K1FnKFDgRMHkS+K

WcNhb7YMoxUdi7fmHmClaNZJW3q7Sa7Rkpr6G8cuAT+B50eIxCFcRf4bzjYvMUHGI8wDUXtF/RfwJ9YExeQJrFxQDsXBY28tFjBJ1AD1VTB6RXEJopw9itrQYRdugrb3InLtNsrYwWHb/a+6c2z20/JdyJMDL6efHeK5hESA+xpUCSA0tIPHYkt2ZDDe1WyBayYgYgJhDewsAKkV6AIXB/Zi1XxoHByduAGhDJk5kBpD1gl9XU4NJe1wdfy1x101

mC019VB0XXrFNdcak0tPGT3XQi+b3PXukhYjvXHSJ9ffXYNb9cLrs9VfATj1rbZeeLUR2pMxH269vW84gS+gD/Xh13ST7QwN/ot0klIOddR0l17Rg3X0Nwqaw3j11FkI3r18jfKsX1z9cBXVlXYcx9Dhw+uGjzS+dL/AcW/QA5gg6t/tfny8fJEBCnketuDgU1+3NpQdUgkBjlQg/AesjWjqclbA2aY/7hnMFGVqIXJjUVdQgNiUpAtoXW2qeNH+

F8NuEXHRwbsLz+p+NvFrg0M1d0X+gAxftXCsMxddXPVxvN9X+J64ypM362WPopAx6cgBhF+G1VGzJAasATXLkW9xHMXCQncB7TBUdvSXXI2UNrX73BtfbpW1xIfhkqYFhqg30Sy4jI3tef+qNDMJ+XcS8ld8/XV3mpLXfM5sk+oduLeN4zgE36PSkGOb2PUYFuXZd26xN3dN0miBsb123ckgHd9ZO4ngt/nP2H964G4PnMTFAAcil4OXRO7qR7Il

oZNff9oAq0MIcwpXP6OsAHABssonU+D5I8q3a+NghsW3KF8mt23uF6p5NTWpy7f1ibt2Rd3LE241hNXNFz7d+3HVyxdsXtB7Ekmn1G/BA8XejLQJQbn3JUntVaUFo3TXJ6K8qg6j2Hwenay14OtyXCcutdKX46/oj7GaHRvntFD15TQpIrtOqJR0MkFkAhcvgOECHmnJj5KEAaSHuDT0eOZT3zF4QECa2IWJEDj8QNIEWCVLRrVIu7XSrKQ+b5FD

z51906nV6x0P56gQBqXzD6uyOA7D9Q9SP7RSWDLOhJAI9CPIjyEfY3CPYpOc5yk33f2bA9wuPDJO9SPe1mXD2Q9RZMj3LTUPWInzSKPDDyo8cA9Jmo9sPHppo/cPOj3w/ZIjiII/CPoj6G1LDy0SsNYnHmoXPBbz+2kE2QywJgA2Q1cJJBAguwKgnKo2wEQQ3QIjpgCJApAOR6Mn2faTMf+SoVZhpujCur4ShFA0uQYKawEEZwwZWw8B/7yiGGJi

XYceRlPkN5J3BKxQriK50sj9+CPP3OByLMO3FVwbvO3yMZVftTNy2Ntyzf917eAPrV4xcB3nV2A8cX9B4SNQADJ+v3We0iRE2wPDwMCr4w6lsQH9Cx8yJeEW+wIdoun8x0te53oUXCs39qx5JBsAdkBQRbsslrJu4PCYdisfsYh+4V8xN24GdKywZ0/p5hl6So4NSk0kY3szRlAvpLkLQcj4fSz0SmcJ7l6BkcQcpVtVa6Ob4n09Hxc8jVr2MzKw

3tNW6ZbPsSA/wLIRRRzAMoB4JuA3OeNn3e9c1y6kHFkSeGE6hZI/hKjX+yJujXOGk/oU+6OfWx45xABGA+T1dC4AMAMmCEAy+7M3pxhA5nEk6yuhEIUWtzOXoxlccuq+PsA7j1SXpJ+8efI7ALV+mX7+5dfsJ2V52jOCGd50XNi3pJx89fPb6xQCyWu96i0GNSe2GkQ8PEjGndUd7JjZKtn3OAw4WF5H/mFTBVzzNP3xVy/dlXeu/GNLcMzzlUEH

eax1PkHTaaAkAPLV77dtXID0HfgP9u+8sDXH58NcVjciKtpdw/sUO72nlz5YxsI3/IoqBQBSa6fXzwe1MceuBd4pfAvP/au76INkJZBEEqAAABknJrKilj+l6jgDvQ76O/8Q470Y9joON8usRHzES+7rr+h5uv9DaDi5c5UyT6k/pPmT9k+5P+T1gBFPJT3yL/HFQNO8jvY76WORP/m0vfC3K9+hEOVkBLgD1guwLgDJg1cG7ixMN0AEmnAn15oA

XOO9xFMLxEjsyfLBtXGXp561mCAf9QXrm1yvsecfAPzy2V9YwAQikBZiRUKfuMyXxdFGkSODdKg2U5guywY5jz4zw0d4XUz5qc4bn94Np1X7t0s+e3VF6s+5v6z58+bP3V4W+qzypeHc3O5pxy6Wn3VNKdCe7a3W/3Ebc30L1vf4Gr7Ps53lg976ODyHtf8Xb01I9vfp/qMOvJJ+TtdAx0Ay+NAV0AeQxXojRwhnA6JaKG5X4cg+yfTncNTNRUht

wu2CnrGzvIRQY5bZiTS8FysDDzXiZbf7L1iWqXYXffa/f9BTtx/ezPrt6RdAJ5F9P2sfOb8A8bPoD9x/bPkD+O3I5MD2gpygMo7czvEQ7t7siXOeMmHzpLb489unzzydurX+D4XeEPfb2Mnh+ki4LzjJ8k7e5ofxjwpO43Sk3ZcWPG70TeGHmk4nPaT4ZE1/IeC97ZO1LsT7ZXEnZOy/sQAtL0ID0vjLyZ8ZbOyWGBYfycmJfSnTo/1CTp/+0wp/

soEkRPzLtyXLsgcD9/FUa7sb5R/db6p4m/bSEswiNDbJB9/fRfv9yx8CA3t2s/+3nH0l/B3du7x9BNuz7LcHPhBSc9y2gkdNZ5fAp9J8EprkRd4d+MTop+8F1s3xsWutkCk9pPGT1k80gOT3k8FPZ77+0lN/z+U1Adsx3lGReXx6SJMiOqWyn6ph2b5spdgvAKk0/IqXT/mbmN5a3WXnQ51/43DrY5eD3vx8PeXv2qaylCptPyL30/895MmL3QV4

Fs+q95z3HqUQIGgnbAhAPYX0A5kJkzEAh0MBBrJz7TdAH+gjrcOyJgHDI6t+vla6iZgNnzYOHA66KcCmSb28o342ihuFDWYavsDHynau9G+jPl30F/eDr8pM8anSb+F8pvcz2m8LPGb241ZvH3+x9ffgd1s+9XiE8W/8f574tvljy28c+Zf8kOx5cwV6dhMK+wYLafGza6HycOY2Cgtd0BSx9bNE/B4mp9F33FeIf+nBK+dMx7DTWdOCxwo+gTO/

73Oo7JhSDOS9Qzpr1HEqj13EefyDmO6ecJUOo3qMYz2n9N//mNBNpgf02mG4h2Q9AJUDfg+AAjAcADwZZCnRNw2RDbJnCE9vXkVdjewp4VvzVJyhR8cj6CX6H1S5lahjYR+f9JQdonNGaB8hfe/MBSVdQV/v9R+B/d3yS4iLtz5pZgRsuMmhUGrr1Ns3kA883ol8C3il9hbFxd3XnWsNSlv1ppr24lEuZJpxNOpBdp7s2jDIYLiOC4SvoHs23sp8

O3qp8qvt29LtmgtG/mC9CVkGcj0nHt6miUBH/gloQxC/9IznDt8/DElUykjsz9sqMrZGjs5BhjsTzqftjiFP9NLPa8Eno69dPqwMrcNphJABUwYAAq8PXgKEgrNVo0prWUjyOJ9EpnsBGqILsKqHeQQVs580oN6N9Es6hwxEmcvPt1QfPmBUS1FrsWgFd97bn/9bvsS5WbEQc55rVd2Wkx8l5o1do/gl9vvnACE/pxcoHudxgfv0c6NhWhvpm/gp

0gr4DvCO4JdoTBI5EQDs7k88DbFtMh1rX8avtwF9EKuNfZkGpBxuz9Wvou8THh18zHl19efjnQN6lj0BflpMA2uGRcgdHkI+tE97JhN9Y+qFcQtjN8oAI0A2APEBtQL+BRWp+c65syd43AkAJpNmlHhmfo6nnvEagmGAu4MlweEO9EO4JuEnUFHhNGuGc6ttlARnnssN4PzNBZkNdDljhd43jd937nR8Ivl/covumNzdkWtKLu982Pv4C4/sl8gg

Ts9t5lAA/HGW9xWsyolYlZYhpAbMdgLtpAxCXtjUIj9p3O29ZLpk5MgRp8S7spdwyJjlugKmB7sswAgQCIAQuCA5AgBnMDHtrkxJkfUciieB3wAz99ELCCEAPCDFskiChkN2BhguiDhHpiDHENiDOUnAA8Qc18w2OOMSgcu85UjZsKgboEnLk5sd3n8dBvnoNxckSCfcqSCUQRSCsQBiCSsjSCUsnSCGQSN8pfmN9b1tidn3jalYWhUA7IPoBtMM

oBLwAM5S3m/k02qZ8YoB3BL0kLsGdIRZ/XvkRt5EnIO+i5gvxGjYbUBZh7FN9NgXLYwf/GR9n4hvAioGGg43j4NjgeLNAAfR8HHKACJ+hH8Ldu404vtACOPg8DfvsacEAVA8iCBl9xxM8RctHGI/gXSMeYCO4S/sj5Zdp8RSviQDyvh6dTthCCqAWOtavuGQhKozVkQeSDAgLExCkLEwWAMQAncurlZDlYdHNpO9SwT7lywWSDUQQGYawXWCGwbl

llDs2DLLhocl3lZs2QZEcOQevUuQUPdagTMM2wQiCOwSKCqwT2DmAPWDYQdGAVDgLd5QULc1hkqCXJjID0AFbhLIDABtQFdBNANXA+lrqCU8sb9ooIW0O+o1w3DPNdEpty5KnoUoNXrdow3gIx6BpfEMYlsDyPmM9ffrrsfQWct7vrPNHvqm9SDum9wAZm8sxlADPvvm94/iHdE/v1d+PlgFgYNHcIgaTEH/BSwgVshBCSiO54hKBINZMCDN2ij9

LRPoBq4ISZCALv47IPxBNIHYU4ABpAogFABKgHBBGDtJszzn88VPoB1FNqT9XCuT9trpflU8gT0YcncA4cih0kssBAYsiJC7CuCBTEPhIJOs+B4yP8BYmOblRIZblscHaA5ssUgzQEzRlOk9kf3hVASQNLRXsmyRIQKpCZIfT1BaspDzIWJC2sgbUkeLIRGsjZDZIU2gikOJgzeMwBYsibVcNMo8+aIPFdhHxAHaul1BKs1l1IXMVJIXKZnIaQA5

IcihiaqkVrIaFD6ekDhNIbxBtIWBBdISN0ksgZDBFqQBjIWllTIVFDYMFZCVIYlDYMHZCGTMQBHIWblEoTFCJujKZNFl5DkyJ48/IWYhg6F/s2vi18OhqY8l6uUDehpyD+fjyDBfnyCglsJDCoeJCxolJCoobVCiyIpCFTAlCLcklCUodqwSQOlCcivDksocDAjITiDkamZDSoaXUjciVCFoWVCEcvZDKoSCFpIS1laoe5CGoW8Imob5D5agFD2o

VUs5QXnMZfsvd4nu0DEnoGpKztWdazvWcVAfqCCYArFeztHJDvjiVh4PjAtbpfwUfP4JISNGJd7N+DNged8/PkqdIRqmtrvgH8XAWgUHvuxkQAYx8f7l1NYvrcD4vjACAgQhC/vpvM+PpJlQMvGCSYtBxvFFX1Uwe+MJPm0ZbmFBtQxMRCb5lf1A1BpB1jpsdKTjsdJAHscDjilt6TgT9ZCtu1aRBRClAdRDaIRpB6IYxDuwCxC2IaU9dCpe0/NL

EwKAP8AwgIkB7aCspNAJ9YpgJEpenLv8rcOLCLjtX9Q9iT8fMsXcqhgJCU8kEt+IGPhzYL9UBQTsVe8nT0+TKoopeiL0aUMuBy5KiBxoTJRskMMETEJCgiQMCZkUKlCAGhawpoa5DUivCc7joicfDsid/Dq8cgjmR0pZKEgPHvdD+ugTkI4fUpynG7lGoY1kc4Yw9k6rHDNcs1DXYY2C9LjCcgsk7C/4C7DCQe7Dfel7DQIj7CThFsh/YSY4g4QT

QuwWHDzEAXCfJJ4ho4bBhY4TVD44fGRE4Z4dglkic/Dqic3jvIBcalnDfqrcB6HrnCxeuFklaoXDeIMXDboaXD14Uo9y4THCo6KTkfIeXDCQQu88RCyDRwba1zHhOCDDpvUjDryC6ganlG4XcBm4W7Dz4W3CEOh3DSeqKk/YW8Je4XMVg4QPCGkO7Qd4SPDynBXCz4ZPD5IdPCgTknC54SnCF4RCdCwJnDbgGvD7aMfCxIKL0eOtvDI4UXDUOiXC

4kGXC8EafCZcvdkL4Xgir4TYdArjE9grnL9Z/mvczcNLCqIdsAaIXRDNAAxCmIcrCs+ratVAYags9sTZQjA2VxIv1BmFJmlDlJollzq09aYkRkhBmzt/Yjb8nfmFBJ0gGFUGNuc2WJ78R5jG8v/l6Df/m/dfQW4DmWmBDQ/hBDw/lBDI/jBC/AaTDIwTx9KYQD8XgW5Uo7p6F2IRn8EwXLZJ0lHoD+lFUWYWwIBBjMAcwGS05jsQDK/rxtuYZeCo

3H5pjgP8BZUFdBtQDUAkooT8uIYgwP+t6csgSYYAznQCIXgwCK1vHswAFcpfxOzMXmAOdh9nR4NEZ8NtEYOd4dtwDEdtPsqXu6RDwceDTweeCGzugYVXoNZqdH5VqZhQhcprvY25lTIISP35qAsRliFKK9G9uK8FVugAfoTWc6zgb9Zzp3tWXgud2XlnEnQYGJSbBxRHwUHE2PIjYozo5J8YLUiuAdNNR/sIDB/qecLXg3EVBta9HVnfsbzsTtJA

Z9DpATN84kQkikkSkiAYct8QRjX07fhZgp5LSNQ1g6g0iOHgkGFssYKDlpeqpUcdyK6Ce+o4CQvl8kwvqcCQ/pF9AwZBNCYdBMVniTCIwVx8owcNNUvsCUoAPgBaYaE4J4AuVtQmrdofuj54gXCBIOMgxOYaCChDuCCKAep8iwQ38iHqjhkwPAjeUuI9O5Nyjr4ZocufmUCLSPa0+oU60t3tY9Goh6R2EbLDuEbwilYaxDphmesoCPyj6EdL9GEb

L9vzCwiFfpmUbIM/RgINBgmXoMC/Vt+IwoAQD+kYrtudvB9d+BWFCwonhZEYpFoxBfY6tjYC2tqjDv/kctvQZjCTgSBDs1h4C8YV4CCYQaciYd8A7ETiifvo4jQ7lTDUmPV9U/uhDeLhtglEv25T5jhNWRlwcBntQFw8AyjlrqRDICJrDtYZyE9YfWADYcBAjYcmATYQgAzYZ/MOIRe1c0SPwOAHZBMAPEBTMtLctoFMA7II0BjgBwBdgCQR9AAO

kzjjWjfgpiskFtbCskQnZ3qmNFSIKQAv4bXDW4UD1UiqjdL6uNC6QFBJUirWw/4HOjPYWuCvhHSQdumRAa4f2CSUPLlQINSBe4SHQIkNujjEMjVF0V7VKwFSB67ryiIAPj0p0TOjD0VQi/sm3D4yDejwasV1QImuio6BEgf4fOjL0Wbw90dKAD0SNkOAMejgEYHDz0WPgIMbI9r0Xzdb0aRAVwAKiRwXJUxwQ/CxUU/DqgYNCZwcqjn0Sq5X0Xlk

gMZ7Cv0chif0W7k/0UHkNWPBiyMViQQMeeiqMPujL0dBjT0bBjd0fBiQMUhi0buDU70Whi1UVuDH3juCPoaLcdPjN980TrCi0SWiy0RWiq0WlsBljn1MvI3M9gK4Y5yvsBedisAxLjycwvHycFEgqFyfIrsj/qs1HBj09h2NvJqkdnsVfEUCkLoVd9EbUdlTvUcMYc4CfUX6CzgQx9A0S98MUfcswwXBDYAeTDowTgk0vi2C0Ie4ijnqtsJdj1Ip

pFRU4YSJcY5Kyx8vNmi8wSsdXntk1b+nG0gQKqgiCHABtMPkxOIWQDuIV6dWUf8F+IZHtL+s396AcStGAeWEjMSVZCAgX1TmNAMwOFudrMZol9zkOcXCjwDGkWytqXrMiqzvMj/oUsiWvPOdSJIudqdJStcMvOlVtB31yrD2cOdq9sBzpMjKXr1j3SK8D9UYajFXmnEiygKslzpx4YylmBe/AfwXmmAx9sXjBDsVstIqMa8x/iIDsdultrkfatbk

bfskIvfs7Xvwkn9i8j/zNZBssbligfj+shgWDY91J/wgaAlACGFssUtAUQ32EY0/REmUPwcZEoUfBskYegcqpgYj4UUcDvUSYiq0v6jhts99LgV21rgaGDiYeGDY/rijI0UhCw7tTDu2H0d61gmjvUA4NbmKQUttrW9UHvqgYoD1RtAdmDwkfwc0gRV8MgSyifSjq1NPiWCKgB/DSkEUVL0Q0lRce7CJcYUCuoaUCeoSKi11rOMevkJoJUcTd3SF

JjC0QgB9YYbDjYdXBTYUqiRcugApcefCZcY0ConnZM48u9CQruJi5/oGpLINphDoPQAjADUBMAKik5bgDivKg9NNgJQhiMinJmcerd/wDFQ9yF9FydOcRqKk6igXoVNldLCjPBmjivUa5jMcdVdgATjiLgbcsfMcs8/MTH94IY8DEIcEC0vkaj3gakMy8Dn9mFAFgDZog9E7qndO1t9NVpr9EwkSkCyvjzjYVnKp0AA85G0c2italMA20R2iu0T2

jDoH2jzYXNVJYYExjgJgA6vC+svrtqAYoMBBgIMmBZUE+chgJUAh8TlFh0R2MZjjbD6/iC8mUqjh8elB1qutIBBaOzcnAJzduwC9cvLk/UAAOSwYJm6Q3bIDS0OYptMNjryAY64ZwUXrxAeXKNANWgsANAAH4rjra5esF2QNAAj5MfIJIRkg29KLIiOKAD7QLIBesG3BMAPKGHZGlBRQ1AB2QfVhCAMTqRgaIB+Q2pzm9IsiqiMaFvZODBzgJvLc

o7QBn1P0Cj5Pmh2gSvJiQMWpFkcpzP4rXKqAMwCjINWiXCdHj15DXB5AvfFJFZnpFIY/Hw3M/GI3MSZ+1a/GpICG6psW66P4znov4v/Hv4z/Hf4uQlBYUXr4kQAnAE84pgE4xAQEixaJIGAnK5VADwE3KE4g5AmJQ1AnoEzAn5Ie2jxIXAn0EtkgEEvaFEE4DCkEhaExQ8glPZQSB7ZKLI0Exh52E0eFEo9RbMEvy5i4dgmYYH6p/49DG3wzDH3w

3qHrvPn6So1y5C/dAC8EtYr8EwegyPJ67CEuTqiEwqLiE2/FSEh/Hy5J/HqLX/EqE9rIf4p7Jf4z7rKEt/HtZNQmxMIAlnFUAkVFGwlmdSAl6E30AGEowmIE32FbIFAloEjgC+3SwnkAawk6EiToOEo6GBsC1jOEwopkEigleE6glQaXwlRZBgm8QJglFZFgkhE64AcE52oREoTGvQjVHW45hFSAiTH/mTaAzOSyD4ASSDEowRz9g+2jbJHIhLkV

PBGMeGB7qdDIrATwi+CNwzWg2GAGyBUKsnfwRZtakYJaPK4oHSeTABZezlUUqax4ktTZ+KTLQxT1FGI0L44zFAqGRNo7GRf0GoQwMG4FYMFxokH6Z/KQb+IpB6oAU/D/AuLQQwhlRMo5gJqfA7YV/aCG9tWCHZ4gLG54uTabtfrCbXO2E32It65CKewQAXci4Af6AL6ImwCzYgDjkUJjbAWEC4AHgBrsSEgIASKhdgXQEUIBADEVXkArOTJTrOG7

wuFatapMRJLuSEBz6gJrCCSBlB+8P1h5yOyodA/8zt4ptEto7vHmQdtGdo7tG9o/tGqwh4lR4ADbkDHewQcQC7/gJbDolTRoAHVPDyI3gBf5d6SHeFoJzTczHuaaGAHMb2KZeWA4yeZHEXfVHEAQ3A4Y44CHuYlFHnAtFH1Xekm+Au4H2I0nHwA4LHAlB8rIAzfou7YT7/gdz67kO7TEk7bYiXW7RNPTyLJY5vGpY9iFXg1Y7KoDX5EECgA2QegB

T6ArFgg4n4ZIkrFk/apIU/UoA5IyrF5I6rEFIrywhkhhRfRJGg5TacpKxGMkr2OMmLlfv5MDMc4zI6AB6o7TAGovy4dInbFr7LOLb7NbRqNftxZg4ZFWWR7DfTEawoZZbEdla8IO4p3Eu4t3Enk1faqvYySeRX9iSeIrSVaMQbPRJKZuEFaYRxFsqHnGGZfpW7Fj/K5G6GS853Il7EPIh/bvY+X6vvMuBdkq3A9kvskp/ZnY/7QHGrfcvS0o4hSi

hLb4+k8qhtcTTFxqPk47qbqTHfExLDsM76JklGFjUA5YclREkt6RFEkHZN6XLCxG449PHBozFFZ4+4GFkp4EEowka24ElFLBHqSZ+ODZ1kzYAjuYGK6A6WItkmFYrXPnGjLKqhjovsbkOKdEnFd0CNg0nCDFR9GgQFVzS453IK4Tu6LrTn7dQldbdDDOg4Yzd7JsdXH1ojvE2knvEOk/vGD4hUB2PH+z6U03GWU2NE9sUb4HEloFMIrVEnEu3F+a

ZVDCOQ6A2QK6BCzL5E59coJLkPMCqyZXQEBcik8IOIDpeWlTOKIMlKbE773JJHEf/bYFsU1DYqnYL7o4xPHpk0xGSzbHFPfNPGLPHwGQAsNEk4iNFFk5FIlkyO7U45g4VvfJRAyGux0jLMA7bLWQdcVJo5giJFR7KJEWuSoBj4ifE1AKfEz4ufEL4q1zL46tGRTCWGrHDgAwAL9B1ZIgjHQCLbEAZwD1geICXgL9CVAfQDruFfFKWH+YVAXYDBTC

gBFgTAAIEBKBSqbmRLJTQCSALPC3UhwiILdfGjoyEGck6EGp5OGoiAE2gtwhjHCkBUwVMOCAD0P/GC0Lm7Lo0hHYIjeEnw8eFnwquH3QuhH4g3fEMmB+oQ0iXJQ0quHzo6eFAgeGkLIRGlFIZGnFdVGnkI6gmY099Gf2auG40xkFyTNr5hHbQ7sgpym9fZ+H9fWx5JEp9EE01tDkAYmnfw0mnkY2GkU0hGlpE2mn7w6kDQ5BmmwI5mnvCVmkCgzc

FhUq3FPvMTGr3HVFz7BanfWSfH1gafHLAWfHz4xfEbUxTFMnIZbw+MyS6reNxfof3YXMB7CAxakZAyBPAlHTXD1cd1C7YLiTZJaFGtcZZqjMbJxASGM52Yr37lU1+IpkiZ61U7Da+ooAGstASktUiAFQIRkmiUzqniUmMHjtIQA6gvEmkjCLGVkwXZFBDnZUVHREs4svD/aE+JxrSS4bTFLGkQwpgxIi1zAQaEBCAZNrYAWbKpIwrHpI4rEC4srE

0AmanTk97SYvMABvOEPCYTciwAFAOlWUIOkEwEOnh4S7zHIhHbgzHrG7kvrEQAN8nO413Hu4prwLhFfb8rM8kTYnYACDF3zJ3RRTFKZchpJcgZCrDYLPko5qdld0ixUzQDxUxKn7A6ZrLIzpGarfKzXkqmIN9fwx8vBIAr2B/yq2I8JKJa7HnIvgFY7OCn3YhCl7WG17OrN7HRec0lfQvzQt0tumXgDumObRuny3Z6yBgcemIySTwfKMGHbkR5rP

KL0RF2VYARQOHGjEW/7FU95ilU+zGf/RzFow0q4J44xF1UrHHmI1FH4w7zFCU3zFE4/zFkwlklBY7qmSU0D5F4mO70jAA65XcOlziSirxY2lTUIBwZqU5Y6Ww8gFaU4hljklTYTkwSESASoBpEwQmUNQYlZEhpL6MwjoCEsHBw3TIm/AXSSRE9r6sgmImK4xylxEvoYuUvr6LjKoCG0owDG002nm0talL4w3GC8Mxk1dCxkZE0/E2M3UmS/GPJa0

9DxHEyKnPI04mBqesCP9SyCYAUgDmQZLoe4k1G42IjLPbLBiY+U/oShKA7xydwiraLBhltRnGRvV1E1Hd1GGIrinMZJFEJ0zEk5GUba4kii6E40NH5k8NGBAvPHPAgk5CAP7FuI8IG04xhRwgVWw4QxaBq2UY4/KSKhxgW8icbLnHYPeumzUy0S7U/amecI6nVwE6lnUi6m7AK6k3UzakyFC2FpIjfE6UnfFpdYSGi0xcF80auHxkVia+3eoDY4P

GoANQKm1wpmgBZIKGXMisEDw25kKme5n2IJ5nJ1V5lvo95l2Mrmk93FCAzjVSb93FiKuU1+GzgoSFQdK5mVgm5n3Qu5kxZAFlA4Z5mwYYFlhZUFn7E5YbhUzVFWpBJnRUi1wZ2ZQDSCI8YnjMxTWIe4l73cRoHeHPQQwi+JFMk5hhCFqoF4OeS2g9AqJ4a5hH/TjxeKJID33MDjkDcHjrkFubVMxU5jUOEnYHGOlUfdhnNHVEkjBLNYYFHU4kXbE

k5kiRkYQ1ua2YucRCrCgoAraioMU+TYFg/nHAgkNHp0gsmZ0lwpsks5nzMbknvyXkm7AaEDYAaYBzoZUmaABEDEACKCHAMQDQgQchiATiqfKJVoJITQDLAX4QfwNUm36DUkQSbUmpRL+Tkgg0mIAIvyfIU0mrWZBmfYywxEgY4BCAG9oXg/7Emo7MSdwGDgv4NYwoPQPHA0DuDRpf7SBibNrZaC8iTAqpkwk/8EIkw4FsM5EngQ3inEHcCHJ0tpm

Ws9qk54vFHfHbOklkuMF7zWnGlhNXTOg1MFR4iukcwACJsBAPFZ3Ra5N49SlqM6sLms4Gn8jUGkSAYERokvGnhkfdmKBUcY2Uzmk2Xbn693R+G+LfmkJzQWnDQ9ADHszWmEs7WmiYm3F60jClKCAmhTAK3BFgcyCuIwph3EiD7H+erZMKCDYAzFwYkM0BhLkNLwNSbuYpgu/57aBSDl6dNyzM8vQFxSN5ZwcwZvESTytUKVkYHF+KysupmfxQfoD

BZVnYwirAeYgMGeJHEnWIsIE040H7baNgKe7OCy4A4YS54FqqxlKknTHIGnl/QKLCUgRlMkoRnDspZmtkutEVAG6DxASoBEEfQD0AbADagZVAaARIAaAGyBi00gCYAU9oDoranHM7dm9jWqL/fLuy8k8cjHkZYDYAGggzABEprseKCaABJDEAAeKaAaEDLABoCraA5ITAocAsgaNn8FWNkxJeNk9aJNkVAFNnRxNNmEQDNlTfVhEVAIsCXQUgCNA

bUD/AebS3EulnAcmjz9IxSBFfd4iqOSkmVs64jZTAKppeQFZBksuxu+azCkGJNKFM6PFhQI8i6yaWIHAcRQtssbhEc+PFIk7inoAFo4Hsqq7tHKjlYkmjlas+jn9UnWal6SmKkfeLF54Sqh5bB8gatGkkWsgTmdM7FEdUnpmsk0ia6c1TZL9UdotQXkmTqRICOkAWa4ALHyg4uzmRQaEDDAdC5bwbACaALYAIAPBwimXAD/aBwGqkggCrOdaDecr

Ummna0CJs/UkBco0n7IYLkewULkfYxJl+aNZnTxDZnHU06nnUy6nXUmllKDURoFaJD5hieWyn4NYABiBqSAxaLHIZBfQRVMYIAxdbZZaOxg17J36nyTYDkMOlZJ4eGB1c5Mlts6qkds5rkWI7tmNU3tnNU/tnTcq1ndMwLH4o0dmSU0LES2IdKF0tAGgkKrQuoCN7EkkDYFfQ7RiGZWIqM5H4rM7BlyuC1yWQOCBXQaQgpRdnSDk7jlWwkcmX2W2

E7s3/pN/dv4t/R8Qj0t5xY8/yq06XHlHhJF4E84bzE89z7bkuVZNIzClxUhKlJU4bH1+FZFjYtZHU6KLGnkHBhovOLE1leqSWDcgzUFJnSQUgJRD/KZGxxDAbJMnIJpMjJlbYuZpNnd3m/k6rS3KcpKk2XuDSGZPk1hHqTpU8uIh8yKwT/C5HwzGBkXnOBlIU8FooUxBkuMTNn/c2Xny8xXl+AJb459bMDrALZqEMScTOoM0GOSH9jWWO5pxqDV7

dSWp6I4snnMMj1HtsprkNMninB/PincMrzF44mL5M8wdnMkkTmvLcnHRogoFlk8t479WqQd+E1lyM28YiXfvwxlWhmc4xvG5g1skbsgThbstlHb4mobx8Qmli01Wn4kM3EmUwXjg0h/kWUoylWU9mln5SzbRE5HqrvUVEuM99xbrdxk7rQHkHUzZnbMsHl7MiHmBMyDz38jXLUI5/myg6Jkvs2Jk6099kvvFUG7KDyY2QG6DAQSQCF46JE4Mwkq+

CbhADgQu54ZcGFhpRuZ6yUMQeEMtp1jaPE/g5GEOY2pmNc+pmkcxpkZk6flZknhlz81743AmbnE4odlk4/PHAlIgX50hjmZ/deIboJuYxA5CB2YRJqCDYl4wMC0rcbMTkrMyAg7HEwqu4wgBTADgCaAK3D0AeICkAesDJgcyDxAZgBOpP6n/tSyyJuC7wkJe1m0TIJYyUfACtoNpB80Xx4aPTh5aPKLJBPPR6hPAx7vM+XKO2bBbeIZADIAAx4XZ

Q9EpIUG5bIcCDGIUd7WIOTrIdcgDqPY6F08JcABsCeGuE1yEl5WZBImfdHI1TlI4dTgDKAceF0kVOAkgTxDwoFVweCmoWhFIKFuChoUS5bwX+PXwWBPXh6BCjpBhPER7jQsIUngCIVRC4R4xCyDFnXGmn+IZIUJJV4pRZdIV+PbXJZCyGq5CtSHRQ/IXFFQoWJC6gnE1UVJlCjJCVCyXgm5WoVOIeoX2IDpBNC2XHd3S9mQs+y52bFXGws0AUk3Y

4hk3YWktCzEheC1h4+C/uh+CvmgBC/h5BC8J4DCyWpwAYYXRCoKkTCqxBTC6FCpC7h7zCtJCLC3XjLCuBF5C/CQFCzUhbC5hY4gvYUVCs3jVCtiZ1C0QBnC2YVaiXOZoC81IYC44mks8LkSAKV6aAGV5yvZQHGo7ZKVKcDY87JkqI2H4E4lZWI1SKmKLqB/xcc4wHbaRSnQomPEKnAjnsC+VkuYxVkEXKfk9s/ikM8ujkE4qP5dMubms8kdnFkwk

b0AXqlhY4ZmMcjzAAGSIQTMpow4QtoxTySDjHiCXmRIu2yt4m8J7vDH6HvbH7HvPH7FPP6nqwi1yPU44DPU16kfhD6k3OL6k/U79aXgo5nD41Y6Sc6Tmyc+TmKcjiIqctTkac10Xic4rj/AIYBwAauAsQ6uDaYSoDLAOyCHQcyBeUSk6NAegAFsoMWzVXaoj4iAA6CwgB6CgwVGCkwVmCiwVWCmwWHMksUYrOTa0FBwXQXDXlb43t7ZA/GmyoCwL

v88pxaQsJY8pVIpzFZ2J80asyoAa95/qbTTrQ6BpR0Od7VwQei4gdkj3Mnzry5ccUIY+bLQ0jpBYgqUGByDcW0PAUECE75mhw6uF7il7IHip7KbijEHNQoDTsdRIUpkB8UJJV9SSgy8WGSHgmoAPsU+wE2iDi1KHDitYoKmMcVR0ScXTihIqziw8VeC8d7LixxA0EgbJHo68VHi2uGSVahFtwi8WK5DUiQSrcVH408UE5c8VvijCXZALCW3i3yH3

i4Sb+IGlDPizACvijpC0gjJSXC3/nhHLDGxE5XHxEuFlDQt+FBLb8X5ICXJ/i7VjyLEcXxkYCUTi4XJTiwd4maYOCAaYiXQSy2gC9KDTwS6MBYSwkEoSj9Hzo9CU5FJSXHipxC4S1Fnlw9SXPaYiVUgu8XY4B8UUSrZBUSmiUu1d8Wd2e962HETGOTXWlYCo0bk3ZgAr8SyDxATEzaYOyB5PXABAgK6DMAauCO2eID7PTKJG/T16qySsJ5bLMAtP

SlEXMK9JUUxrjpuc1HdSNYD/7C5JJAFzB8nWoD42BhmR0v8E+/Cnl+/TgV+DeOk8CuUUz81pmKi9pnKi2bmiCrqmEVTUV50oZnc83UGeIumG7qFTLfDKvGaWDBQUFNKbEpVXYN41dln89dlpIlgIKXTRl8Q8cn2wqcm68qrGx7OcnBycM5pSlWQOKLKXD7D7QDNZAYr04f6QMgf6LBM5EwUwvkmvXnDiA/9JoU7VGfsiQB1wQ4xa1LX6VAGABFgG

oBXQeTk3QAsVsAS8C1rANJhSgUKJ7bzI9wO7ipyRC5xSvBnIZF1TeiUU48eMwZMlP7QWoSKA5S4fkSiwqWAQtMmlS+qk4wvDYBoyqVEbXMltUlUV1SrOkai7eZHQQT7kjIhKLgSNK7bHZFUokT5sc7eyZHCia9CdQU53c/ljSyblLcnRkxeQelzSmckLSkM61ocyTBiGGU5KOGUBWTaWdYuTbdY3aXHEEc4CAkf7QUqfywUiBliA0EC6jCQEXSqK

nUi1/ZPUl6lvU7YC+i7UD+i36l8hJTGSOb9gxTKhBg7M+7h7IpmRpRSDvSfKnHiGumIcgGK5JeyR8eXbD12D/hhgd8oQ8OGB42MUUo4kfnEc7kolSmUXIo3gWeY7GVXA6qW2I/GVL8sQV9M8O70ALElLbb5YrbSskf+SEhQMBQUPAQaXdSmH5sIJKZ+Gf3bMy1IHqUhulqcQVQWuQ6DQEmoDMAaEBEECEAq82hQjokckbGTXl6cvdI68wpHD0tv6

FI5wCuykaxIuNLyey5LzCIuQydGS9DB0/7ZQvDWLwMPPRAudJLAxYsJGUZFxZ7X2WcCRGS58raX17Ms5281qwO81+lx85V5f04gx97cRQUWCHxRic+V2MS+XiKB1C2YO+loDB+llwWkX0i+V4ny08k/kuxRneHnblUcZYxQWWKjSGzA1k4Gbn4SEjgMo6WQMy5HF8m5HReeBmvYuSBPI23FayiAC1yigD1yxuU8RfCk4MsPAVaJ2Ubkb9ABiNPQK

xY+65XT/zUMnbBWAmFGBypMnByjgUkcsOXcC9GWgQ3GGp47MneA1On/3RfnCcxOUSU4mU3EjfkfAtUBaIzKW8QuRmci+dnAzbl7h0suVrs1Rlsyq/mlY6aWl3JQSa5NmkNffRDEgz+yaK4oFsaH/m2U+XH2UgAVK46FmWPXOhq4x4XukD0VeivWUGyo2WR3F4U6K94R6KkKkvQskV1LRUGOS5UHOSiABhimTlychTlKcmMVn4uMUmym2nJcm/ymD

E+LZECHhaYgN7wwdRKlEGazLNDk4KheLSq2TAFeuaeSIwxubWYIVbEZBxSIyiql1Hf8ZSiztk082UV08+UWcKoNEe3IQXM81UXCMtnlEygk6CI3rnlki0688qGDUIR9iK6A/qTHAJGuRfi4HAeqQPPRZlKfZZnWirJkIrCoDYgTpz4AXTiTgFuWmswGnty5wXPAWaW9yyF7gvcMoWYOeSScSdQefIyiZ7RhQ+4rzI2WMbz9yxWRHKd6RjM2ox/sU

cnEyEYD5KpLhhiFewuYG3mr06ZHr05MDfs39n/sr+Xfk7pHGSJhSpyVeTtNA7zUrbAzgqjjY9wNYG1AZ+XlnN+XSvWV6fy5l7eyJV7fy0FV2KYin+GY8jdCYZbAK45ThCM7z5aTjlL0u7yHSxWXHS6BlKY2Bnz+BABfee5HGGDWVUi/WkSABZWNgZZWN858rroLW5CDTTGirTvnhpa5SOoVYyfNCFEhGQfl0Milp0K1inR05GWpkuOnhyppmdclp

lkHKqUDs+OV8K+qUr9QkYUAJqV9Uka5cuAGZH/J1C1jE0Xr6DWQtUZK610jQWjS7unjSuRJ901RW7sk1o6SmhF1wx9HCglFneqsFkXs4VEUiQAWsS1xkDDbkH+LMuABKiMXBK6MVt02MWacjVJC0v1U/M3yHPs5oGvshyWYC3xXi3CsVViwwXGC0wXmCywXWCw1pnRDpXLfJMoxTNna42FOTaUopmkK6iqR4Hzy+8n4Y3JM1HeldjwQHevGMU2kp

xATl72o0BVwyh+KsCphlIyg4GU88flcCyfkRy8qV8C2fmCUhpUdMppUEy3pkCK9pWhAqQUoAisk9KlSyHKrfQH9YcBdVbD7juLoxTU7nEVyqXlVymXmWiNgCVAXYD4AY6qXge6SrK2grLYCGElBTZX4rWgFD03ZW5InZKdq5MLdq+A69qkoB0lQdU7qc9goMb5VivCPkSvUgC4C/AWEC4FUH0n+U6yE4C+4kEYR4BzDCXEnRNPKhJ4wYApVUf7YF

+fgErYtekVnNFUMi1DUJ83bHU6KQYhibhCK6Av5Ns38mMa0yQsa5vmcA4fwKy99J0qjHbwUkvlMqllXIUtlVIMsLmcq26wPqp9V2QF9V8q/yBBGYvS9hE8KZDcGHEZTGzfsV3ylBHlmDHeNZUZRhlR09ilobH/7FSrDZqqsqU1KiqVaqnGU2Ihkm8KhxH6qh3aEjSJmdKzfnWMPsDZgTyIsc9ezUJIv7OYetnMcy0WCHVuWVfDRluq7Rn2w3YwkS

xh4PowXgxatS6BqoVEK4kNVmKmOaE3VXFuM29k7rfNWiEasVFqusWlqxsWnrI3EQABLXhADNWW49AVvsykWoKqTX+KowDmQYciXgIwDJDJkWyJIKw5faNIBCSvoJK3gD2SXwS6lDvzFhS/A5aE1llaZillU/KXk8ydVFSphXmalhWcM9hVNUupW8M5dU1SkQUJypzVJ/STKvU6Sm9uDCZ0qfWYSfbwR0yt7i3kanwZEYLUVY81yWiTABJilMVpij

MVZinMV5igZmFi+MVaC8pj8QZYA0gaUBFgTQA2QZgBOyfADbASSCxIGyAoJBTFpY845Do1sWenPyKb4wXFQgjlGnqAgCtCvVIs/cX5s/Q9kVAN4WeC4VIASpLV2Uld4sS8xX3CqoHOXKNXws5VH4699Bi/OJAS/FAVNAqrXkimrXxMurVXS9AD3a5MWpiuCDpizMXZi3MWKod7UFs5nb3YyRxnxVkVXTTLyvKa1F79cuy7xXPBgFYPB+xMySRiPq

SgkqMmZ7L9CJuezAaAkpWQgewEhyk5aO3WdW+owbbLa+nmragQUZ4t77CCwRmOawmWiM7eY707dVdK2fSZy13zrGClhkFPVnTM7bRvbJ1BZoh1Usyp1VDknjkjkuv7I6kGna839U8yvuUPbKygthGDn2YB/y5aF8YlAN5zyIf/aHaI5ExORHwj0nJknKZhQCePexsa1M5uRbBh5gXvzEUuGCwa8PnoDCV7vy9FWMijvbrebFUgq5vxtABZa5aSM7

vUPPA7InWSqOd1C3aaDiwHZFUHyiQA3QRrXNa1rW0atl70a4yQyjQIS3KCJzfoYfaWYUjXUqvjXVxM14X7OBWPYhBVl89QZIKjhQE6YQKpzGGiCA7UDMAZEgxIMBz/NYgC36+/XKgAgBmkyTVc6iADHQH7V/ahAAA6oHUg6sHUQ6qHUCI7ZLnEffg42brUqyLNpw2SKAwc9DmxQfJlOoyikhvSdIf6V5jv8NiSv4A4CHyNLyjqlilsCtikBfE3Xl

Xf/6uAvuyW6zGUcK/gVLq5j5C+VpUu6lUqUnLdXNSndXdK35YVvMOLSnSvE0ymozCs+LE0IJ6ai7IaV0k0Tnh61XkeZYrEPkDkla8p7Q9ypgH8KG5XoEC+zNBVWxouYpVviBeU4GkYSFhVWIlnIZoUvF8lxxGfVNawQjz6zFUd67bFd6t8KQMFsIVUDvzt+DaX4lTDXB6lpqE8/bST61bGJ9YqBGACfhuVHlZ4DHgZu8pfV2KV4hUBSKCg4iQz8e

GFV2SNDJJcNTGHAO+JQK2lUwKovkMq4TWHlZlWtxU/UV85BXsqznXYC9ADLANgDagZQDhbAmYKajbBukghjg8FsJa2d4mVEfZjgMCfacJLhAKheSLwHDbTneSwEughVVEGmEChoeEmzalGWqqxbXJ4pOkKi2zUhg0BKxMGyCOpIghAgXcixMesBeSjSDwJBpiPBBACLIxrBwQWeKVzY4B2QeIDDOGkCaAdZL8QVX4dkddj8K9nnFjD+j7ait79gS

lZ5/ZCDRpEdzrGbnZk2UPXly5Y4JisOC/6/7WA64HX8QUHXg614GgGpsU7VFsUX8l1WuETsUx6uQ09i8MiT5M1pDZZRZB0DcF5AlE2akNE2RLJsHWHayndUYcFREpiWOMq9m80qx7sSgjGla7E1C9HoCELfE2ObWyUMIollxMklmFGvxXHQIwXKoYYD/AM4YcAc6mu2OyCxMIwAUAaECYAOBSXg8D78RIFTvDIFSdST6YSqmz5Z6LmDcIHYCuGKy

wY84yLxiHAy4GE5gziD35yqn5QQG84AAqVGBbNf/hjqozWVU5zFOA6UXjG55jNM1GJgA6Y1KirMZ7Gz6UwAQ43HGySCnG842XG4CDXG7bXIQzQDT8UmXBOPdXeQPBgYKeGVbbZ2Xzs5cpocw7TXavO5ms6Thwm79W1aj9lFGiADaYIsDxIr1KbKKo3baHPUAGXLz1SNyJ9aw7zn3a7STqApSW/GA6TSibW5SvRHjq0pVOY8pV2mypXTPLNZUG9Vm

eA6OX442OW9tD00HGo40nGs42SAC42aAK43K853UNSu42ua93XuarL4V9JSAssbAGIXdNFYTWA5KNb40KKyXkzKvzRJRURI1AW4DbAGLkegcHxFgYgBW4OV7XE2wUA0+wVayDsWZm3RnJE4JZYLVACwJS8CaiVUhYg0mjmAF7pxIfEgm5aHIoEsIA9ZakzxZZoVfmn81/mgUwAWykDKgPw6gWqHJOQswmQWu3IS8D5kMSoxUOM//n4QNd5hq/qEJ

E4w4Ps14VwW4gC/m30D/mmkGAWlC0i9NC0NZaqELQjrJQWnC2Va8b4RU9k3ZmvxU2QezLEANBJ9lZKlRqA4DFTFGxHhEBm5HacTJAUVw5KHoTDUxDmDzaFGTawzXTahhWSirs3U8ns3nLPs01XLGU2amOUho0c1em8c2+myc3Tm2c03GtpWuMeIBu6tg2mq54jBI48RZgvg2l0+LH0CC/Bw9UQ032EiFfaioBEEfiDVwZVZaAXYbagHgAUAIghQA

K3CYQBKLagJAEw6wdGr4+HVty/YJFUrRlXbD1XC0/BZ4msyr0aGDRR0JaFHZdJZkLKkgdZeNChLYYXyyfwLipEEX4ASIUuK1Ui4W3HVBLXK0Mm/K1WaIq3PCVKFM5WJba5SxBhASq0S5eq2RCmq0fZUa3IAJq0CmFq3f8s9n6K8FnXCtOihq8nVsS6xXkWziUfm9q0qLISoFWr1jFWvq0akOkjlWoa0rQka3VWwOS1WnlKTW6a3ezGC0EszNXVa7

NVZmpyXi3AUDxAQ6CVAbYDEASQW4Kz3EtNSA2YagxjVPa1E2/IMQrTQIT1cC9ANssYJukqrZ7yMG1F9HRz4coOU7A6EACzJ3nKq2On2m83UkuNVkGWmg2LqlOm4yqBCmW700Tm/00zmwM1zm9dW3G5g3OktzUiK9hA9SG25lhE7XkIFO4yfE+SL6T6TnqyZVI/Y+zOqta4ZmjmVRa/RD71b6pxa8W1O1CfCFA5kH2Mu+GEWpxnXuEi2TggaHU6ji

UIs9WAy2nOahUzxWtAkW58W8W5CAXw3+G4s37YHk4aNKKBJTCIQhCKKCkyXA3QuIBWR4yMn9UFG30KidUcUsflmapo4Wa1hUzBTMlRyoy1Dmky37Gsy0+mv01TmgM1Bm+c0Gq4sacIB40TiR2lfG9m3/gNtUFy00W+41uaGmk/nDS6ak3a+6nqwAE3/6oE1AGsE2Q6uyDQ69snBi0sWrHIK0hWySBhWzQARWqK0xWuK2lGxK3V25sV6FVY4nm/QB

nm5QAXm2/XMAa823m+81CKpK3ackMX6ZWVBW4Q1BFgHMDHQS8CXgauC7AEGCWQZQBAgK3AUAGABqoSE13Vf6lr4583+GS7zwm/umo66RZfmwSCqATgCt5BYAz5O63xkSq2ZAYNqx1JLIxSJIXQirlJXFOqFD1JLKQgJrIsWi6HqQkOjEQYiSkAYuFNodQDTQcnhUmUEBFIEeqV4WB0i0eB0X4qKFi4ISq45VNWhw8JBwO/AA8ovHqfm2RacmddjR

gO+3VFR+0KmZ+2FC5eFPZD+03vFIXf2s1q/2+XIAOsC0YWyYmgOjS5K0CB0kIqB25GZB2mIfB3Y4ReCCO1B1iTdB2jITB3y5bB1Y1cZB4OiVKnsrG4LWoNUpam4XdfNa3Zap4W+UoWlBZEJZtC0h2325ggUOglCpFah2v2+XL0O6YVydWk3nC4SCsOwB2m5YB309Lh1oGXh0TZO4RusAR24OlB3COxB1hYMR3COiR2JQjB0+5LB1eqnx1CO/+TMm

9VGsmikUc6o22knPu0D2oe1Xm+IA3mu83JgB80RKsp4dVBFy8wEHYiGNnFwG1jy1mjz5GoFiQwHYHQssVwyeROiiYG4di4wUsp7xF5iZeaA66I3z4DG4zVVUubWhyhbW42/2342lPEra2g3E2uzUYjMm3mWyO1WW6m02Wpg2uMBGDhmjOWRm71Dqm27Rqa4kkrkXbTI+SKjVWWkl+WrmFHmwtlzKiQBW4ZVCkAQ6BwAfAX5YnTkR60PYfq0MQV6q

aWRa8rHm+E6at/JPW1oPlnxCErS+xep3m85p1v6XcKgzAw1DhfeXeGioB5mgs1CAIs2WG26yd6tDW4q9xRVaRfTPNHD6yq3+Uou8OJou95VeGyjU+GhEB+G46ABGvCRPhBF10aw+nGSS9JBIyRpwc2366vaWLszWl2yhIAx58ww0F8tI13YjI3wKlxiIKvI1afTWX1as50XOq53AQQZnS8s8bIWGRygK4lKxqM0FOSLODWWIsIoMd6iZ6OFzDsKN

6tm601lK9GHaWiflds1VlOmro4um4y3TcyZ0R2yy3R2mm0UwqNHOIlUoRCRO0rACaRz0jnF8G1PSzpfvZ0CXtan8/O2pmsLXaJH2Vvmh2HoAeC20W/2gNJUN0Ti72bE64xWk65W04Khy7hq7d4a29ADJO882Xmke3pOse1ZOie0XvCi2RupkhcWhUFxPHNV7gmb7120K2YXZu2RW6K2xWqADxWzu2ZRCXWfA7A3pqNjyRyUG24GXwxbyxS1zswUW

9+a6JEtL7hKxFRIiiuECpchwZEwOlaY+Q3XdO200Io/V1VK85ZDOyY026ug2tU0m1h28m0WWym3WW4M0U44cBLOtqWko1ACqWbNrRCbAGBxaH5tGFDKEwc+QMxVt6+ul57tkpumWiIgj0AGkD/qK6D1gJAhvqhHUcxVYQqKl50D0gu2KG8WWLSsWJJ6LzVUFZGw06DZpIMCd1U+WyxCuR1AN6ijW/K90gCWm83CWqZqBGmZrWGxF3d69xTnYnmCz

XRBhUDd8JJAsj3B6njXDncjXGGjAYm2wl1m2uF2LhUbFbeRPl2KcCmnka9iJAo/5TWaGyzAtXSQcU5S5gFI38azl30q+uKMqrI2ia8vniaqvmf6nM3vuz93EAb92Sm453AMOens7ADgEGKqhPO+qiLYVkVboK/hmSLU1+YIbnNs/o1tmpVUjGlVU42g13Luo12m7E10h2s11buqZ2Wuqm0x22m22Wwchv0xy0rmrP7HeJxT5yt12VO4ZVFy6zDyO

Y7W+W5iqkAu53qMgN3dcUW1qKiQAuKhpIZevC3ns5LUmKoi0rW9LUws1SrrWwK3BWyt3hWmt1t2+t0d2uAWco2XJFu7cHPWhJ2vW0k7VzesBTAfiDHjGc6zK4BjvKcelHhLtZzlUcmwMRPRKQV0Youbfbh46VWfgiC7QozV2dOmz1zuzs0LumdWOe31Eru3U5rusZ0zG900eei127u2Z37uqmFKQR10/KNJJ6e3OVygMrnSKlTLcuFLwpm592BqS

SDQgLeD4AbUD1gELRFgaEC/gJfGWC5wDYAZMAqw4sVQmnu0z2ue2JABe1TAJe0r2te0cADe1b2ne172rTk126E0nM9sWn2oN0To/BYxIYnJiiQx3GITUD320JAEAcqJkRM3j0mlRa2O2DCzWrRX407H2toCXKBAG+0E+4x3lZSaKkRaaLk+9E2M6g1r3Wwk0c/HL0k65iU8/Ck0PCrR2JEii3nZMiQM+jVj4+hMis+4n3s+iqJc+vK1U+vn1RMln

XcW4lnV8slmWiWe3z2xe3L21e3r2ze3b23e1gG4BhGehyQK2FqgfNa1GWAj5yO2y2VAKqhVvkFF7foTfSkJVaZN9CzE/sVcQq3FDIbO9/7qWt0Htmlhmma+bW+2h00YkjVXOmoMHaq9z2em7d3TOq11zOhc32ugYFlvdP6u7ErRI2GPRDuCRUB6hsqowTmCTU/m0ggnNHXq+FYZYh6nAQfACFNZ2y2JP91ILaeVdePt3POrK1x67mU7K/JH8yuxQ

bBGhCqOL32jumel++8coB+vvxoehj0SvJj1DAIl0kuyPwpxAj0Uu9DUjlTgTtNBNJv6UBVxyEJFXTArQ2MW36JAPF0Ye3+b8Qdr2deqADde3elku5f2L6yl14q98ouoRlY42KQbOG6S3hiWdph08T176qBmCaw/VWvCTV/c+Zh8uhT26+yAiPU+v1EERv3Fm7LlX3N4gCDV5QpaAVVC7AFb7yGI212Hy19qr1Dze2wGtsuz3Y27s20fdb3Oe+Z5m

7Nz38MoXh7eim1R27z3WukRnp+hZ0+rYRXF4vbRTu3VaXe+cSJNZOQfhNQWPuy9WKK7uk16k+3/aTH36Ia+1kOhX2FuvIHiBox1mIEx1zIGN0EWjxapa5xmq2/CDFe8X1lwfX0Q+w30w+k30I+8306Oii0yBjgDkOh+0EoBr32Su9Y+Kst3/mCcCVnRl6EnUS2DAYcBtcAGTl6qrbxmytkVbc5SYKR0YAGV32nutYJjuls0Le7V0dm3V0re5hUDO

vuwbejVmjOxnkUB813UBmZ0+em12r8u10LO7UVc8vrkYfUGFEa7AFGA693r6YCS+idv3yKkaW/GgK0SAZ72ve972fe770RjSoB/egH1A+pt3d2t0WWiK3DDxRICYADSBAgANmyoO0m6SOAA8ASoCWQWcILbYH0H2uwXhUU5mpe7K1BZYcZaQin2xII/EEhTvJoAOYrw06UDmIACUyOxUA9Ew3JdWxYlaQvq0h0CeHmIWx0lWuR5u0C1irB+bIwSb

6pRdSES2OwACYBPXlOQLDg3mLDgaUIWBrelkBgRX6w+8hVrPxcsHUoQ8H1gz/aRSFsHYak1k9gwJLhUklkQQHAAjg5pcCNPtaerTz7jFhcG4EVcGNg31bXHgYTIQ6VbHAM8HUOhbwLWO8HPg6/Bvg0Fhfg1sh/g2HQgQ4qAQQyHMlHQL6VHbl643eSagBWrayLTTrStUsHeICsHufVCHmHTCHxoTsGEAAiHWftpsnsiiG0Q3taLWAdamFriGTrvi

Gf7YSHOHm49fqmKHSQwoE5xcIFXgwSEPg/KZaQyYh6QymQmQ4CHsFsCGs6KCHzcQ+83ofE7eLS179wf5onSh9YXpbPYJXfxEfIA0901F65uDSIbA8c29q2VKNwXFUFJpbfcoLu/5FsF/5kDiBxzblaaNLRvA0LhhcsLljaFWYQGg/nOqrNQurBzfPykg1QGd3TQG93bHbnNfHa2tdqzJ2YpFtQmmittFQLpFTbcvFDi19zZUGq/kor0zYG6Fgxfa

JAIZd1LnVAL8WZcbCf5c8gYOHPLlpcfLmOGT2bbwu7oxLuaeODRfZTrI1S/DNbcqjJwx/Vpwzpc/LiSK9bY9a2dU163Q7mrSThspfbouw6RcWa0vFRSNXn+wAZpndvDJkdl5DbdRkX8SYDuXirPR07cAwVL8AzmGdLUQHLNVwzCw8Hbiw5njIAMkGyw6kG6A4waGA4ORiRozaWA5ely9ICsfNTUZMucUGGxuFUgNg97ecXg8ewyl7r+d2L/Mqjh/

rvjxKEWKIRahJ0SQ37ksAOEAMbq1bybkqx9ruRGmaZRGiaEWQaI/2p6I4oHFbcoH1Hdey+aXhiU3QN9NrXsZmI7rwKI38AOI2Ut9Q7RGyJMwAGIxr6LcVr62TTr60Fd0HkwMsBPJOPxrw2AcL8Gm5gwJeg1mn1qizjIpqRpxV/kSrrnfEahIxJxJTbjWQUw4QabPdbddyP6k/wxUqAI3mH1VYHbqOUTbEg+BHKA0n7PPQd60g/QG47fa6J3jqLpB

V4jSYkDaOTpzbcIa6700VFRyGAIa+OfF6UsTCbhbb2GiI0LikTeoqK7hPcq7kjcZ7nXdMvWPcDhdfAp7jXdZ7uyH5wwbArhcGqBIyuGpwTUDRI1rbO5JVHvaiVHp7kwB27rraPFYeGvFSW6XraeGPQ/xAkIMmBsAMcAKIXpHs8KrILvAo0/0BKEMFE9thVfJ9HlbXYEOUabaFd+G3UWH7R+VOqfbWbq1vUBGrdbUqEgwn6Sw8FH9veWHDvZWGdtQ

HpTvVBBQLkgxYvQXK24E59MI1F6w0jNY2bXF7LZqzKhbfg8RbXlGUdcLiJHiQ7mfV+LJAyT6popkzafeGR9jCYHYY3IG2faT7porxG/+fxGDELcK9Dpo7hI+uHqTYLwUY3L6zA4r7MY4jHnoagLhowbbdwU4cZvrUGggPUHrjI0Hfvc2jWgxb6d+ADbRyl80OYkH6RvevYrlAX0Z5LTocbNX1u/rAc2Ng4aHIxZiQ8WF5b2E2shBpfhfwaH7bPV7

bjo5H7To0u7iA7H7jXfH7XTcOaJnaWGU/bQG0/RFGFneNMN+dn7M5URqMFIzDU7UK4+pb86uPLhGW8T17VjrcENIEcaQYNKpbnZIaisfOVeDbIau5YdNu/WB6DeZZg15NLGJWSj5oBgrGb2I4MkwcmdQXebEjDffTrwm16OvV16F9asjQjVTJDyJd4krlcQkjSSrJVuJajgPWUMtJqSJZdxxZZeh74NXuT7A9XBHA+ZU8PR/ScVUR7fwl1wppGlM

pRtQUprMGElmpbK73aeRt9acjd9U/rYFdy6j9Yp6gA1XIT9dedQA2grvY77GOAKwa/Q+6JS+qvJsWrVIxDKXYmncEjJGu6hfWd1JmYbtGcAwdGNYyZrOKdrGaPt5G8bSQGw/mQGwI/brII2bGKw7575nYOQNZohHJGe9xr2LWUOA+diuqvQNqzfs7Mo8DHEvZuyCI2fb3Vf2H0ANta1gwISDWg0lkE/NkqfdjHSTUraVAyrbVrUm6BQzUGXvSzGP

vWzGfvc0HOY4D7aveGQME+KHg2pYGXQ+zqTw7YHA1MwB6wEWBCBZCRrY57HqPPqtP+D3AI9G5F7fcGFoPhBwiwrldto9gwIoGs041FwlkbYbrdgZjaPI3q7VvbrGn4/rGXPYbHTXTdGxzXdHoIxbGqw/a7d5swGAE8eF8WmX9NnQDGM7fK0K+pVRhRRlGgYxIbQtZpTkvfAngPYgmheD8YSUJ/ZAzSiypbajhheO/VOAL4mzTMMF6owYrM8E1G1H

XjGNHZUC2o/hiOo8qigkz4n8ImEmtSIwnDia6H1I/Vq1CmXMYAFdArcF9LiBZ7jdyHoDryPG4XUOC4AxJAwv8mziqfPfwwvY8pEZJfE1LXlL1Y0t7IgzVSHPeonBnc/HLEa/HBBR0yP4156v4+kHxBbVUeAMaroo7kG7+K1Q1tESTPo2D94gQ4L7MJAmnEwIGYE5fy4E6IHUcJuLcsp3QZDikh3ABjq8yEUgwQDiKKHsIA8ukxDanOYBNLgRKmHZ

qQ37cEsNg+JgZHY1A/gB4gZxaZpYalgTrCYuKYJe47gll6rUeFhBgkNgAgNIkLYcJwgdkEwB06FSBxIIigrCUinMgI4BrALDh9gHCnRAMrRggLDgUhbjk4IP8mvBVSDBHp8KOhd8Kuhbo9/hcD1vVQEnwyPsnZsv/hZHicn3hWcniCZcmhFtcn98nqYIUw8naJa7UCQi8mg2smR3kwqHPk7XwJJfeo/kyinb3kCmZHaCnbk3ynscNCn9SNimEU3i

nkUyMTUU36AnAJinUmHSh4U7inUUy+KZU9qnOTKSn2hRw9KU449fhd0KaU0zQ7xdgmlw9hi+Q7hiqdcTGkk6VrGU4cmLDvTR0dWymUyBcnYMFcn4RWCm7k5CmL8diDbHcKm3k/Y7xU9kAvkxYyMNJJKmHgHViU3KnZJQqnOwaHDw08qmgcKqnYU4amcUxTRNU64gUU/indUximoIAamTwEanS0yanqJWansCRanSNGSmMhdanBaD8KeHtSmQnrSm

nUw9bWdSNHJvkAG0FZZB31gc5lAEjx9AP+oDjsoBgptSB6wMoBnAIVQfpUvFSDJAbFo7koo0lydD+MXoF9E4okwuZ790PD5u5vc9HRhf4EZdZ7wg+H674306o/TEGQjP0m+2ddHAoyMnQozBH1RT/GeAMUnlzbbGVnVxJQcdzs/ESmiubUyxNEoYlvXXnb+A12GQYzsm+w/Ib49T37ZyX37iZDqaz03SoL09fJe/cvSWVjFZIZoqN5ZejtoFTLL9

9RJ6VZb+l1ZYAH0KTmagQFAB6AIGbNAI0A5Wbwml4j8jbtGMwD9guUkeVBd4Dgx5P/GMwUpTVIHUKKEVMhzsaFcGMDNe0mGGEomAvT07RjT0ndLXrHfI11z/I6+n346bHRkw9Hv43BGeAFIl/4xhD9dSucQE+DtIvX+AmRuQYG+u7GNKfhG3E7snwyFdAEAGiGI3U5m1obD15bYtbmo7EnBI5SaSvRuHStY5nnM4OnVI9kmlPX4qBgxkAWmLKh4u

e1qd+KXpfDBwlpOF4oJEf+B0qV8SkrvOkzZt1JqAojDZ3Tablvd0ncwwAC+k5onSA656340IL30/dGwo7BHLY4OQmdiaqgvdi0DknupEozthEo+JxLiB9RVTdZnso6DHco0B7O/ZDH1NmN15YIrBI4CQ6FiV6wsLetl6oFFkxJpCZ7AJWi6CbnklDi49paMtAMHYYgisnpCkso3c0AAUtfADIBOSG5CZAtLhg5mMh8eA1B5aKPkmOjPkOkJGBpaG

g1rENLRBJJ3UpiVHQR7ZkAnk0wBQhWEBsOl47zeAYBEkIHBsACeB7Q1hBZeJg6UyMiyB4XBKCsnLQxJrY6QkJA6vHTA7Inag6AGsRAnYILQEkOiBfQLBhnAAbV5hYSB9NqNnNYONm0AJ4SqCdNnUcqUg5s3zQFs1oAwgPASReuYcXegsgNieAgtsySAds5lDUAPtmKOt/bjs0Kl3aGdmmSJjSrs1jVhACe5qig9mECWKlJai9nfqlsgOwB9nwsnk

gfs8CmwhQDmckHrCX7aDnwc6yGHQ0BpoczShYc6HD4c+MKkc1UUMkKjnoHc7UMc8I6sc5wAcc1KR12JqJCc8TnWHqTnsvVyGhfWSaWo26mb2UTGBaaTc/KSNnw4JTnJszTmLWDNn6c0qBGc44hFsyzmVsx1kr9bI8uc1qAec6nE0Q/LlBc4dneICWRTsxYFfcvQtLsycJpc7dm5c2kUns2CAlc7K8Vc0Ug1c0QSvs+9krin9mJeFqxRSNriDc+YA

jc8SRIc6bmwnTDmvVVbnZHjbmriijm+HWjnHc/I7fHektYMNjnaMLjmPcwTmaPN7n0U3VBMk3E7mEzkmv9fsMgQJUBjoI0wOEAlsgQBYB6wA/NjgKQBK1czs10xltzseT5qRpOp2mgX9lTQpAAVgeRIGEjZdNff8ayP35gxO6hg9Sh9VY6mGOk/lmuk1TzF3UpmNEypnNVZBCjY6HbboykHU/Ud7Mg4ORxGW5r/05wbOhMVo2di8a54B1n19AYxq

rJbLes92G7Mwhn0wgob3nfrzlDXds2gIAWldl0J3DBHha43UiusQ0jpZaHz9pc9QaVeRnQ+Ry6KM2rLzpdRnLpTmb6APWhLwCxDqE84HVzesBRrLlNiwjwh5XZ5rSyhd5KrLQMvRuFAIoOYD/RkmGvUJJng/dJmgBMbrGFfemdY7AWSs/AW4/eii+GW+nNMx+nDE09GVYYF6mbYcpzsV4Wh3G/8fo+ZnEfGwDjCyuyxDVMroE4HHtk1QXwY7Hrhs

/kCqcTCcGgXNbtvtEm8vSL7g80JGPU2HnnhRHnYizvms1dYHS3YzH/zHABlADAAKAEsaN48Wa8YEFYyZiTZ9Ra1Q4bOZ85mZQMJPLxCctBfGsA8Fh3bYqrOk6wzp1dEGzozYXI5X5Giw0MnQElVmDE+gWx2hJl7nC9HMjqjAi7IQXyENaqGxlINBBotMOw0+7BqjaLug2Zy+gwMHNAEMGTCv9YxgxMGQrY+aj7XMHeOYNnqAZ4m6E0UgRU+a08gX

cXXk1cUIk51DkizyGg82oGQ8xkW72eHmhac8WHi4NHaY0On6YzYHCi4Godi70H+g4MHhg8cXxg5MHuY9R5T0Co1yBdnLr2LFLvBPBY+M8sFzEzDbjIi6M+pLZZdyI6gLMGT4MbEn4T/H7jTM1JmtXWmGxqOYWtLVEH+nQMXKDc+mpjTonHCygWoI2gXHoyGaeAGSovlh4jXdomUDGBWy+Dfx5dtFTE1Mdo4NizBnBbVsmKmiHHO5ctzJybQXGC/Q

XPnT3q6SortGVkok3DGXt7bWfE1TVrZ6yrPLwXl3AfKpJxXwwlAupVnrbtJjY7MKUEriF+gp/ZnG44i3G241+TCPW+Fi4/NZckrMzEecQZJDKsDmOVhqwwMf6m4+vTii6UXyi1uqO41Yb4+Xf7V/crJHJD7KDvK/gUlcUo0y7oC2AuJdv/dPH0jdJ7MjSTtZ/ovHnsfJ6zyigz3RTwBJAJgBrIG+tizW84wDjE0jkSNZayoRHtyAnhgxGi7OjOUz

5lk0FNwtbaHJLFUzbl0WBjUMBsAH7EawyonmSw+nWS2C52S1t6Ao0adas0YmFnYMzGs0za0OYrpl2XOJ2ndIr8AdGcupcEWDnYyiXE3Jc1gUCMfTqqX3zd/rNWE2B6U7LAHyxkA3i3qQrLoL7Y3cL7eQ98X0i2uHMi0YGxI/vVxHORFci09b8i2NGOFPSk0FUCB8Fq5Lq4EOQmy9hZwoBwIw0td5rvYHizVvvxt9ooYhdiCMwCsN7mzXlmdXb0WT

ow/His2yXSsy/Hys6MWSjE4ipi5MmYs7WG9RUfEQwCXpl9FMz/NTPhPCMth0o4DGpLmEWLy+CDNGj1Qr3WHG1NuJHUAB89zECHQEkPTcPcimn71JiKqQxmRk6r+oNLrOQiUdLQERCEglI0jH7HtJWzeHJX90T8nU02TU2SCpW4PAA11K3VBNKy7CdKxkg9K/or3i4uGIWd5nWo+rbPU/eyxI/sZDK7JWWMeBjTK0pXkapZXDNNZWsYBpXrAFpXoa

qwTlAE5X3FSCWQs3vmpvj640FcpyboK4g7II2jizTRTxVUKwY46BJLlGokPmnb9whD/xILhj54w7BcAxoVMnI1Nr1Yx6DhjZrHenabryKxQaJjZt6ro0gXpuVbgl2HABdgHBAL7MQABCF9arbLM5GgDUBnIJMXq1jwA8KVuWkI35UK9IFAh3L8TdtKroCAQKLTy1AnnE2sqh1sokvMJJ4b+S4LbrN7NYmOznbk5YcCTS/z9EP7Qzq2tn1wYOD2fh

+X/c1+XA8+5W0i75nNA4KHBeLdXzqwOCrq8zqVI8W6R06TtUq/Vq9ONphnAP8AgQF0xLwMqhfJc4B8ntXA7IDyboMIVRpTWewu3THJnoiJn+y6GsxrF8ScbKUFo5BF721aMRsnNcw95MahsWqEiOi9VxJdhm46jMeECDfVW4UUyXCs15GKK4uWqKwMmaK3bqGDV+ndM+3tsC+nLCEpOzz5BsjC/iQFQGP8CNyKahL0hQXBA8thKfGMqg3fvmczQ+

1g4ECAYAFBocq+ahO4O58f0OXp07ULHeACK5BVZ+qxTkGWXZXjAHQV641daOWuZoon0bXsDSDQm83MYMX51UHbEC5yXVy4LW6szwBZ7PNWAE8uQCAdSMj1QoKb3YSVPqAjj+K3XTBK7tXT7PtX8vMEH8oyRH6gcTkOkBpAm0PSCo0/uK5QyOLbHUONM66gBs64qAKwI8mAJVrn3Mx8Xvy+gBiLQQnSLVSavUyuMS62XXc6/pLEQ9XXgs8DW2gbbi

wa1/rzIBbgvWVABkwAByb1WeNOKusA0lXVx+OEEXIIKi5FC+LFJ0g4NfC7GHKq8DEEw9OJDCwhdxyzZ6Mw1MBMLm7WgIWjKltdQaRnWpnuq1jFwo+uXByHpcZk05ay8CINXDcvoc7X4X46A9hRkXzafXfKWQtYnWEwsrW5TjIaVS5zLdjFuHjLjuHfLuOHGI7maPLtuHTLjOGLLk9XiTQracYzocfM2L7Q838Wsi0LTwG8OHIG7OGwK0eGIK817x

ozN9joJJBJIFdAhwHZAswyUnJ68+HkwrtgXmAQw8iKsY9yFeljCGpiDWZlM6jPfdQgz+GZtc1WFM0Vn2q+4DgI97WrEVfWepjfWno0j7mK5n8j/j3AsGH5qSAjUX3jRgoNtGF6Kg5sX8wevjAG03MZDbeXg3ZJWWI2aw2I9JGJxbJG8TYLRuI4pHmHhFCoUABLYcIPEJeAGx/gP1lzEAGw1ADxK+aLR0qQHCJ6bnqAg2Il1RaAgB4q62D7HmY2Va

exGrG3qGbG6SG6I/Y3vHkqxHGxVlEQy43t/GTU4kB43IUN43NSCbR/G8/Viej2I2I0T13aGE34q2od5rTfDUGzgncYyvVCvRYrVw9OCW68Q8JI6xGvWJY3qI3JG7G3U4HG9XkcQUzlMm242cm5424RD433+UU3Am6U2Qm9D1Km0Q3h033XA3APWczTZA+ydsBFOYO89a3/tdyHGJbGEgxcjm9sO4CEiN0KsDblNZH8GUbciwlFQ+jftGamWNRXI7

bcLC61XyDRRy/URI3hi6BHaKxPZHWcd72dBOy9RfkoTPaGG+DR354gSqFnousmBKztX31evEgG/ZnCo+Pdshb1Hao+VG8gY3cqo5PcKJWi257h1D3yyg3PMzEnGm94sMtZg3fizY9/ixRbMWz1GW7qVH+o3VHFm2CWCi2FcPQ/DWQreOBx2bFnqPEmcIXKaW3ysKE2G2UmPnF5hi4kTB8S6MQdo3TWqjvc3pWTfH5M/Z7RG+83E6Z1XL677WBayt

yk5YORXEcHWMIeOpRhI4pl9MlGA9f0ippJ5rFa4qWDG/qUoi4ib06/Y9UYxTG0RFTG/rpeZyY3DGlfWRFnU25WSW4m6m635mSY+03oYykhHW/DGOfdTGEq5r7e64bb3QzN8hgPuNIa/dq2AJZBJIDqAiCJoB7yvWB3oMqhfQ/v8g0pjWg6Qfw9VjkRGjas6jgPbKj/lQlQdKNroKKnofKsuU2ASIYd633o1Y2zXsw55GYC4BHPawWHJG4Mn+a06F

/a7fWeAOG3GszgXyZRmAWninpOK9LX9+WZmOqhlLwxLwadG7/WZLuEXpOLj5VtEG7tlZHGGCwLLa2wxJ2/OANg8cGdcMxnHMdnwX69sIWhC6ICAypRmxC/PGaM34riAMqgroCAttMArAcq4CscDLTp7uDHozQT5BwbSCNbGLrJvXAOXhM3RIqfDIYsrrtGgiy22+Zi7XlE8I3FW5zWxGzH7bCwbH7C+tq6K7a6GK/Hbgqbq3J2UmlblJFQp2/0Iv

MierkmrfELW6u3lazYxELqHHjG7sZAs25m8gUx2MwnLba629WfW3cLCYxS3tHSVrBeKx2uFD3XGvSQ2WExCW/NK3GPbMQBzgCYnWMxltLsRsB8YP3G2qJtWF64dpRgWOUqtiXHss7GbmBQI3r4z0WI/ZYW2q+824gwObvm323tfH82MCzwAnoe4WkI5o1fxNxID+h9H362D9OKkMc5S+IbNk9R314rR2O5V2K06+Oi3NuTmI4FTnKCVFk483TnIE

e0Umc0tnWc6tmM8+tn5fdnmpHdtm8809kC85cURc7V1S8+dns5hXnP6nxBq8/dna84rmN6K9nVc/6wDCW3mtc53ndcz3ngczYywc0F1B88ItscGbmtkBbmCcuPnEc8Txbc8oB7c947581E7k6svnMIKvn8cxLwic2KIfc9vm8gUlko89rBqc5F3Ps9F2GcxfiU88tm/Dn9Xku5tm0u7zmMu3tmx7gdnsu8Xmxc3l2Jc4V3rs8V3Zc6V3Hs+V3oUJ

V3m89V3ps5rnbHfV2oRHrne8yDn+86122Qx12R8+bmx8/JKEcykhJ82a1p8x47+HejmRu5jml867mV8+7mpu17nZu1vm3yxzSXq0oH0Gx5WiEwG2dJqF3o8yt2a2Gt2oLTF35s8nnmc9t22c/dXOcxtnucwd3c82tD88yd2hc5PkcuyXn3QPl25kJLnK88bwSuzcV5c8YTns43m3sy3mau+92CQp93u80Dm+8y12Ic+12HcgiDKeN13FiWuK+u/C

gBu0N3Ye1qRRuy7nz1Ej2ZkCj2N82j2nAMCXI2yJ3vFSy2LSYGo0LnVlNAPoBJANqB8AKsaIttXA0TKr9q4LXBV0wf9gGDE5r4uQLK+jBwS2y4oO4KSXp5IuoP/I785vXFcadGF4cNV35r0/SX5W/O6Oax23H4123Pm6pmRi5Z2sOxkGcO/a7OeWnLhS5nKPwvnh3w6nbkbOsFZFLRQMXVtWNk7BnLW353v0FzFAuxDGaC0hnt21qX5pW0AwZUh8

GJMgwhvIOA3S2e3CMwdKp41asbsdqNVZdP9Sy4K6v9QBB/gIWK4AHBA29fQ3+IrhyUXukkgZAEIQ+0Lt9yGGB4VSKtAg3DK4gBfZ3PkYl/dmVoc8MRWIg6RX742830SQNsly11X1W/23NWxuqFnVTiH60F78Wn/wAVCtXsM7O3RFZEbI5NZm/jfHFtgPgAiwMoBCpLdzJ7Sj7D7alb1lelbeIeJXKfkEt96qY7rg5+A1eOFluHkZ1xoVgP4cHRLD

srgOvWCTVkoR2wsc2bRaNFZ098kVlAgA5XQkI8Ygq90AmaNMKNSN7BoUMzU2CXgP2TKRpXsj9AXgwPmAe0WQLWGt1teqgnVcrA1fMGgAAHWb4FAJRGKALA03mPIPlB8wA98vEBRepiBwQDfQKkL+AEHQtnZyMUsikFdAiwM4AaLeFlouy/aIQpoP9avJAL8ZWBmHRBa6c+EB86qTUAQ2ZMxvqL1+sgLnrAEoO2mGyRmod0VoMM+AGHiQAVQE4hrg

POAZHV+a9AKiGFIVr0UE0M21Q7ujMQDYSYihfB2SD7BiCSaxJmz50ny5gPkhzz6f7eQO48wQOGhkQOSh1ZLCJXEhyh1HRKB+lkaB5LVzugwPpaEwOwcGLhWB+BKKNBwPoUFwP/ENYheB9ig8B/+BBB0rlRsCIP/uybmJOhIOSh+sGZB6N05B6gAFB7XIlB8wRVB0Fh1B8wR7B9oP2sroP9ujYhDB9jhjB4UhZ7t+aLB1YP2LXbkrEMSE9QHvkDat

oOxJs4PNSM46bhye53B7A0bQ94Ov6r4O6SP8qbABR1gh75DQh7YgL4ZEPbrp8PYhwqH4h4cGkh588pB6kOcQ+kPtCWXkRenaBch1Xk22DxLI6l62lrVx2CY/EnPKwBX+OxB1iB9MgcB2QsKh7anDutUPER9MhSByL0Gh9gsk6lQOxkC0O+aG0Otcp0PYq7RopU+wOGHTdduB8MP60HwOvWMZohB1MOKQ9qwFexLxxB40OFh9IOssrIPOQOoPFB8o

OthxnAdh2Yg9hzoO7svoPhIEYPk8yYOLh+YPLB3+b483cOQgg8OHB88PHEK8PkyK4OOLcwAPBz8PtYEnB/h/4OgR0EPvVWCPwhycZ0ak9mYh/8A4h8Q6Eh37RiakqPkRyOLz0RkPHaNkPMR8mRsR6axcRxpdNaSYY8i1b3IK7HlWFGgqsq0SQMxZgtiza74H+AEIvxEDRghEUyqi3yh3fo2SbZYhzIViKKr4w82U+wVnoC2onrC5RW0O1omMO/Qa

OmQ8E7IJoANIK044IN97JIK+drIFTtECIhqXC/yXSyQo3Yo+fhJ4FKNYsZHX19M9tZgU7TwB9UH0ABgloB7AOrcPAOu7SD7Og5AQNIMJIFlN048ytMGEFhcWAXjxCfMgx2IOm0x36jaZeAGlCX7aKnE89T7LHdT8CcnbQ4m5IOUhwvlR3o4BmwL4gxJh88N0Qzm0AGGOTaJYg0JY4g/avympK/BjZuPczFkGLhoJ3cBWZPvl2ULEg4J6N184BNm1

hbDg1aFEBn1JVHYcKO91eoPRaOrA0gQPULggGgA3eLEwqNGxOaNHCKihx+bXx87RoTHzRX7OY7vxzdlfx3Q7/xxqwx6DNDox6BObCRBPwe44gcJwnmbskRPkQ1+bEJ2pLkJ4VFUJ0pO2UISBMJ2ShQkEpO8J6yBR8thhYGiRO0AGRP1WJRPcNNROb3nROaOkRLRukxPRACxOnEAg52J7DhOJ7DhuJ/iOvM4SPojp9WsG5S2cG5L6KOm+OBJx+PhJ

+cKfx+NCmfgBOpJ1GOGR/NlZJ+BPAQwpOOkLpPYJ9rk1J8Q6NJ57CciXhEdJ+hOz4AZOlkGhO/4CZPRIIRPtcuR1LJ2KJTEORPrgLZO3EIBoaJ2otqOpx1GJ8xOJs2xOOJ55OuJ+SmmWzxadfas2/FZSZq4EMAbIA+15G5eCgOTKak5O76xFEEJt/dWP4bOIpJ3asDXO7fcy24tg2caqFRvJfhwjBVyDgmd4xmc8TDdQ1z2ax2P+iwswhgm1zCDq

h2hi9n3i0LRyjY/h3GOZOlh4Je7QM4XKCMIPq0y9lANWsnWbyAsyf6+M7epoOPhx6OPxx5OOgQNOPzILOOIJHazqC7CEDOWNOeSe6R10DZy4tOHhdgJoAk5HQljgNJ3bLK6yDgNCAFsM+R4gG6zjx6qkQQgYAiwHZoNSp4KxsKYg/4CqxMAGb1bekbn1ujZBV2BkgEAAAA9V+xc1JUeWQAWf20EWfIEDOSectZyoEWuP9YGau/WsFNpID7mpsk0k

hcp6hoK/ccwDuAdIl9dP9ua5gcSVZocxAMQq+A/sQquGWH96vqU+K9gv5k+LVvaFHw+G25CudmYJySlGwdij43Tvossl3pOxBl/tqt8gMyNtctPRu/Mjt9OXHupYL5aDRrMbVO03kNasl7Dk68Bi9Xedw823areOrHS8AcATJ5OyQ6D+xuHUX8pUvatc+2IZiON0FpQ3d90emgDE5hVjHPB+xaxPMA5ICuzj0khIt4gj9lFUVARfvL91ft5xkI33

+nWR+CIFSYKF312l7Az+y1XzmSUVy66yMtN6vckFj3LEnHHiIJll3mf08bHL6s9C54PPRnxcNJTWYumad/8obhHeV1xi9vXtvyRkZ3cp35mT1z90lnll7I2ozBBn5GrNl+abOe5z+4ybxiesympySjAlchuGFJWsjC5it+GRQXyJiRmrYb05acunStvaO0lsIPJ9wzt3p15tYwp/vdHHsdlZ7RPBzv2sf9um0LOpc32dyRn2MH3GaJbAGqN6vFro

HmDrm2zFLttOcKl8Iv3uiedoD58eSHaMdF1vIHATzBMEhfycxJhutNN+4UaBkKdSo3WeHjumcpxIWlsL+hP4JmmMW9qwPZj0htQVvMf1a7UCXgN65nmxoDuRzKIZAERyOkcepJciIQ563RcKmoxJhelNx8s6GFlKQDjTezBh0lE2J3KdzCNcfhv6d1sfwL720P9tTytclVlOenmvj9d6cxyz6cyCh1BGirP5nak9C1lUazZEMaX7V3WYpz8v2LHZ

dva+K45wnFaFfjjpCRkb6qQgXScpLhABQnW1seFDGcpVu7nCgeWePciCStoHor6AJmdRADUryUfepyAGOJxcMIBezBwBOAEsCVga0Aw0K/SzalVhrZSQAyUJR76gdpfNVzpcnuAZTLDWcvug0miWEHp2NAAfSVMxrAtZOMyDL/l3CY2Ze3qJgAMMUmhzTmYT/qJgBTLgox8KQznBwTICSmVX7CgXZwpW7jgzViYBoKi8eEAK8eVgA2cZbE4Bw25j

WHKMaxMjUuxlHU/CqWZQu9qiAA5aQbU8vIyPuBzmB1bdRHUWC/xfRf+W3929POL4zuP9lxIdc1BfUV9BcVZ9/sr8iZPFjYeBHu1bY5/ACA7Aa2vEkggz4QobwinUFtUL0ItXqo51/Wu0pkQ7oP4AfiA1AIghDoZv0oD4OOG+Uucd98ucalyuc1YqRT/LlkaArq/jArlQ2grv2lhk/+UdzqfXoABedFj5eekull5rzzj37hMpFdcOEAX+BgXEGYGL

paaOSXEHzyzz1+V2wLyVUYEfLcrOVdYq2/35xgee/hMma5KY8RrGJxQbNNiTWrqBiqhd6hVKNl1DhS9vnz3/3mvf/2IUisu5G0AMMx1lszffQC0r+leMrj9tLyB+VVF6qiD65qR59aOuPLpiQAzbqReBx8gauves3po6MtVsg1IL+FfPTr2tfNn2sYLjVtorrVva7UxN6tt8rsNuOebO4guEKEktK3GZe52kIsC2v+satbWL9uRZPZL3SkSBRJeF

C8nuOh66t9rt6BvDhnMY9wxWfl7HurrVQON18VFZa/hfuka5e3LvMoiLii1HU0dciT76ojT7X15LtlFoKwgC+kGAA8AesDwwYs3rkK5hHzEEbHiQeNTAstsdSG34WYHGwSt50b4Mj/3jpbrwKJpPvqx2TPH11GV+2gOeeLjkslr1Fd0HT/vhslUmLjumES7MNLAuDg40VUhca3Vqj1GKjtCV4n6BCYqy224iPBd2oaXXDGoNJdiJYwfDfsd1ysEj

qFk8Lnjv/l7BuAVzqPxxPDd4j4TvSL0aOyL3Mf1/NBUdMNgBQYVftNSzOfUeIxjn3BiRVF4+mudlriuB621GR0BjmoY9NZfGhUtjuVvrxGmeBfNtuqJu6ddjp9NAb5cvqZoQXEAHIJIg4CDw1m6A2QUKZTAZSGSADSDve/iB4JaaujTE4AvRqDaaNdo0jUkjtgZqCBEa4CQYcuOuOqnztobyPW9+JrheERhfhkUrIkT8+qX1IHCiPSJuzsNQAhbz

2pAgcLecLlIs/ludfupqjehTmjfKo4LdkQULdg1eLeMbphPHhzGf7r+rXtMA6BO4oYC/pqlf8RRXbHxEcDjMZ/i8GlrhXKB5UG+B0bSb1zeu2hC4sC5yNZrv9djGx9MIrl6cIFqRtv90BI6b6yBCAfTeyUIzf8QEzexMMzcWbqzd8linGrAF6OElarfUyucSkJavsl7B92pz8lfeb/+vDkvzffTI6sSVpLJ8TsBw/gHzqsLY0Nq5viWD0AXIiLWQ

neT7fwMW4C2uj2BoCzweKXCBJCiBPmijvTEBb+OUx2dQODptuWg4IniUOjxxCYgKWScPL7M+AKHucmWLd5D+kEN1OCBKsSuYKwNWhBHL8X9i2R5kprEAwiGkBgQBHcZIWWp41Eh7RdOJCv2DUjrsFjpsyb6p1TvGrBk4JYhj5SvXAaWjXZuzruHOJDJQtkj9ZKACw4ZgBhDs3jSgDcCpjsWmWTBup41DkwPHXH16AKjDIW97ciO2HCaAbyec8XXj

EgH6r58PFAWsISf1FEUgSgpEwAs5nem7s3fm7i3dm7tWjGIUnLxphurVwOswYhZC3riuOoU7pVgXb98d0TpHLS7lnft18njcYh7ucpc3MBpzwWtE07p7W9JuHZdUP4kVOAmXJUT+IOCBBiH3ccmMYmC1J3NFIJpwG1OiejvHooE5ScX9qBupAgR1iFRRUxhUVidyQpXMl7+Mh3CRrIxLIHBtTr2hk5j3fQma7ewNW7fPge7cNRJ7fP4l7eK7oC2M

wDwdfbmES/bhQI3vQHeYTkHeq/XiApICHdi0qHcdIGHdWAfujw78cCDdjwnI77EcNddHdSV+ABeOoSCwYbiWS7hZAE777d45Ener78ne1kPHJU7j8e07g7pPBiXg+7+kzJMGJCesEKsc7z+rc7ojcaQ/ndusIXci7kOhi7s1gFN6SbJ7pVhy7iXIK7t7eMwFXf80dXeFdrXeY0iJB67taGd5I3cPMyxCW7rA/YH5nfW7nYp27uOoO7g4xO77CAIS

03f7GZvenGL3dL5V3e+7nOv+7jdEHQBXNB7rrsh7k2hjE/TSR7kXrR7prrgY42Dx74xCJ79wmm7lPe2EqLJp7uHvCOzPedTjpA57r4r574Qdx1IvcAOUaI3QMvfRDptCV70aLV7xWDtsJgn17se6iPapvKO2ptEtxLdfF5Lc/F1Ld8d5NUUW87cVIfidXbt7pt7xJB3bkUO9W9Bzd79Ra976A8tgQfeFIYfcHQUfcA7ipAT72pyg76fez5PHdYkM

SaL7uHfn7xHfZb8Gqb7tHcY73ffY7gBqH7/HdD7y4TE7plMhIS/eU7gPq37jkj37hneP72g/P7tnfv71zNc7u5Pf7vnfRZQXfu0AA90kIA8S77iZgHlBFe5Qeh97xi2G5Eeqq7+A9ZCxA8MH3XdR0fXcPFQ3eg9jA84HuY+W7vA+2738D4ke3eO7wODO7sg/M7ig8OHy7cymag+NFU3f0mP3c670pBMH4wksHgQlsHiXIcHjENcHnnh6sXg9J5gQ

8MmJPe0H0Q9tEvmgSH3XuoO6Q/Z7/fK9FBQ/SjvGrKHjqLvCNQ8gkcveaH9WhV7hUw17vQ+BEgw/sDnddqRvdfXF6kBoK5YDQgKYCVAIwBYQUsaAcxLlVbvyqtSR9jrGJRDek+qRmou3xqroBVBk87HBie1fZys+6+F6/vIchiQ+49c1NrEFTgFhhjXT5TdzlnWNuL0zuBzqbDeLoc2+L2KMS7dosSlt+tcHaPQiRWmuHb3zdASE7dednb29tMbd

6bgzfTb2bfzb+sCWb8B6ozm1voDstcf6heNYz0ziqhdG2KtWECJ4YauUzgNkxIbeAhIvGBYnuKC4AA4A+SIYD/yEpcXCcpdGYI5qszx0BydQmpFZQmpg59rIv9O7xyzx7kKzuNk2bzP0G6d7m/YT7kAtzWc/c7Wf1ajSA8Af4DYAF9V9BwqgLTv3sDgYMQTHcvRNrc2dY8ulbcuFp5AqaMR0eC+5lBFORyGBp3uaPciGJK9KDe96SCxr2eIcPk+j

L26d+zoU/ILyjmIr3msB2tbUYxCU90wzqRoR56KCud5RUBDzc+btXnHbzatkrt00an3TcTb7U/Gb0zfmb/U+Lb21mLc40/GN6ztidqdxrc90jbABzkboBEoEzxpiSZfbkxID0+HAa7mnc8WLxAAUnLAYgARsxzkzl+melL/08sz2RAkCUXrXVV+xJZa6otAKlQxnkAZxnnzk2bpgNFeZM/oAQLnGkwujpszM9f67ACVAQ6AcAai6HQCrcEn7AlVb

ks8Q+R9i5TKVum14eBqJZYJVlWZmowes9h93mAl6JXaOjS+LrADs/b7N2UhvK6dwk3rc9J4c/5r9Aoint6c9c5c1M2mvWyMrbRzLYAdQQUBX3MWtcrnjzJrniZUQz9U8YjTU87nqbd7nubcHng08ozk89on9lFNyc8+Fb6tS8koBVusvsBiATkLEAOelTl0M0nAQch9wbYCchZco/n8zL7AEUwBe30+Mz5meBn0C+1VUXoac7QdJZDTlN+6M/3c9

UkIX57mJDPPBvctWcpnjWeYXrWdUQA9fHQKK0qoW5yFnwk/Fn1/wtBSb1aybKlkze2VJ4U0sthF9cTwATfnPVZp1q6xPprts8AbNitdnmqz8X7PyCXypXCX9rkFr7ttFriyJcKyte04z2nObr3bUXrg62lyyNpr9/pqXqbkUB7S+Tbwzd6XvU+GXmJJGnky+nbrBceqCy8cWXkk7cvuDWnsQCGYC7nLAUM02JNC4XePUoIAGoCOc6I0kluzJEQBm

dlLwK9oDIM8UiUK9mZaC80eVABhXiC8yzqNkxXmNlxXuTbVrTYBJX5NmpnoiBYXjK/1aj9ZMECggiOPK+kXv3uOSEPDTyllhoMIAckMtBjo379Da3ZRApSsPsX8IGRJXFJo6OXKnpcyM59SJjUdX89BdX6nk9Xp6eiXjTfdcoa9Qbk937yUmtLJ+kZ/TzrOlWf7Q/L2a8qn9c98ByGdQIRa+7nmbf7nhbeGn4y+ZWm4tmX3Jfmnp1nukJzno2iGF

fnt1nfn6YBusr9DuoGKBKuXADy2Y4AimUHHf0ZC9Y9Z6/AXoK/rgCLliHm7rFZXEjjobADAARzoJJWJhDAOWr7gT29y1bACOdAyDAAXEi4kKnaYQYAC4AEWfe3kWcGQAyAA3/JcPc+C9FLxC8JXhCMqGVC+Gk1K9Y9GG/TgDSPLAGLY0Q5VAsZ9ft+9kqzLyDqRHkC8mHx8+7UpBORJStrcbmub2ZruBckGl5u5rj2uAbsc8vp6Rv26pzOyoUo2d

MS8DagKYBTQbADVwbYA0gXdiVASFNzj5bdRRnIOP1mozkDagoYVvg3NrtzvsIVwwARFe8bniv1ZRk5lZyhkpprk093l0rKuT8XhJH8LdoAVgBmwGoVg71IrLAaFAJRALroj7dd5A0++9Ti+9Q4K++5ZKkC331KHxkB+/WIJ++ZDxYqv3/n2YB0w+qO8w/vV38vBT3jsS+sSPv3tycOlWLeX3ibo33jpB33gB+P30y4v3odeA150NZJ5Ksq3ky9oK

viAKc+gBT1YWuaenfiK7B/gBhDdBDeZdkXMBWzj00pkl7KT6PKVchDzKFfZrkRvId4U+s3oOcor0BK93/u9DAQe/D3rGBj3ie9r/ae/WbhK8hSvBd6t3vySW2U9baaU/pozPzkMdiSobpU+rnmDh3YLa87XJiNn7plN80B+96Q+kydLyQANdJLJIP8XhoPvEVGjtIq+IBUfTZXqe/VG3Au7vGpJZHQkorM+/BANB/smSR42IKEchj4TDQnR9EkPc

/cWP5nspNqtjqAOx/ZCvZ69Tpx9kQIRYnD76hzDjLKeP5bM+Pn6/+PtgCBPhADBPi8xn7hw/Bj1/eRP2psuV/C18RnHsfV8lvWHhB+0bmJ/mP/8DxP6x8lIZJ8OPoJ9f3w4WGIFx/ZP9x8nC5B9eP44ybHvx8O3gJ9pPgZ8hPip9RD6Ef/AGp8xOpZdEPgreonhW/on+rWWQSyBEjdY1Cw5G/0s2h+raWwYrCEmsr3i5jRTJ2kODBF6f6TKbYtTi

903pqu3xmFeIL5AoPT9xfKZwbdx+sU/kXac+c355pkFdccNro/5dcUnmCBg++Mzea+BRsR+GyiR9D3ke8yPye/yP9a/y3jv2K3y8/K30GsWnwPjuXmYABs4gCMrQzAMSMznmZXRcX4Umgm3ngBdgQ1B2ZK/2AXv0+vXsijvX9ACoARzp2dVWqBybycIOJmhJZbieOdOO+DQOC896kG9Kzmzc8JpM/JXtC9Q377nqINBWyoWVDaYIEARswM3HPpLn

yGb0ZjMTs53PgMTFWePD9xlLiHeNrdqyVqSZSsz7vUbG9QL6RwODO91HeDLSXMF59F3xDsEBxm/kckc8TnwtevTx6j/PuYI/9pm11Xv6dtwIJe9gG5hNPIZWrt6F9GPtU+bnjEbwvge9Iv6R/j31F+5AIy/nlzF/Fg7F/0V3a+Gc90iJAaEA+sgCBUYU2/Er2l++XnbmjefyrsqOzkK6RznroJ69AXll9QINl8QAL2/B3omjcTp29T1aEXtC4V85

oUV/EycV87a5YB/xtO8yvjO9Bc9M8Kv+rVTAIsBD3n91TAX628bpeJGMUhhgKuYtWSfV9qJXBhSDSOTrmtrdq6fTUmFuksdJlu8+zsitwr3q8s3zu/AbkR9ZjJI48AHslqgwI6VAOH1TT/ADnQbUCaAdiIz3qmH6YF6MK6OMSSNEF/rBBLTVSRU873ja8qXjIiLVo9PGPk+9qAEp/FExMC5bmBt9P96CyEtD+JFzkOQP7kN11mB+WHv8utN7yu0b

jD8oflgDYfgh92S/Leid3N/QV+rXEAFV81AQ6CUz/E+fzku97ATNL1lTd+2Yl2nSKexi2MFCyOSL2kbYRq/X9rres1uPEXvlxft39Te3vzTfd3oQWPv59/6AV9/vvoYCfvxIDfv398KP4VrLACreAv6oxQMHQiKnucQryLqrUzAITPV+vswtg7e0FOD9eZG8ugNwNsgE8oqMkB4shIVSdox8XtMEo61a5ucWB1BGooT1IqMO1+xq+oHDtZcL+9Ti

IC4aQsDHLhUSiAWDD4EpxA1ObkyQaekyyYOeEpKI8BYwaWhA4TgAuw8L8GtAZ/I1N5ggP/aFvMChpm1a8Ux1GKsTijgB75E9HawQICog4xAZAbJDS0eWRtMMkNpp2Xdeq++xT1afJs9Fo/gjg4pKDyrqq9/EhXMVtOQdIb/1dUb8cQA3dKDxzqmS4xBJZZUDIP2sHkpxzoOD7ifVfoep7kBx6b5Jq2Df0EIjf4Xdjf5b+G1ImgG1UnJkmb4/4Ol1

tNE9z/GITz+kdXKc+f6rt+fshZU+2GrUNYL/aT0L8zC4r+vF7HBRfsZ/i8WL8QmBL8PCSNMpf7ABpfuMwZfjHeeobL9BHboB5f7HCFf6Wig/s1qujtABlflQlc0Sr9BYA78biur/yiIWhNfvSBWT1w9GIX6qzZW67df8o/w5fr85pgnJnf4b9X3kXfjf4glXBnSXTfy8xUgrn8Lfy79LfqY8rftb8/Xzb/i8bb8ZC3b+b5vx7k/9piSPbh6nf22r

c/xb+oHigBKD0R13fx3Lp7hLefFwj8Ub4kd49tpukRpVhufi4ovFyHsffvYq+fwIn+fv7/31R+ohf6vcg/gL/g/j8ey/9HhKDmH/W1HrLJf+wmpf8cDI/5h5Zfs9QY/rICI/7H+UdXH8Bf0r9skcr8k/wWpVfviAm1a7oU/sSBoAKn+cAGn9UwOn9tfxn+dfsbqByHr+GhhZ+yOvmii/rz/a/vn+TfwX8cAGb8Yguv8ff8X86/qX/kS9b+Q/4IDy

/vx6K/03tpIFX9Hf7tMa/+b/1/zv98//X87FB78KO5E+hZkh/bP/ABoK5MBLJaED1gKaDiujj+0Pu7DcfpTuYAvj8rAHna3+exh/8TBS2YnLRpr6/tN3s99xQGxIM39Ptc1gbfevobe9thwv262rI3QNgAzxTWBXQbTBjgEvAaQh5UG1AAmdlUHkIPT8JMgM/Vg0jPwO1c7wQdEpRORl61zYQDxQVgTfKPR82xWiaOLRUuEC3QPhotzIgCj9mACo

/KJ9BeEy3aUAiAJIA2p8pUnqfNBseaSafFpt2o1I/DLcCAIoArD8InlJFOmNRpy2fTN9V/3q1XABGgCtwLSMoAAvNc9d9/2DDfLwLTV3TPEoUlR68S7xclGqvbbQ8NV2jNpNT31bbAc9fZ3nLf2d5P1+fdDsJL2NjXqZv/1//IwB//0AA4ACWhGAgMACnSkgApbd/330zSS8WA2vLQ+RHBkciFACT0HLHM7wbPyg/DF8sAM5iHACEPxMbfYwbfy0

JO39zvzE6AH9Dchx/RwcPuwSfGv85vzCAhv9rvw+6bSUOfx9VUmNrf00JFol3vxG/UepskGS/BP9ogKl7WICBv01/MX9efySAlKAUgOuZY38CP0CnMltGAMSTZgDStSCAzICPPwG7cIDLanyAl2FtBxiA5/cSgMn/Dv9ygMl/Pzo8UFV7Rf9iH1xfIrcv9XwAQ1dN/ygseQt+tSSVYPVYDhrCHzxmpHgsQ25fKg8wDRp6KQFVdIh3UFj0XXVjp3y

uO/8rEgf/JTcNAMvfPNdr3xQXXQDex30AkNEEAFi2F9sZlFqANOAaQH0AQ6BjjTntN85X1VsAjAtlgCwLBwCAEzY2NPQWkxGpbKV4sS9dcM4vALFvfbd050LtdABl12kEO5d97TvHZAdnzTDiMMQjGxc/XfF/CkxwZMd6DyBwQIBEAHfQYWB9AFiYAodPLkuyCXhdf3hDQehEh2knFKdxF1olB7saQIGfJI8n6hSfEqIAshp9UgDAsnxArEciQJJ

A2RZBKnQ6SkCQDw/qGkD68iUHXYMGQMjHXmckR2uDM49VaFyyL2gqc2R3P2puQLFwXkCagM47cjdSWxhZBoCRIyaAvHpBQMJAk1hiQJ3AUUDyQIlAtMdhw2lA7EhZQJlDeUCER3W6LXNfqjZAtUCOQM1AkvcSelCQXUD9iUzHcCsZFwvPYMC2N3q1egBlACtwAPQNICmAWTti7x34A1tk9CBUKcpXiWakJp1XlDGsLPxmw0FFMpMXUV4fJ/9Ox07

bDu87gLQXPscN3XEkZ4CRx1ymd4DPgO+AuNttQD+AnTM6szAWWYtIjT8ELZ06RkF2dYJTTVGsUlc4QLbXAu0yxXWbNgBjoBCtHJhziwxAuYNp5Rq5OMQAgInRUE9tQNGQOYoGp3IAlB8L6hy3KHA98hKfCsAkPw/vVB9INCChJcD/QPGhNcDWAI3AsLdtwOCWXqc9wNSfZB9P73xIPUDcEwsPM38/Wy+rfzNCHRPAuYYzwLIgO8CYt03AuLdrwN3

AlJ8Sn0fA4Kk1nxiZYhtQwPo/eRcv9XoAGoBZ7SKaLe4cqzeoQBls0h1iT/wMwLIsGxgAhHlseNQwCkpRIitv13UA119/w2f/FDsb3zLApFcKwO4VdpRqwNeAmoA6wK+AzAAfgKbAv98AQI09ZR9acXc3EawkAK20ThJyO3IsTwwdx0pXSAh1lAoAKABLwFVXT7UxILhaGyAxwInAt+lbxy7pRUth1XIsQXloiwKjEaFSgJkPMScksnPA3LhMP2f

xcLcdwNvA0CDep0oAiLd64XiA+ncmCVXAv8CUnxInKyCzIOQfO8DkP3YA58CGmwNA31t+Q2brU0CIOlF/PSDfwOlAf8DCAPYA1yDxeHcgyyDPILy3DZ86Px4Ahj8v9VHA8cDlUEnAnJ0781+gJ6YEGDuec+wsIKKZOPRKthQ5SBhub1+XXRI8GXTUQ8h5TS6EH31kw0dXVPQLJGRcXA1CwNbvd2sk8Vf/fq8fX2G3EDdRHwYg2sDfTXrA1iDGwOb

A8ZNy10FLG2NI51d2TgR7+E+mQoMENxc3N5QWRjfwKJcNLyHAvTIX3WrlS0QwQC+eas44AHF8Zld7BSoSZDIbP3o7TmUt2wrncD1UMw2cBeU7VRWBOYEhkTAAcmYtEWJSdU02qFTjKudLmAR8VW5p5FB0D8J9YkvXZxRHmk8MTihj504LSWVuC0b1fVcJACjAmMD0gnjA70sV/SRdWFVU9iRoWyx1ZBOxV0YybynkLNoPqD1Xa8IEIKQgmkAUINY

9felEYO7jNiRwSFBhM1Z3lEgXYfVibELsAGZbSz7AAstJ+z/9WeMAA3vbMstulCXjW14n5xr5LaDPnhYhNQ9GX0q3YBg1TSDEdB4edlw5bKkYYBDJDwgMFHIFNV1j3wjpNQDpP35PNPtiwIz7UsC3/zsLB4DpuSeAqYAXgP6gj4CWILYgkaDZGxDNZYBNywDfJCMghD6kLzUqKhIXFzdNwmxrSD9BwN3vBOs2xXPYDSCcQLFtVHBYOiRpbScGkgD

gmmkg4L9zPD8A8xfA5a00tUNAixU+F3gfeSDFILSggL0XhRDgp+pzeyBrS3tmNzDAhOwkoJzNZVBtQHznWKIaQGEXFd95O0NuADZ3wR7+GpNXAySmQnkRuRlCE/tVZB4fEiC1YMuA2T92oL6vLPt3/z5rT/8hBQNgo2C3gIGg02DhoI4ggvtXGGWAJisDM0nZJXRcV16lA2YlLWkVE/wVG0hfRxM7PwRAssUJIKkgmSC0QO/mMsVFQHWqMIBLnVk

g27VICCkIDBlJIGWAG6Apg3aDEH1ZgwTCdSDsQIXAiDolwIiHNmAUkHChRxAZez9/BUQtkFTgNABAQGPALUCdoTx9axAH7FGQGJYs9056ef8F8yKJMOhRim0rQqJWJ09ya7MAHSYHb2AxcBiWKAl9CT7/X+DzkzIgPfJAEOfAb4Qm4FSKEPouemcnc7cLK0+6RmlosghHUOC8IlhwG3BvGwJAw3oc63gna487NHwnMydQ4TEmFUNWfxyfRYkmCRO

DehD04OPAkvc34NkeT+DMH0BzH+Cg00cgohCuQJAQ9BDwENCQSBCZDxgQqJ04EIzyRBC8ImQQ2bJUENAQjBCIENkJaDpoCU6JXBD5EOlAQhCZwxIQxAAyEM66JydGiioQ9VgeuxxZOkg34KfqJhDkEnbYIUDFQA4QvyEuENMnWJBeEMcQfhDevxD/TENhEIxDC1hPEJQnLyDGn1gfZp8SPypbMSMgslfgwMcpEOPRL+DZEM8fGlB/4KNyGcNgENM

hIxDVEOCgqBDuunT3bRDAij9qfRDUsFWHUpCscCwQjolYCTkQ/JCCEMKQ48A7EL5oSHp+enonShCialcQ2hC/BziQwqJvEJYQvxC4AACQ2zQogG4QkJCCcj4Q7q0IkMEQ4KCRENGQ4qdxgM2fZf9eAI0jIEBJIOkgp1B7l08qRyQFIBXsWeRAaDVNfV8BVUAOPCDhXlNfZIAHUEeGRbA7MCedMrQy23MkKgJy9X/YPNIpP29ndWDBzy0AtTcOoO7

g3WD2b00vXqYB4JrAoeCTYIbA34Cx4LBvOasf+1HbSdkUMi5eE8t9WXmg/6cT/w6kcS1wZ2gzahdu/RtKd/Ia/T0ZeIAiCHIIW6gMzAOgmcCJdkR8OlIQGxmldUsO/hQzOeVUzig9PLZqAnA4RQwjKHeQ+oxtdEX0MT0043XKcF18XQqAAmDsKSJgqV936UTLU+V15zsUWQCDkjaob05RvAxgi9JyBUngFDJj7jxguOIC4KLg/4AS4IRg5MskYMa

oU0pc8DIMYVgMKyyUXuBExATkBjw/+A4LE5EKRgELH/0Z42LLHl1gAx5gx+cBXQ5VL/VKgDJQilDCZhyrDgRL2EcUGZYX8GBlD4lCSxlGDxRvxAAiAflZN1OAtuCyIPbbTWCX/y7gi6NrNWLXe99e2khQxiDmINhQ9iCoANqqCRIXo1VNClh2widjJ2CsUIngZ5c8VxWg/FD4QJoXGD9/ySxAlO12+ztbKLd5v0DgjZC371KA7tCggAnXGptBUUj

g3GNuF1jg3hcQBQ/Ag8E9kO3gw5D0t1K1FqBzu3iQuKDd8y2QyYDSH3q1OJFmAESAG6AhgDC4EsdXiTIFfVZEbFTwe30wdhSma7RVmleIP/NT3W+jcIw5N3FFQ6MvQRhAdZdxlwEfT18zO0MtLNCfm3jfPqDoUMGgs2D4UJs3Rt1uIMY5MpN03FXgutcxr3E4W35fiRkMUSDT4LLgA+DtgCPglVIVIO2pfTJz4NgIK+Cb4PF1bu174PKaR+C20K0

gjtCPzQT4LUCQ6HSXRPMg4XMgxicrj0WJZZCkc08fbKdqMJpQaxA1WF1SdVhOdwJyEUh/EAEoJndCakZMOycJcnVDcYdKpzxQDbtq6k8nAacrSFiYIacMhX5oIiRccganBPhpiX3RLUDiQKanGydcACondqcZD36Qu2om+Gl4dTCgf196IKFyMJL3SjD4MQyXGjC3IIEw4JZ6ML9yQ0ML8TkQljD2ijYw6th18hJ7Wo8eMMd0PjDkRFgaITCG9yM

wsTC3MNQaaTDeX1kw+TCFhSlkOqBlMMcg1TCo6Fj3DTDrJwonHTDhMPCAcnI2OgMw+vgvWGSw0zCgegSQ+gCkkONArytUkNo3ILILMNGiKzCN0Rsw0BFaMJcnRzCH91QnVzD4MQ27DzCOMJwdD/drs14w4xB+MMCw5HhEJzHuELDjNDCw/Wh+p0iwnE1osPhFWLCPtyeyFTDaFiSwkzDRok0wtgBmp0SQdLCG919yRydOOlywtTDwMRC/MzCV0Kz

HbODYIIjAr/UrcEIARoBJAG2AXOl7ANFgpMCmRgF2YrZdFxL2EttHRhObespqfCjKVosQjF5sN5DE0L+Qgc8X0NfQpVsP0LEvb9Dc+xzQv9CmIOHggtDzYNDnS2CU2jgAwRAsqXPYfiDXPEgwmxNXIkdGdzBqZgQwxEDZvl8obDDr4KnAouciMM0gntdzmXfhDIB7hBiWUd4UxzPRa4RWEJR3caFBICp/fhCmCSLIdZCB0OVDKOhG0FIAaDAAEQL

rEegLGQpoK0BvMJyHC0DnwGmbbbJITF8PfiUHihUQ22g6EJ5wuLJrs34PLEBtACChdnC6cNMQhnD6DyZwqXC2EJNYIGpacKr4bq0ucJBHDwB04L5wnpDwQCFw1oYu63NzT8A7QDwRfhDJkIkJSeptciIkIQAFcNQPZXDjhRGQwMdbcI1w4GBtcPDg4dDXqyjguoCjQISTE0DysMIxEh0qf3pw1nCjcKTHE3DnwDNwjnDLcMCJbnCQ8JC/ERCBcMd

wmMdRcIe3EZB3cO6tT3DZcL2QeXCldz8OBfJA8McQYPCbcJC/MPCKoAjwp0MaP3igmCDEoLggnM1kMNQwo5CsoJu0bCtlgjY8feR7fRz+RFxdZDjEEksgySDEcWIA4h52CgxFT3CMMA5j6XO8TmIY9EjfE99YFwgLEisoKhBw9ZcwcJEvW4CdYL0AsFC43whQmHD80KGguFCi0IxXIOskUMmgysllmluUKNIZWh22E/xPFDfrbwCShkrlav1Vjl1

AO0lM5mVQb3BqUIfg72Cn4LRnBOxzoK5XS6DWUKz1RfD7GAkMFfCSuXT2NKZV4h52T/ouuCTOCVcIXQkAXVDDoGLgumcV5zY9V3kOPQLjX8IuhGRcFQUgXHxXOxQvxEICRRRL7j3kbVCMBi3QndC90IfCa/15Vy7jWw02RWY1cFwX+GcNRCwgZD/4GrQFbEn2d1d0409XFnRvVwP1dmC/V3vnQnZFlxvnDk1xbhAIqYAwCLUXB7CeW36keOQOPAa

of9hO+UmkPZIJDCQYSOQofjG1Y4CM1xagm6dj8LfQiiDBHwU/V/seoKzGXNDjYIAw0eDH8JVKZYBYAJtggBNZFDjUP0Qh3ClrRDd2BHkAmvVMAMeqCnDfYLS9dABDoALwq9Y8gWSI1vDUiPAfOXFp1wcpCRdx0MTYSdDF1yQwuABD4J38RzYXhXSIjxB51i7wlk0TsJBrLmCpgJzNLDDL4NJwjKCZTVVudG8xlUNkaOQUs2qsc+4OTg+UP5ELFwG

2VKU72G10FPQAVFqgowsl5HOUJOQXVAcGS01utzgXSAtWGScIjZdAUJLAnQCL8PuAq/CDAPgkW/C4cPvwwtD/gPHg8NkraSz9V/CVnTaNC5JU5CY2ZYs3uCG8F4gkXAJwolC9QUDUQgB+g1B1SoB/gGblAONm0Jr1VtDKcNOgxlDO+wugkek6PGTXegY1TWswGFUoPgYUUECBBlNNY5EkCNHpYAIkPj/4eudohFm9KygONlGBUBhVdAWIggjRUKI

IwuCSCP1QsgjTVxGxSgiM4mNQyA0Wmj2RLzxYbA1XRRpFyig2fbBvmlkItsodyRP9CoBLsOuw27DZUHsA8gi+VjJg2w0xlWosO5oM2merKmRctGuIHD4CDAvwC1AWYPH+Ists+mvnG/ZVCNZVKstxC3n7HM0PiP8CbYBviJwVMuDjkJL2MIQAhE5ieihRVWERXcI1GjO8UT8zawTQhwj/kLWI0/CbgNHPaiDxz1ogkm0qwMNgqFDYcJhQo4iEcIH

bEd83gWngr6d9bzooDHCSAhpLbHCG3noKJyRYiJb9aAjiMKpw2/l5lSCQmqcB4TV6WQkGkng0OZDsyPVIXMjI8IwxepsFKlnXN8D51wjVacEicIvgnDCaEwzI2ZDgkMLIvSDNkISg7ZC84L8VZQAroDgAO4RlAB/dA9CWpBrJcZUG4PIpLRFIbCZKRxROwIdI2i9lYN7PX8Nk0MKgV9D1iKsLTYjgUIzQkCNIcL7g0DcIHmwXcNleCOBAvVsMAXe

IZS8+DT3LE1tyBUvQvFDW1w9g2Fs4iP8MbXRhvWPvExs9HQ2DDdc8kDeHDJdqfWaFN8j+10/IuKc+QOoAzHsI4Ojw7yD8YyCnZJCmAMTwoUNQgOTId8iklzxyACi2yN7wjsj+8L8VYe8BS18lKYAGbRofPjcqgno8dyJ3lD5OAMRblBIMJ8ZVbiWwU19j+SavbANAcIYsc99/kM0A1citYK2IzqCe4ORXH9DepmUAauA/cPpFB5xrAEqAZQAIhAO

uf4BKgEkgF19IAGWAc9RdgFIAa5woNGrgOAA5eWSYG6ArYIMIZSg/CIngrlsOb2qMfacprzGvAMBMUJgwv2IL7hzEWN9byPs/R6plsDeocECgu17XZE0CQhInUE9iAOsgx9FbHUco7ScqAOMPXD8o8JyI11MSsPjwsrCwpzEjNyiyICcoqgDIIP1tbgDUKPOwnM1oEiEAHgB8AEkAYCAdjUTAvCiQxAIo7MRTmDTXC5hL+FJ0EksS9V3wsqCBGAR

haFFPpGdI9uDYV2uA5m9z8LYo0FD6lX7HUBJuKN4o2V5+KI4AQSjhKJgAUSjxKO0kKSitRVkoqAB5KMUosGp92FUozAB1KJOIsG9V1xRwxtYKqEuIGz85xEuIQVwbbmRsPisW1zPLBL1fOwRkYmxnPz9g5GNwD3aAjo8K7nV4Rg8Hu3ywvCI98jEmawBpaExAILpJbX7QmcBFaHMbDQ8wgBcQNiMCdF+qf/ANIWoHJfNaBxWyAAADQgA/qKhwJVh

X7FTgKOptclsdWxs2SHmPFMgG6iSyZnc0AATHWP9FiXVYcyliSHQvBoVn7w+PELD+cDhomGj8aIRogJAsQGT4KkMYADHybYpJJVDhfAlK8E0HJ/kmii1Ia7tBnwvcMbtwQBnIF2E58kAlHJBLEFj3fHhmHk9SfHMb6BKiQmZANDQASkx9uhOuNi0XfyKApLIE+DQAP6itsL+om94AaM56EEBaOkVo0B0CQnEJPiAogH9qCbIvijxqGlBnmWMQRpx

7j1uo52pPBV4dWXdxKhKiQSAd4Reo25NWeHgomh03chzyWDADaK2QPGo8DzCAAPo2IzRTJwA863WyIHAwUEayN64yaBSHIrJGCXUWSDQZvxpAHPIZOmloM9RKQDDoMQAr71do1RYXWHCAVpcxcDV9fxAEkGWcVM9ahTjMbXIiQ1QAeWjKoz+o93cKcj+ooYBFaIojcpsDrix3akxCwCVYIHBBAAm7fBDa91gwYyc7QBco9IDYKIW/KkCm7mOovFA

VQKZov2oLqOryXakJCTNoj0B7qOoAR6ixu1MQF6i+TAtYd6jOyi+ojkcfqMlqf6jAaOBoj8cwaM/qX9QCQiho/GiaUDxowmikaLFqN7I0aKYADGiiRTGJUTDcaLjqeGiCaJho97pCkBJojLIyaKIACmj/VWposLBaaKeOXVJeeyhQHmi4kBZopgg5kHZo2opOaNKQbmj90V5ohJ9+aKZ9PUxRkGFo8IBRaKYAawkUCSlojvMA6mR4OWiFaKVo9Xp

VaOyAdWi6SFsdLWi3WEHyVDp9aJTII2jJeEayTbodbT06TUhq/2tosXBbaK1ICyZHaL/IxMAXaMwgN2j6GPVYYWgqd19oqtNjEHUlIOidUhOEGIpw6L9oNYko6KF/PHI46NGQIrJE6NXoFOirhEEY9OiAMUzoqeps6N59XOjeHgLolZcOkGpoHUNjEDLowDQK6Io6f3Jq6Nrosptocgbovfcgjhbotuj5shNo5Opu6I4AIw8OQwgfHyiGn2Kwoj8

4HxafDa02n32oqfMPv0HopA8A9wVzM6iggAnoxIprqOeEHW056IXorHMl6NgJZUhV6P4MD6joaA3o9QBOR3kjUujd6JBowZ9waKPoq4oT6Jhos+jn6NN3RGi8H3VzG+jNYCNJTGiw93N6R+jmonPo1+j5j3fo4mih6Omyb+j+8kpovPd7CRponfI6aOAYxmiwGOxZQehIGNiQaBi7ilgY0BiEGJAtJBjlAAFo1BjQkHQYl/ExaOwYswlcGLNaZJZ

CGPLo4hiVaM46chitcyoYnWjqMV6Kd2iikAYYrxjmGIPqH6oLaPYYonIbaJ3AbhiXel4YzddWslQ6NOiHmNwPa4BRGJ9optgJGIDo0pBpGNCAWRiw6PmyCOjFGMTAaOjJHlUY0JB1GM4AJOjkaNTonRjVRAzoyEwDGNGQHOjtCRMYxqxC6OTICxj+6AWQaxjwgFsYnr8sAFLomuiYm3ro9I8m6OYAdxic8kFoLxiAGh8YjgCDw1BLKKiH23FuMe8

iUSyCbTA9/iPYIs9aHwGkUmRP/F8DZ2kVgFyUamQmNSCRIGhAg2DwdyIiS0vGIrY5Y2UiU5Cc9BFYV9gjGGXPFWD98N5PAS9WoJPrMjkvn1cIz0ivF30A6aiAwH2wP3UR3BS8Ebk77iVrBFVtqNhfe3VeqJkouSjoQAUopSiRqOYzMai5bwzfYEiuSRxfBojLLw0qP2x3LyVcQ+sC323gYVgCZxeUGeQvWSlJLsAUvGu0XFdG32ZfCpdbbxJUYO8

yYFmQ4O81hX7fAQBB3w2cYd9LYJFg1WdIb0zvVVJs7x2fL/VjoGOgKAB+IA9ADr0NXyq3eLNUYFgOI8gNtBIVVIgI0jVkNZpnohvQ4+4JGhDAdWR6X2DCeuxQ5CJaJ2lGuHEGYZ4eTyAEfs9FyIFPCq4mb362GqiQUINjP19ejiCIjCEWwjXvfcssN3kvcZgzPjQYE5krKM10E1id7xDRP1j+qMGo4NiVKNDY8ajjzwjYhlCo2JzfHgCrzzLgBJB

sAHRtM7lpOwAgQt8/bAIMGKBsAESNShAHLxvPPPAfWUzAN1kXXzToa29m30awVt8S2KCAMtjcSDSw7t8QLQI4lqdXrGAAdPdY71gvIG8vOVrY5bc9CIbY9Wcp3zSvDM9YbxwvWfhcAGzFS8AAL2Z2KVi+N0DEB0Fu5jKTQhgR2NOQhQxx3CUQDCMctG+dS1ErPxKCWzFWTyopFqg7GEnpPc1ZW0fQyEAt2LefLWNKqM+fAyJvnzgLO1jHHGPYg05

HWNjAYhQIiM0sGS8uK2ETF4hjvHvYr1ibKM83BY5puVfYgNig2OGoz9i1KPDYjaiV/wCA8y9AOMRTONilEnxgERwOEHsKFEBt4B68czIEACBoaUk/QGVJa7koOMHIEWD/LxevQti3r2CvCQBcOKnqSxBy2NMQIjinbzWFWJhyOMkPYgBKOOivApdYzyTveK99Pz85dO90Ly+5ad8jiDQVSQAkohrObWtxoIDSXjjV3yBGGvo7nkc7SnwSFQemanw

VgSNrXXU5IjIsO5RmOSrsdv1r+ziAayw9mwoZJTsGzTU41G0ZWQtYmT8dOLAoPdjDdiog7Yi0F2M43mxTOLOIEBNhvS4OXFdgaD3sezitqMc4tajjghc46Si32MDYoajlKNGo79iFuV/YtvsSMJyXADjtkKA4ioBrMEFmRIBByAFJMOJASVAuHQjt4FKIZvk50EoQQcgC3zwcH09MOPS41l9MuPQAbLiogGDvQji6iVxIRIUgcF2/LHjSONiYcK8

nbzSwszIOX1hwYO960B+vAniSOI2w4nifr0J4+njX7Ec6e2oqOMq4xO8QBnjPBK8VWX85FK8mOKzvdK8c73q1ed9lAFlQJzlWIN7Y4s8ftGZYLfRJOCTSFK5CAi+JZ7ZX9A42YYiwnEU448g6KF2wcdxL4kNBHPlaZAYEH5CQ/XNYzq9LWP/XCoAduOamT9DCbVFPB1jT2JGvL3lKYlDfebA2AQ20cUs4Wxu4p9j3YJfYx7i3OJe4kNivOPTfHzj

eAL846NioqV6IXklQzRt+O5RHgDdZBGAuwE0SO087MjXtLBQnUCowUohMLm4aPQjUuJtvDLi7b12uIWcg71xIWX9yuOmmatinuVBvGzd1iIY4/niML0F4ljjheK/1WeJCxQ/eC7kpeNofFCxjZ3HKZ1BntkV422sJVVWmbCxXiRvQvllHRhL1YuJDEj140YF15EN4+pNnXyLAu6creMNdIR87eN2I47iL7DazALV0wXgGc9i6WE946yjveL23a/C

oEFc4gajnuI/Yt7jvOL3vWAjovH84v7jAuLLgaKAB4looU4AyaGOALE9KZ22AdC5DMAxMCUkj/ki4xLhOQkxPPy9keIDPfPiSVE+oIvjg71L4ytjvgAr42jj/3zTPFC8J3wa45ASG+JnfL/UaQHM3V+gjAGpADvi+NwzSdcgcplXacgpVo3pfCrQfcVZmfbEMAwyONvkluN/QDrc10EzSAxgI9C48Zc4wCyWI9WNNOIVbN19F3WX4jxc3CJwKe3j

57yC9DqQVo1TtLHD17zBXIohj+Gu4w/jdt2iXB7i+qP94y/iv2Ov4hOtI2L2se/j10L2vd0g4pgaAPMA8AD8qERxobFA4xzlXonsKAWYuYDg47yYfJAJnfNiArxR4lt80eIgAPLiqUIq4hO8xX2q4qviEr1cRWvjZXybYtOgW2L4Ar/VBiV9NOAAbIC/PAgTV3wr6cDZZmQ5OLoRvSSg2T/NPqFLicoJa7H1YpTjteONYpgT5sBn4iUjBvTi0Bfj

zeL63FrkPXzPwj0j9uKRXQ7ipzwd4r6dOzw4OF408AXEtKNJIQKb7L3jFBNWgvYjGsDP499iPOKv44Pib+NPPTmUdBJjYvQTgOOOAa7lRuTOvUmgfzxpnM4AEQELfUJhWCJp0Q+sPTwySekQwBJAvAvj0eLp4ipd2eK8Eod8fBIlfBK81+3HfRtiBeObYoXjW2JzNKYBSAGOgQSh72itwKyBY6NTAOABK8liYfXFl33/obriMtmDxMKAnQVLjC6c

UrmnYoftAVAPIVWtHn3m4p/gLSOTuSM5WkxYEu91qKgLwSpQShM24j59tuIqE90ivX1qoo9iRBJsiDwssQKdUOc9d+SL9ZGwfiWPVT1jOhJ9YoQU+hIv4gYT1BKGEzQS/2O0E8Pjb5zxfLlUwUW8mN7ZaXy/EH1llgl/QZBgzrzlJJ0AoGB0It5RHBLS48ATUeN2EtwTcSArYw4TYrxOEkd8UqIuExjj6+OuExvjbhL8VB9V1qk25B4IhgCGDTQB

LwEDNRSjq4BzFbjiSLxOfPjil5CZKQlUP/EFjJ8Ms9G4bLfDckkUAv/YGSi14o1iq7CmIzOB9eNn4kbkjePRExiirgN041o5KhNxEw9itE1qE7KBjuMakUHQvxGd47Z0gjGQsSaUD+MfYroSG0JP43oS/ePP49zjXuKZE9F9PuIRNZ8ixhIj4zkT0AHqMOzlv+NCYHgAEQDFJKYBXWVNQERw3rm+tIYAyaG8mDvwHOXXQJHim32cE7DjXBKZ4g4T

PBOVErnjk730/MXUAhMnfTUTghJuE0IT/qWZgF4AiSBXRboBAnGgAbYk3IEQge4AxgAYARToKABWSdsdXSN3E0WkL4AhwDIA6QEW9Bij6Z0gY7mRugHIhVPsxqGXIuacMONvEm5x7xMG/KqjXxLPE+8TLxJ+fb8TJJF/EjcjBiAAku8SMgFFxQBJQJPfEjIAdl2mNKCTzxPNwUsityHgkj8T/GN8gFCSMgHUgRJCbxJ/Ei8TnUMuoDCT9AGSZRQj

oIhEaQiTC5EvATfhgYD6AQiTgIDegJ2FhQGXQeATpI3wAR6AwbEXKEBUYmjDSUMBdxN0eUEB8AAbgdiSSS3sUChgCnV2dBxhJXibQCJhSvAYAdNU3fXOATKhCJMbhGyIyxhoksUghLRoAsSwSADvAQYBdxPUkjqJkmW0XSKQ+bBIAT8gTcB/eJ79dlGUAFEAgcAjwGFMpDHYQcMBaGBDwUR5r7TOFX3BrJNwAWySfp14AHySjvFhwZWQ2eKnYKCS

/xMBAKZd8NyIESewrzGuKYvx85CMk2J0x8gzPQlkDlxZNSOig0nWfD0gSQEBAUgB/lUyAWJ1rEEFwpgBDJPEcRcAk4EUk+hY/tQJoAyTnFl30F4BkkEYAFFZQQFikwphvaJJwL/krb1KXSiTQCCGzbF8DAFB6NqS722YcWFisgiwgBqSm0GJRZrjgpKHMbRcz1FggSkwrQGTsI3BDOU0YBwgDICAAA==
```
%%