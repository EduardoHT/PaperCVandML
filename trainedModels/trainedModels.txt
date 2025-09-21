### 📦 Trained Models Collection

This repository contains **60 trained models**, organized as follows:

- **5 folds** per configuration  
- **3 YOLO versions:** YOLOv11, YOLOv12, YOLOv13  
- **4 architectural variations:**  
  - Original  
  - C3k2_P2  
  - VoVGSCSP  
  - VoVGSCSP_P2  

🚀 **Key improvement**  
The **VoVGSCSP_P2** architecture achieved consistent gains of **+3.36% to +6.10% mAP50** for distant ship detection, making it the **best-performing design** in this study.

---

### 📂 File Naming Convention

Each trained model is saved as:

Where:
- **ModelVersion** → `YOLOv11`, `YOLOv12`, or `YOLOv13`  
- **Architecture** → `C3k2_P2`, `VoVGSCSP`, `VoVGSCSP_P2`  
- **fold<Number>** → `fold1` … `fold5`  

✅ **Example filenames:**
- `YOLOv11_VoVGSCSP_P2_fold1.pt`  
- `YOLOv12_C3k2_P2_fold3.pt`  
- `YOLOv13_Original_fold5.pt`

### 🚀📦 Download Link

[Click here to access the trained models](https://drive.google.com/drive/folders/1xNG2iGO1K8PUf6pUYZfpqBfRWDbWH4bN?usp=sharing)
