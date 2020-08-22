# road_lane_detection


Autonomous driving is one of the most disruptive innovations in the field of AI. Fuelled by deep learning algorithms they are creating new opportunities in the sector of mobility.
It’s very essential to train the autonomous driving model which can perform the same actions as an experienced human driver. One of the many steps involved during the training of 
an autonomous driving model is lane detection, which is the preliminary step. This project aims to detect lane lines based on the view of vehicle mounted camera using OpenCV.
We will capture the video using VideoCapture object and after the capturing has been initialized every video frame is decoded (i.e. converting into a sequence of images).
The video frames are in RGB format, RGB is converted to grayscale because processing a single channel image is faster than processing a three-channel colored image. 
Noise can create false edges, therefore before going further, it’s imperative to perform image smoothening. Gaussian (GaussianBlur) filter is used to perform this process.
Canny Edge Detector is used to compute gradient in all directions of the blurred image and traces the edges with large changes in intensity. The objective is to perform
edge detection of images in real-time. OpenCV has in-built function cv2.Canny() which takes our input image as first argument and its aperture size(min value and max value) 
as last two arguments. The canny function calculates derivative in both x and y directions, and according to that, we can see the changes in intensity value. Larger derivatives 
equal to High intensity (sharp changes), smaller derivatives equal to Low intensity (shallow changes).
Region of Interest (ROI) is to take into account the only region covered by the road lane. A mask is created here, which is of the same dimension as our road lane image. 
Furthermore, bitwise AND operation is performed between each pixel of our canny image and the mask. It ultimately masks the canny image and shows the region of interest 
traced by the polygonal contour of the mask. The Hough Line Transform (cv2.HoughLinesP ()) is a transform used to detect straight lines. The Probabilistic Hough Line Transform 
is used here, which gives output as the extremes of the detected lines.
