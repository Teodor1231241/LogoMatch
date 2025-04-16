# LogoMatch
Clustering Photos by color and shapes Similarity – w/o ML
This project has been made for matching logos but can be used for any group of pictures
LogoMatch is an innovative approach to grouping pictures based on color and features similarity—without relying on standard ML clustering. Instead, it leverages computer vision techniques and perceptual hashing to mimic how humans visually match photos.

Key Features
-logo Extraction – isolates logos from websites ~99%+ success rate - some of the links in the parquet file don't work
-similarity Scoring – uses perceptual hashing and SSIM Structural Similarity for comparisons
-ML-less clustering – groups pictures via connected components
-tested on 10K+ URLs

Tech Stack
-Python (OpenCV, Pandas)
-JS - json file compiler to png

Comparison Table
Algorithm    	         |Color      |FocusShape/Text       |Focus Speed	     |Scalability <br>

Color Histogram	       |✅ High	   |❌ Low N/A to text	   |Fast	             |High			<br>
Color Perceptual Hash	 |✅ Medium	 |✅ Medium	             |Fast	             |High			<br>
SSIM on RGB          	 |✅ Medium	 |✅ Medium	             |Slow	             |Low				<br>
SIFT/SURF on RGB	     |✅ Medium  |✅ High	             |Slow	             |Low			<br>
Color-based Hu Moments |✅ Medium	 |✅ High              |Medium             |Medium			<br>
ORB + Color Preprocess |✅ Medium	 |✅ High	              |Slow	               |Medium			<br>
OCR + Color Features	 |✅ Medium	 |✅ High               |Slow	               |Low			<br>

Algorithms used:
1/ Color Histogram Comparison
Compares color distributions using histograms in RGB/HSV/LAB color spaces.

Pros:
-Directly uses color as a primary feature (e.g. Coca-Cola red vs. Netflix red).
-Works for partial matches (e.g., logos with similar palettes colors).
-Fast 2690 photos ~1 min

Cons:
-Ignores spatial structure
-Sensitive to lighting/contrast change

2/ ORB with Color Preprocessing
Applies ORB (Oriented FAST and Rotated BRIEF) to detect keypoints in color space.
Uses color thresholds to isolate photo's regions before feature extraction.

Pros:
Combines color and edge/shape features.

Cons:
Less accurate for low-contrast or gradient-heavy photos.
Long processing time - ~2690 photos in 90 min

Usage:
1- 2-Python notebooks
2- Website links are stored in a parquet file
3- output 4k/8k png of all the similarities found in photos
