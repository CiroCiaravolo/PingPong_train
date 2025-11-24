# PingPong_train
A Yolo Model for PingPong amateur matches

# 🏓 Ping Pong Scene Understanding

A Computer Vision project using **YOLO**, **Transfer Learning**, and **Polynomial Interpolation** to analyze amateur ping pong matches.

## 🎯 Motivation

Amateur sports analysis often lacks automated tools for **statistics** and **fault detection**.
Table tennis is particularly challenging due to:

* **Fast dynamics**
* **Small objects** (ball, paddles)
* **Low-quality footage**

Our goal: build a **scene understanding system** that can detect and track objects in amateur ping pong videos with minimal labeling effort.

---

## 📂 Project Scope

* Built a dataset **from scratch** (13 amateur matches)
* Applied **transfer learning** with YOLO
* Used **self-labeling** to expand the dataset
* Applied **data augmentation** (crop, brightness, exposure, blur, noise)
* Filled tracking gaps with **polynomial interpolation**
* Showcased an application: **bounce detection**

---

## 📊 Dataset & Methodology

* Started with ~250 manually annotated frames (via Roboflow).
* Iterative **self-labeling loop**:

  1. Train YOLO on small dataset
  2. Predict new labels
  3. Review and refine
  4. Repeat

➡️ Result: **8k labeled frames** with very little manual work.

---

## ⚙️ YOLO Transfer Learning Setup

* Base model: **YOLO (Ultralytics)**
* Backbone frozen up to layer 10
* Early stopping with low patience (to avoid overfitting)
* Hyperparameter tuning for best **mAP50**

📌 Key challenge: detecting the **ball** (small, fast, blending with background).

---

## 🧮 Polynomial Interpolation

To estimate missing ball positions:

* Fit separate 2nd-degree polynomials for x and y over time
* Predict missing frames
* Good for **smooth trajectories**, less accurate on **collisions**

---

## 🚀 Example Application: Bounce Detection

Heuristic-based approach:

* Expect bounce if ball moves toward table area
* Confirm bounce if vertical direction reverses (descending → rising)

---

## ✅ Results & Conclusion

* End-to-end pipeline built **from scratch**
* Large dataset obtained with minimal effort
* Effective tracking system for amateur videos
* Demonstrated practical feasibility for **amateur tournament analysis**

---


---

## 💻 How to Run




   
2. Open the notebook in **Google Colab** or Jupyter. https://colab.research.google.com/drive/1tRM0ee0IM94lHsl1ajLS6pIgpNwlwNkL?usp=sharing&authuser=3#scrollTo=GN-j5Q-CXxu2
3. Train the YOLO model with provided dataset or your own.
4. Run the interpolation script for ball tracking.

---

## 🔮 Future Work

* Improve interpolation on collisions
* Extend analysis to **serve recognition** and **fault detection**
* Deploy a lightweight web app for match analysis

---
