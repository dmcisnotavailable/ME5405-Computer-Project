

### Q8 Q9 

 The goal is to train, validate, and test a k-Nearest Neighbors (kNN) classifier to recognize 6 characters ('1', '2', '3', 'A', 'B', 'C') from the `p_dataset_26` dataset.

This part includes two implementations:

1. **`q8q9/`** **(Original Model):** A kNN classifier using **raw binarized** **pixel** **vectors** (1x676) as features. This model is highly sensitive to translation and preprocessing artifacts.
2. **`q8q9HOG/`** **(Improved Model):** A robust kNN classifier using **Histogram** **of Oriented Gradients (HOG)** features. This is the final, recommended version that solves the sensitivity issues of the raw pixel model.

### Prerequisites

1. **MATLAB** with:
   1. Image Processing Toolbox (3) (for `imresize`, `imbinarize`, etc.)
   2. Statistics and Machine Learning Toolbox (for `extractHOGFeatures`, `mink`, `mode`)
2. Dataset Path: The scripts use a hardcoded path. You MUST place the p_dataset_26 folder at: ~\Computer Project\p_dataset_26
3. Test Image Path: The final test script expects the 6 segmented characters from Image 2 (e.g., 1.png, A.png) to be located at: ~\predict\image2

### Step-by-Step Execution (HOG Model)

1. **Train Model:** Run `q8q9HOG/HOG_KNN_train.m`. This will process the 75% training split, extract HOG features, and create `Train_HOG_data.mat`.
2. **Create Validation Set:** Run `q8q9HOG/HOG_KNN_val.m`. This will process the 25% validation split and create `Validation_HOG_data.mat`.
3. **Run** **Validation** **(Optional):** Run `q8q9HOG/HOG_KNN_predict.m`. This will test the model on the validation set and print the accuracy (Expected: ~98%).
4. **Run Sensitivity Analysis (Optional):** Run `q8q9HOG/HOG_k_sensitivity.m`. This will generate a plot showing model accuracy vs. different `k` values (Task Q9).
5. **Run Final Prediction on Image 2:**
   1. Ensure your 6 test images (e.g., `1.png`, `A.png`...`C.png`) are in the correct `predict/image2` folder.
   2. Run `q8q9HOG/HOG_KNN_test.m`. This will output the final classification results for the 6 characters (Task Q8).