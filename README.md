# YOLO目标检测系统

基于YOLOv8的目标检测系统，支持图片、视频和摄像头检测，以及模型转换功能。

## 功能特性

### 🎯 检测功能
- **图片检测**: 支持JPG、PNG、BMP等格式
- **视频检测**: 支持MP4、AVI、MOV等格式，带播放控制
- **摄像头检测**: 实时摄像头检测
- **多任务支持**: 目标检测、实例分割、姿态估计、图像分类、定向边框检测

### 🎨 可视化功能
- **智能结果展示**: 检测框、标签、置信度显示
- **固定颜色分配**: 同类别对象使用一致颜色，避免闪烁
- **实时数据表**: 详细的检测参数和统计信息
- **多种显示选项**: 可控制边界框、标签、掩码、关键点显示
- **实时刷新**: 显示选项修改后立即更新检测结果，无需重新检测，数据表保持不变

### 🔄 模型转换功能
- **精选格式支持**: ONNX、OpenVINO、NCNN三种主流格式
- **参数配置**: 图像尺寸、量化选项、批处理大小等
- **实时进度**: 转换过程的实时进度显示和日志记录
- **格式推荐**: 根据部署场景智能推荐最适合的格式
- **转换验证**: 详细的转换信息和结果验证

### 📊 数据管理
- **数据导出**: 检测结果导出为CSV格式
- **参数调节**: 置信度、IoU阈值等参数设置
- **任务类型自动识别**: 基于模型结构智能识别任务类型

## 环境要求

- Python 3.8+
- Windows/Linux/macOS

## 安装部署
```bash
# 安装所有依赖（包括模型转换功能）
pip install -r requirements.txt

# 注意：requirements.txt包含精确版本号，确保环境一致性
# 支持的转换格式：ONNX、OpenVINO、NCNN
```



## 使用说明

### 基本操作流程

#### 🎯 目标检测
1. **加载模型**: 点击"加载模型"按钮，选择YOLO模型文件（.pt或.onnx格式）
2. **调整参数**: 在左侧参数面板设置置信度阈值、IoU阈值等
3. **选择检测类型**:
   - 图片检测: 点击"检测图片"，选择图片文件
   - 视频检测: 点击"检测视频"，选择视频文件
   - 摄像头检测: 点击"摄像头检测"开始实时检测
4. **查看结果**: 在右侧区域查看检测结果和数据统计
5. **调整显示**: 检测完成后，可在参数面板中修改显示选项（显示标签、置信度、边界框等），检测结果会立即更新，数据表保持不变

#### 🔄 模型转换
1. **打开转换器**: 菜单栏 → 模型 → 模型转换（或按Ctrl+M），或点击"模型转换"标签页
2. **选择模型**: 点击"浏览"选择要转换的.pt模型文件，然后点击"加载模型"
3. **选择格式**: 从下拉菜单中选择目标转换格式（ONNX、OpenVINO、NCNN）
4. **配置参数**: 设置图像尺寸、量化选项、批处理大小等转换参数
5. **开始转换**: 点击"开始转换"按钮，观察实时进度和日志
6. **验证结果**: 转换完成后可选择打开输出目录查看生成的模型文件

### 界面说明

- **左侧面板**: 模型设置、参数调节、检测控制
- **右侧主区域**:
  - 检测结果标签页: 显示检测结果和播放控制
  - 实时数据表标签页: 详细的检测数据统计
  - 系统信息标签页: 系统状态和设备信息
  - 模型转换标签页: 模型格式转换功能

## 项目结构

```
yolo-detection-system/
├── main.py                    # 主程序入口
├── config.py                  # 配置文件
├── requirements.txt           # 依赖包列表
├── install_converter_deps.py  # 模型转换依赖安装脚本
├── README.md                  # 项目文档
├── core/                      # 核心模块
│   ├── detector.py            # YOLO检测器
│   ├── model_converter.py     # 模型转换器
│   └── utils.py               # 工具函数
├── ui/                        # 用户界面
    ├── main_window.py         # 主窗口
    └── widgets/               # 界面组件
        ├── image_viewer.py    # 图片查看器
        ├── video_player.py    # 视频播放器
        ├── detection_table.py # 检测数据表
        ├── parameter_panel.py # 参数面板
        ├── converter_widget.py    # 模型转换器界面
        └── smart_detection_viewer.py # 智能检测查看器

```

## 支持格式

### 模型文件
- **PyTorch模型**: .pt
- **ONNX模型**: .onnx

### 转换格式
- **ONNX**: 跨平台推理格式，支持多种推理引擎
- **OpenVINO**: Intel硬件优化格式，支持CPU/GPU/VPU推理
- **NCNN**: 移动端优化推理框架，支持ARM/x86平台

### 任务类型
- **🎯 目标检测**: yolov8n.pt, yolov8s.pt, yolov8m.pt, yolov8l.pt, yolov8x.pt
- **🎭 实例分割**: yolov8n-seg.pt, yolov8s-seg.pt, yolov8m-seg.pt
- **🤸 姿态估计**: yolov8n-pose.pt, yolov8s-pose.pt, yolov8m-pose.pt
- **🏷️ 图像分类**: yolov8n-cls.pt, yolov8s-cls.pt, yolov8m-cls.pt
- **📐 定向边框**: yolov8n-obb.pt, yolov8s-obb.pt, yolov8m-obb.pt

### 媒体文件
- **图片**: .jpg, .jpeg, .png, .bmp, .tiff
- **视频**: .mp4, .avi, .mov, .mkv

## 常见问题

### 基础问题
**Q: 程序启动失败，提示模块缺失**
A: 重新安装依赖包 `pip install -r requirements.txt`

**Q: 模型加载失败**
A: 检查模型文件格式（.pt或.onnx），确保路径中不包含中文字符

**Q: 摄像头无法打开**
A: 检查摄像头是否被其他程序占用，尝试更换摄像头索引

**Q: 检测速度慢**
A: 使用较小的模型（如yolov8n.pt），启用GPU加速

### 模型转换问题
**Q: 模型转换功能无法使用**
A: 确保已安装ultralytics库，版本8.0.0以上

**Q: OpenVINO转换失败**
A: 确保已正确安装OpenVINO，检查系统兼容性

**Q: NCNN转换速度慢**
A: NCNN转换需要较长时间，请耐心等待

**Q: 转换过程中出现内存不足错误**
A: 减小batch_size参数，或使用更小的模型进行转换

**Q: 转换后的模型精度下降**
A: 避免同时启用INT8和FP16量化，检查量化参数设置

**Q: 转换后的模型文件很大**
A: 启用模型简化选项，或使用量化参数减小模型大小

## 许可证

MIT License
