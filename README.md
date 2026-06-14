#Sudometrics Project — AI Image Analysis for Diabetic Neuropathy Screening
GitHub: NKAI2202Location: Cambridge, UKStatus: Completed Project
Project Overview
This project develops a complete AI‑powered image analysis pipeline to quantitatively assess sudomotor function from Neuropad test images, used for early detection of diabetic peripheral neuropathy (DPN). The system processes mobile‑captured photos, corrects for capture variations, segments colour regions, and provides a probabilistic measure of dysfunction — offering a robust, reproducible alternative to visual inspection.
The entire workflow — from image loading and correction to segmentation, modelling, evaluation and clinical interpretation — is contained in a single Jupyter Notebook file: annproj.ipynb.
Problem Background
Diabetic peripheral neuropathy is a common complication of diabetes that damages small autonomic nerves controlling sweat glands. Damage occurs early, often before symptoms appear. The Neuropad test uses a colour‑changing pad: starting blue, it turns pink when sweat is produced. Current practice relies on subjective visual assessment, with no standardised way to measure partial colour change or track changes over time. This project solves that by turning the test into a precise, digital, quantifiable screening tool.
1. Pad Detection and Region Extraction
The pipeline automatically locates and isolates the coloured test pad from the full image:
Detects the mounting card and ArUco markers placed at each corner
Identifies whether the image is from the left or right foot using marker coding
Crops and extracts only the relevant colour‑change area, removing background and card elements
Saves the extracted region as a separate, uniform image for further processing
2. Geometric Correction and Normalisation
To ensure consistency regardless of how the photo was taken:
Uses ArUco marker positions to calculate rotation, perspective skew, and distortion
Applies perspective transformation to warp the image into a perfectly rectangular, aligned view
Resizes all extracted pads to the same fixed dimensions
Ensures all samples share identical scale, orientation and shape for reliable comparison
3. Pre‑processing and Image Enhancement
A robust pre‑processing stage addresses real‑world capture challenges:
Performs white balancing and colour correction to standardise under different lighting
Detects and removes shadows or glare using adaptive thresholding and colour space analysis
Reduces noise while preserving edges and colour boundaries
Normalises brightness and contrast to make results consistent across different cameras and environments
4. CNN‑Based Colour Segmentation
Instead of simple colour thresholds, a Convolutional Neural Network is trained to segment the image:
Classifies every pixel into three categories: blue region, pink region, or transition/mixed region
Learns the true colour distribution and transition behaviour of the test pad
Outperforms rule‑based methods by handling variations in shade, saturation and partial colour change
Produces a precise segmentation mask showing exactly where and how much colour change occurred
5. Probabilistic Assessment of Sudomotor Function
The model outputs a continuous score rather than a pass/fail result:
Calculates total percentage of blue and pink areas
Measures how gradually or sharply the colour changes between them
Combines area coverage and colour intensity into a single probability score representing the degree of sudomotor dysfunction
Maps this score to clinical risk levels: normal, mild impairment, moderate impairment, severe impairment
6. Model Explainability and Visual Interpretation
To support clinical trust and understanding:
Generates heatmap overlays using Grad‑CAM to highlight which regions of the pad most influenced the output
Shows exactly where the model detected blue, pink or mixed zones
Provides visual evidence alongside the numerical score, making results interpretable for clinicians
7. Reproducibility and Reliability
The solution is designed to give the same result every time:
Tested on multiple images of the same pad taken from different angles, lighting and devices
Outputs remain consistent within small tolerance ranges
All steps are deterministic and fully documented
Ready for integration into backend systems for clinical use
8. Longitudinal Analysis and Clinical Insight
This project also includes functionality and discussion for longitudinal monitoring:
Probabilistic scores from repeated scans (e.g. every 3 months) can be stored and compared over time
Trends can be calculated: stable function, gradual decline, or improvement following intervention
Enables clinicians to track progression of neuropathy, evaluate effectiveness of treatments, or adjust care plans early
Turns a single screening test into a long‑term monitoring tool for patient health
Tools and Libraries Used
Python 3
OpenCV, NumPy — image processing, geometric correction, filtering
Scikit‑learn — metrics and evaluation
TensorFlow / Keras — CNN model design, segmentation, training
Matplotlib — visualisation, heatmaps, results display
Jupyter Notebook — full code, documentation and results in one file

Repository Structure
plaintext
/
├── README.md          # This file — full project explanation
└── annproj.ipynb     # COMPLETE PROJECT: all code, models, analysis and results
Skills Demonstrated

Image processing: detection, correction, segmentation, enhancement
Deep learning: CNN design, semantic segmentation, model training
Colour analysis and feature extraction
Probabilistic modelling and risk scoring
Model explainability and visualisation
Clinical data interpretation and longitudinal trend analysis
End‑to‑end pipeline development for real‑world medical screening
About Me
NKAI2202 — Final‑year Artificial Intelligence student based in Cambridge, UK.Available immediately for roles in Machine Learning, Computer Vision, Medical AI or Image Analysis.
