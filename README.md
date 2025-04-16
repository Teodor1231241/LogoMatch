# LogoMatch
Clustering Photos by color and shapes Similarity – w/o ML <br>
This project has been made for matching logos but can be used for any group of pictures <br>
LogoMatch is an innovative approach to grouping pictures based on color and features similarity—without relying on standard ML clustering. Instead, it leverages computer vision techniques and perceptual hashing to mimic how humans visually match photos. <br>

**Key Features** <br>
-logo Extraction – isolates logos from websites ~99%+ success rate - some of the links in the parquet file don't work <br>
-similarity Scoring – uses perceptual hashing and SSIM Structural Similarity for comparisons <br>
-ML-less clustering – groups pictures via connected components <br>
-tested on 10K+ URLs <br>

**Tech Stack** <br>
-Python (OpenCV, Pandas) <br>
-JS - json file compiler to png <br>

**Comparison Table <br>
**Algorithm    	         |Color      |FocusShape/Text       |Focus Speed	     |Scalability <br>

Color Histogram	       |✅ High	   |❌ Low N/A to text	   |Fast	             |High			<br>
Color Perceptual Hash	 |✅ Medium	 |✅ Medium	             |Fast	             |High			<br>
SSIM on RGB          	 |✅ Medium	 |✅ Medium	             |Slow	             |Low				<br>
SIFT/SURF on RGB	     |✅ Medium  |✅ High	             |Slow	             |Low			<br>
Color-based Hu Moments |✅ Medium	 |✅ High              |Medium             |Medium			<br>
ORB + Color Preprocess |✅ Medium	 |✅ High	              |Slow	               |Medium			<br>
OCR + Color Features	 |✅ Medium	 |✅ High               |Slow	               |Low			<br>

**Algorithms used:** <br>
**1/ Color Histogram Comparison** <br>
Compares color distributions using histograms in RGB/HSV/LAB color spaces. <br>

Pros: <br>
-Directly uses color as a primary feature (e.g. Coca-Cola red vs. Netflix red). <br>
-Works for partial matches (e.g., logos with similar palettes colors). <br>
-Fast 2690 photos ~1 min <br>

Cons: <br>
-Ignores spatial structure <br>
-Sensitive to lighting/contrast change <br>

**2/ ORB with Color Preprocessing** <br>
Applies ORB (Oriented FAST and Rotated BRIEF) to detect keypoints in color space. <br>
Uses color thresholds to isolate photo's regions before feature extraction. <br>

Pros: <br>
Combines color and edge/shape features. <br>

Cons: <br>
Less accurate for low-contrast or gradient-heavy photos. <br>
Long processing time - ~2690 photos in 4h 20 min <br>

**Usage:** <br>
1- 2-Python notebooks <br>
2- Website links are stored in a parquet file <br>
3- output 4k/8k png of all the similarities found in photos <br>
