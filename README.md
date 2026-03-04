# Homography Estimation, Panorama Stitching, and AR

This repository contains a complete Python pipeline for estimating homographies, stitching multiple images into panoramas, and creating a basic Augmented Reality (AR) video application. The core logic is built from scratch utilizing Direct Linear Transformation (DLT) and RANSAC, relying on OpenCV primarily for feature extraction and final image warping.

## Overview

The project demonstrates how to project points from one plane to another using homography matrices. It is split into two primary applications:
1. **Panorama Stitching:** Taking a sequence of images from a single viewpoint and stitching them into a wide-field panorama.
2. **Augmented Reality (AR):** Tracking a target object (a book cover) in a video and mapping a source video onto it dynamically.

## Features

* **Feature Detection & Description:** Supports SIFT, SURF, and ORB algorithms.
* **Feature Matching:** Utilizes Brute-Force (BF) or FLANN matching with Lowe's Ratio Test.
* **Robust Homography:** Custom implementation of Normalized DLT combined with RANSAC for outlier rejection.
* **Image Blending:** Distance-transform-based smooth linear blending for seamless panoramas.
* **Performance Benchmarking:** Includes an automated ablation study and benchmarking script to compare SIFT vs. ORB across multiple scenes.
* **AR Video Generation:** Smooth quad tracking (via Exponential Moving Average) to project video frames onto moving objects in real-time.

## Datasets

Please note that the datasets used in this project are **not included** in this repository. To run the notebook successfully, you will need to provide your own image and video data and organize it according to the following directory structure in the root of the project:

* **`panorama_dataset/`**: Create subdirectories for each scene you want to stitch (e.g., `panorama_dataset/my_scene/`). Place the sequence of images inside their respective scene folders.
* **`ar_dataset/`**: Place the necessary files for the AR task here. By default, the code expects the following filenames:
  * `book.mov`: The target background video.
  * `ar_source.mov`: The video you want to overlay.
  * `cv_cover.jpg`: The reference template image to track.

## Requirements

To run the notebook, you will need Python 3.x and the following libraries:

```bash
pip install numpy opencv-python opencv-contrib-python matplotlib pandas
```

## Some Outputs

Using ORB:

<img width="6000" height="3369" alt="v_bird_orb_panorama" src="https://github.com/user-attachments/assets/9440c107-5496-4309-932a-9565678ab7b6" />

<img width="2445" height="2462" alt="v_circus_orb_panorama" src="https://github.com/user-attachments/assets/6c2df036-0f22-4231-8143-06d2c7434b28" />

<img width="1658" height="1971" alt="v_weapons_orb_panorama" src="https://github.com/user-attachments/assets/c3a05c08-f071-485b-92ff-bd74aa429095" />




Using SIFT:

<img width="5899" height="3404" alt="v_bird_sift_panorama" src="https://github.com/user-attachments/assets/5a1b35d7-ab50-40bf-afc1-d4f8dadf86b5" />

<img width="2438" height="2454" alt="v_circus_sift_panorama" src="https://github.com/user-attachments/assets/83840838-edf7-453f-9112-87a968fcfaeb" />

<img width="1664" height="1983" alt="v_weapons_sift_panorama" src="https://github.com/user-attachments/assets/1c1a3aaf-e548-4ba8-8c2c-f778058885be" />





