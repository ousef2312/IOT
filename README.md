# 🔧 IoT Predictive Maintenance — Industrial Fault Detector

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange?logo=scikit-learn)](https://scikit-learn.org)
[![Accuracy](https://img.shields.io/badge/Accuracy-95.86%25-brightgreen)]()
[![Dataset](https://img.shields.io/badge/Dataset-AI4I%202020-lightgrey)](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset)

> **Detects machine failures in industrial IoT systems before they happen —
> 95.86% accuracy, 89% fault recall on 10,000 real sensor readings.**

---

## 🎯 Problem

Unplanned machine downtime in factories costs thousands of dollars per hour.
This model reads live IoT sensor data (temperature, torque, RPM, tool wear)
and flags machines at risk of failure **before** they break down.

---

## 📊 Results

| Metric        | Score  |
|---------------|--------|
| Accuracy      | 95.86% |
| Fault Recall  | 89%    |
| Faults Caught | 47/53  |
| Faults Missed | 6/53   |

---

## 🗂️ Dataset

- **Source:** AI4I 2020 Predictive Maintenance — UCI ML Repository
- **Size:** 10,000 sensor readings
- **Fault rate:** 3.4% (severe class imbalance → solved with SMOTE)

| Feature             | Unit | Role         |
|---------------------|------|--------------|
| Air Temperature     | K    | Sensor input |
| Process Temperature | K    | Sensor input |
| Rotational Speed    | RPM  | Sensor input |
| Torque              | Nm   | Sensor input |
| Tool Wear           | min  | Sensor input |
| Machine Failure     | 0/1  | **Target**   |

---

## ⚙️ How It Works

```
Raw IoT Data → Outlier Removal (IQR) → Feature Engineering
→ SMOTE Balancing → Random Forest (100 trees) → Predict Fault
```

**Key engineering decisions:**
- Removed 465 outliers using IQR method (9,535 clean rows remain)
- Engineered `Power = Torque × RPM` — captures machine overload
- Used **SMOTE** to balance 210 faults → 7,418 (50/50 split)
- `StandardScaler` to prevent large-value features from dominating

---

## 🏆 Feature Importance

| Rank | Feature       | Importance |
|------|---------------|------------|
| 1    | Tool Wear     | 0.239      |
| 2    | Rot. Speed    | 0.221      |
| 3    | Torque        | 0.185      |
| 4    | Power (new)   | 0.166      |
| 5    | Air Temp      | 0.090      |

---

## 🚀 How to Run

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/iot-fault-detector.git
cd iot-fault-detector

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the notebook
jupyter notebook IoT_Predictive_Maintenance.ipynb
```

**Requirements:** `scikit-learn`, `pandas`, `numpy`, `imbalanced-learn`, `matplotlib`, `seaborn`

---

## 💡 Real-World Impact

- 🏭 **Continuous monitoring** — sensor data read every second
- 🚨 **Early alerts** — maintenance team notified before breakdown
- 💰 **50% downtime reduction** — industry benchmark for predictive maintenance
- 📅 **Smart scheduling** — service machines only when sensors say so

---

## 🛠️ Tech Stack

`Python` · `scikit-learn` · `Random Forest` · `SMOTE` · `Pandas` · `Matplotlib` · `Jupyter`

---

*Built as part of CAI4702 — IoT & AI Integration | Arab Academy for Science, Technology and Maritime Transport*
