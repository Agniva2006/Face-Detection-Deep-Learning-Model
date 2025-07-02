# Gender-Detection-Machine-Learning-Model
A gender detection model based on deep learning, created for the Comys Hackathon.



# 🚀 Hackathon Task B: Face Recognition (Folder-wise Matching)

---

## 📌 Task Objective:

> *Given a test face image (real or distorted), match it against its correct person folder.*

###  Success Criteria:

|                                                                                                                              | Condition |
| ------------------------------------------------------------------------------------------------------------------------------ | --------- |
| ✅ If the test image (or distorted version) *matches any image inside its true person folder* → *Label = 1 (Correct Match)* |           |
| ❌ If it does *not match any image from its true folder* → *Label = 0 (Non-Match)*                                          |           |

---

## 📌 Dataset Structure:


/train/
    /Person_1/
        image1.jpg
        /distorted1/
    /Person_2/
        image2.jpg
        /distorted2/
/val/
    /Person_101/
        imageX.jpg
        /distortedX/
    /Person_102/
        imageY.jpg
       / distortedY/

***distoted folder contains blurred,foggy,lowlight,noisy,rainy,resized,sunny images
* Each folder = 1 unique individual
  Val contains persons not present in train
* Distorted images exist inside folders alongside real images

---

## 📌 Solution Approach (FaceNet + Cosine Similarity Matching):

| Step                                                              | Description                                                                     |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------- |
|  1                                                               | *Use FaceNet (Pretrained on VGGFace2)* to extract face embeddings             |
|  2                                                               | *Build reference embeddings for all images* from both train and val folders   |
|  3                                                               | For each validation image:                                                      |
| → *Compare its embedding with all embeddings in its own folder* |                                                                                 |
| → Calculate *cosine similarity*                                 |                                                                                 |
|  4                                                               | If similarity ≥ threshold (0.6 used), predict *Label = 1 (Match), else **0* |
|  5                                                               | Output validation accuracy and per-image prediction logs                        |

---

## 📌 Result:

| Metric                    | Value                                                                  |
| ------------------------- | ---------------------------------------------------------------------- |
| Final Validation Accuracy |  *1.0000 (3376 / 3376)*                                             |
| Method                    | *Folder-wise matching with FaceNet embeddings and Cosine Similarity* |

---

## 📌 How to Run:

1.  Upload dataset to Google Colab (train + val folders)
2.  Run FaceNet Cosine Matching notebook
3.  The notebook will:

   * Build reference embeddings
   * Evaluate val set
   * Print image-wise similarity and prediction
4.  For custom testing → Upload any image → Run final test cell

---

## 📌 Extra: Test on Any Distorted Image:

Notebook contains a final cell where you can upload *any single image (distorted or real)*
→ It will tell you:

* Which person folder it matches
* Max similarity
* Predicted label (1 or 0)

---
