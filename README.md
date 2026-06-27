# Signiq AI Models

Signiq AI uses custom-trained machine learning models to recognize ASL fingerspelling through hand landmark data.

The recognition system is split into two separate models:

* A **static handshape model** for ASL letters `A-I` and `K-Y`
* A **motion model** for the moving ASL letters `J` and `Z`

## Static Model

The static model recognizes non-moving ASL fingerspelling letters using normalized MediaPipe hand landmarks.

Instead of classifying raw images directly, each training image is converted into a 21-point hand landmark representation. These landmarks are normalized and used as the input features for the classifier.

**As of Friday, June 26, 2026:**

* The static dataset contains approximately **4,000 images per letter**
* The model recognizes ASL letters `A-I` and `K-Y`
* `J` and `Z` are excluded from the static model because they require motion
* The static model achieves approximately **98% accuracy**
* The trained static model is saved as:

```text
signiqo_model.joblib
```

## Motion Model

The motion model recognizes the dynamic ASL letters `J` and `Z` using short sequences of hand landmarks.

Each motion sample is represented as a sequence of landmark frames, allowing the model to classify movement patterns rather than single hand poses.

**As of Friday, June 26, 2026:**

* The motion dataset contains **714 usable landmark sequences**
* `J`: **317 sequences**
* `Z`: **397 sequences**
* The motion model recognizes ASL letters `J` and `Z`
* The motion classifier achieved **100% test accuracy** on the current processed motion dataset
* The trained motion model is saved as:

```text
motion_model.joblib
```

## Current Model Notes

The models are still being refined with additional targeted training data. Some visually similar static handshapes may require more diverse examples to improve reliability in real webcam conditions, including different lighting, hand angles, distances, and finger positioning.
