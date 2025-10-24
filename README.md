YOLOv8 水下礁石与管道检测项目

![Python 3.8+](https://img.shields.io/badge/python-3.8%2B-blue)
![YOLOv8](https://img.shields.io/badge/framework-YOLOv8-orange)

一、项目核心
基于 YOLOv8 实现水下场景中 **礁石（rock）** 与 **管道（pipe）** 的目标检测，提供训练完成的模型、代码及数据集资源，支持快速复现与推理。

二、核心文件说明
| 目录/文件               | 作用说明                                  |
|-------------------------|-------------------------------------------|
| `weights/best.pt`       | 训练完成的最佳模型，可直接用于推理        |
| `train_code/YOLOv8_underwater_detection.ipynb` | Colab 训练完整代码（含参数调优） |
| `config/underwater.yaml`| 数据集配置文件（指定训练/验证路径与类别） |
| `requirements.txt`      | 项目依赖库清单（一键安装）                |

三、数据集获取
由于数据集文件较大，存储于 Google Drive，点击链接下载并解压：  
[underwater_dataset.zip](https://drive.google.com/file/d/13vxfj91pTnSkRat-5FScnhZNBLRgo5IA/view?usp=drive_link)  
- 包含图像：共 100 张（训练集 80 张/验证集 20 张）  
- 标注格式：YOLO 格式（txt 文件，含目标类别与归一化坐标）  

四、快速使用
1. 安装依赖
```bash
pip install -r requirements.txt
```
 2. 本地推理
```python
from ultralytics import YOLO

# 加载模型
model = YOLO("weights/best.pt")
# 检测单张图像（替换为你的图像路径）
results = model("test.jpg", save=True)
```

五、模型性能
在验证集上的核心指标：
- 整体 mAP@0.5：0.340  
- 礁石检测精确率：0.729 | 召回率：0.241  
- 管道检测精确率：0.731 | 召回率：0.286
- 模型训练版本，存储于 Google Drive，点击链接下载并解压：
  [yolov8_tune_runs](https://drive.google.com/drive/folders/1Ice4UXoIhtHrhN8S19X0hC0HWIe-_iQI?usp=drive_link
)
  
六、联系方式
- GitHub Issues：https://github.com/haodiGeng/yolov8-uw-rp-detection/issues  
