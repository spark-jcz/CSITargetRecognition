# CSITargetRecognition

小车目标识别模型（YOLO-FastestV2），ONNX 格式导出。

## 模型说明

| 模型文件 | 说明 |
|---|---|
| `yolo-fastestv2-224-20261028-mosaic-dataset20260913.onnx` | 当前可用模型，输入 224×224 |
| `old/` | 历史版本模型（mobilenetv2_ssd、yolov5n 等） |

## 模型结构

- 输入：`input` `[1, 3, 224, 224]` float
- 输出1：`[1, 14, 14, 17]`（stride 16 检测尺度）
- 输出2：`[1, 7, 7, 17]`（stride 32 检测尺度）
- 输出通道 17 = 3 框 × 4 坐标(x,y,w,h) + 3 objectness + 2 类别

## 类别

| 索引 | 名称 | 说明 |
|---|---|---|
| 0 | target | 目标小车 |
| 1 | distractor | 干扰物 |

## 部署

目标平台：ST STM32MP257（MYiR myb-stm32mp257x），aarch64。
运行时：onnxruntime 1.19.2（含 VSINPU NPU 后端、XNNPACK、CPU）。

## 测试图

- `jpg/7.jpg`：推理测试样例图
