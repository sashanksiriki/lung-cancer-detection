# lung-cancer-detection

##Image Enhancement Techniques (Stage 2)

Applied in this sequence, using OpenCV:

Median Filter (MF) — noise reduction; replaces each pixel with the median value of its neighborhood, removing salt-and-pepper/Gaussian noise
cv2.medianBlur(img, ksize=5)
Histogram Equalization (HE) — boosts global contrast by redistributing pixel intensity values across the full range
cv2.equalizeHist(img)
CLAHE (Contrast Limited Adaptive Histogram Equalization) — enhances local contrast by equalizing small 8×8 tiles individually, with clipping to avoid noise amplification
cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8,8))
Morphological Operations (Dilation + Erosion) — sharpens edges and refines structures by expanding then shrinking bright regions
cv2.dilate() followed by cv2.erode()

##Preprocessing Methods (Stage 3)
Resizing — standardized all images to 224×224 pixels for model input consistency
Data Augmentation (training set only):
Random horizontal flip
Random vertical flip
Random shear (±20%)
Rescaling/Normalization:
For custom CNN: pixel values scaled to 0–1
For pretrained models (VGG16/EfficientNetB0): model-specific preprocess_input() functions (mean-subtraction/scaling matching their original ImageNet training)
Patient-level stratified train/val/test split — grouped CT slices by patient ID before splitting, to prevent data leakage from near-identical slices appearing in both train and test sets
