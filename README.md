# Paper: Computer Vision and Machine Learning Approach for Correlating Optical Coordinates with AIS Data in Maritime Surveillance

- AISdata: Data transmitted by vessels synchronized with the video.

- Dataset: Dataset used for model training and validation.

- Video: Demonstration video of the complete visual monitoring system, considering the YOLOv11-VoVGSCSP-P2 model and the training model for large images.

The video illustrates the simulation of the system proposed in the letter “Computer Vision and Machine Learning Approach for Correlating Optical Coordinates with AIS Data in Maritime Surveillance”, which employs the YOLOv11/12/13-VoVGSCSP-P2 model for accurate detection of small vessels in optical imagery. In each frame, ships are identified and their positions displayed in real time, along with the total object count. The interface simulates an automated maritime surveillance environment, including zoom-ins on selected vessels where a secondary model is applied to high-resolution imagery for improved robustness. Additionally, the system integrates a coordinate transformation strategy for mapping detections to sea-plane projections and supports the detection of AIS spoofing and going dark activities.

Link: https://drive.google.com/drive/folders/1fqvkSqTJTW4L7IVmuhc1ZNElBs_SGGny?usp=sharing

---

### 📊 Coordinate Transformation with Machine Learning Ensembles

As an alternative to homography, we implemented an **ensemble of machine learning regressors** for coordinate conversion.  
These ensembles were trained and validated on datasets with **100, 1,000, 10,000, and 100,000 point pairs**.  
As expected, performance improved as the number of points increased, mainly due to the models’ ability to capture nonlinear spatial relationships.

Among the tested algorithms, **ExtraTreesMSE** and **RandomForestMSE** achieved the best individual results.  
They were combined into **weighted ensembles** with independently optimized weights for the **X** and **Y** outputs, minimizing prediction error.

#### 📑 Results by number of points
| Points   | MAE X  | MAE Y  |
|----------|--------|--------|
| 100      | 299.54 | 141.56 |
| 1,000    | 4.83   | 4.87   |
| 10,000   | 1.71   | 1.12   |
| 100,000  | 0.11   | 0.25   |

#### 🏆 Best-performing ensemble (100k points)
The optimal ensemble used weights of **0.8095 (ExtraTreesMSE)** and **0.1905 (RandomForestMSE)** for **X**, and **0.5238** and **0.4762** for **Y**.  
This configuration minimized both MAE and MSE across axes:

| Model              | MAE X | MAE Y | MSE X  | MSE Y   |
|--------------------|-------|-------|--------|---------|
| **WeightedEnsembleL2** | 0.11  | 0.25  | 1.42   | 7.19    |
| ExtraTreesMSE      | 0.12  | 0.26  | 1.36   | 8.50    |
| RandomForestMSE    | 0.17  | 0.27  | 4.60   | 7.31    |
| LightGBMLarge      | 0.61  | 2.27  | 39.11  | 608.08  |
| LightGBM           | 0.62  | 2.36  | 42.67  | 427.13  |
| KNeighborsDist     | 1.56  | 6.41  | 403.52 | 5112.58 |
| XGBoost            | 1.53  | 4.53  | 486.32 | 2768.28 |
| KNeighborsUnif     | 1.87  | 7.61  | 542.82 | 6511.76 |
| CatBoost           | 1.70  | 4.94  | 313.94 | 2480.61 |
| LightGBMXT         | 2.86  | 8.55  | 130.18 | 1457.68 |
| NeuralNetTorch     | 2.99  | 7.15  | 423.57 | 874.85  |
| NeuralNetFastAI    | 12.63 | 36.38 | 3657.66| 30861.42 |

These results confirm that **ensemble learning** offers a robust solution for coordinate mapping, outperforming traditional homography and most individual regressors.

---
