# Image-stitching-from-scratch-and-OpenCV
The panorama stitching algorithm can be divided into four basic fundamental steps. These steps are as follows:

1) Detection of keypoints (points on the image) and extraction of local invariant descriptors (SIFT feature) from input images.
- Resize and apply Gaussian blur on different levels for extracting local feature (SIFT) -> keypoints.
2) Finding matched descriptors between the input images.
- Descriptor of the keypoint bases on the neighborhood of that keypoint -> collect gradient histogram.
- Merge them into a descriptor vector -> homographic matrix
3) Calculating the homography matrix using the RANSAC algorithm.
- Homography matrix is a 3x3 matrix that illustrates the same local feature
  |a11  a12  a13| -> horizontal transform, scalling, rotation
  |b11  b12  b13| -> vertical transform, scalling, rotation
  |c11  c12  c13| -> Perspective transform -> RANSAC algoritm
4) The homography matrix is then applied to the image to wrap and fit those images and merge them into one.

  In case of stitching only 2 images together to create a panorama, we didn’t face any difficulty
and it was a straight forward process. But in case of stitching many images together, we see
that as we stitch more and more images, images near to the side starts getting distorted
=> Cylindrical Projection and Unroll involves the projection of the images onto a cylinder, unrolling them,
and then stitching them together.
![image](https://github.com/nttrung2406/Multiimage-stitching-from-scratch-and-OpenCV/assets/105348335/970abe0c-ea4c-44de-a9a8-30d6b68068b6)
