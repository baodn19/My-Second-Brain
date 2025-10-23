# Canny
- *Usage:* reliable for object detection, image segmentation, feature extraction
- *How:*
	- Smooth image w/ gaussian filter
	- Gradient of image w/ sobel
	- Non-maximum suppression: thin out edges
	- Double thresholding to keep edges above max