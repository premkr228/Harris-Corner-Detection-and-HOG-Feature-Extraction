# Harris Corner Detection and HOG Feature Extraction

1. Objective of the Project

The objective of this project is to study and implement two fundamental feature extraction techniques in classical computer vision: Harris Corner Detection and Histogram of Oriented Gradients (HOG). The goal is to understand how local image structure can be captured using gradient information, and how these features can be visualized and interpreted for further use in tasks such as object recognition and image analysis.

2. Image Loading and Preprocessing

The input image is loaded in grayscale format since both Harris corner detection and HOG rely on intensity variations rather than color information. Working in grayscale simplifies gradient computation and reduces unnecessary complexity. A basic check is included to ensure that the image file is present in the working directory before processing begins.

3. Gradient Computation using Sobel Operators

To detect corners, the first step is computing image gradients in the horizontal and vertical directions. Sobel operators are used for this purpose as they provide a good balance between noise suppression and edge localization. The horizontal gradient captures intensity changes along the x-axis, while the vertical gradient captures changes along the y-axis. These gradients are essential for analyzing how pixel intensity varies in local neighborhoods.

4. Derivative Product Calculation

Once gradients are computed, the squared gradients and cross-product terms are calculated. These derivative products describe how intensity changes behave within a small window around each pixel. The squared terms measure variation along individual axes, while the cross-product captures the interaction between horizontal and vertical changes. Together, these values form the basis of the structure tensor used in Harris corner detection.

5. Gaussian Smoothing for Noise Reduction

Gaussian smoothing is applied to the derivative products to reduce noise and ensure stable corner responses. Instead of responding to isolated pixel-level variations, the detector considers aggregated information from a neighborhood. This step improves robustness and helps suppress false corner detections caused by noise.

6. Harris Corner Response Computation

Using the smoothed derivative products, the determinant and trace of the structure matrix are computed. These values correspond to the eigenvalues of the matrix, which represent intensity variation along different directions. The Harris response function combines these terms into a single scalar value for each pixel. Strong positive values indicate corner-like regions, while negative or small values indicate edges or flat areas.

7. Thresholding and Corner Detection

To extract actual corner points, the Harris response map is thresholded using a percentage of its maximum value. Pixels whose response exceeds the threshold are classified as corners. This converts the continuous response image into a binary map that highlights significant interest points. The detected corners are visualized alongside the original image for easy interpretation.

8. Interactive Parameter Exploration

An interactive version of the Harris detector is implemented using sliders for block size, Sobel kernel size, and the sensitivity parameter k. This allows real-time observation of how parameter choices affect corner detection. Increasing the block size results in fewer but more stable corners, while adjusting k controls sensitivity to edges versus corners. This interaction provides strong intuition about the algorithm’s behavior.

9. Visualization of Harris Corners

Detected corners are overlaid on the original image using colored markers. This visualization confirms that corners tend to appear at intersections, object boundaries, and textured regions. It also highlights areas where parameter choices may cause over-detection or missed corners.

10. Histogram of Oriented Gradients (HOG) Feature Extraction

In addition to corner detection, the project implements Histogram of Oriented Gradients (HOG) for feature extraction. HOG captures the distribution of gradient orientations within small spatial regions of an image. This makes it effective for describing object shape and structural patterns, rather than individual pixel values.

11. HOG Feature Computation Process

The image is divided into fixed-size cells, and within each cell, a histogram of gradient orientations is computed. Neighboring cells are grouped into blocks, and normalization is applied to improve illumination invariance. The result is a high-dimensional feature vector that encodes edge direction and strength across the image.

12. HOG Visualization and Interpretation

The HOG visualization displays dominant gradient orientations using line patterns. These patterns often resemble contours and object boundaries present in the original image. This confirms that HOG captures meaningful structural information and explains why it has been widely used in classical object detection pipelines.

13. Feature Vector Characteristics

The final HOG feature vector is printed to show its dimensionality. This vector can be directly used as input to traditional machine learning models such as Support Vector Machines or Logistic Regression. The dimensionality depends on image size and HOG parameter choices, highlighting the trade-off between detail and computational cost.

14. Observations and Limitations

Harris corner detection performs well on images with strong geometric features but may struggle in low-texture or noisy regions. It is sensitive to parameter choices and does not provide scale invariance. HOG features are effective for capturing shape information but may lose fine texture details and can be affected by large geometric distortions.

15. Conclusion

This project demonstrates how classical computer vision techniques extract meaningful features using gradient-based analysis. Harris corner detection identifies salient interest points, while HOG provides a structured representation of local edge patterns. Together, these methods form a strong foundation for understanding feature extraction and offer valuable insight into how vision systems worked before the rise of deep learning.
