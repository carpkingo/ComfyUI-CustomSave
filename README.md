# CustomSave

一个基于 [ComfyUI](https://github.com/comfyanonymous/ComfyUI) 的节点套件，涵盖图像处理、文本处理、遮罩处理、采样器、视频等常用节点。

> **说明：** 本节点由原作者 [WAS Node Suite](https://github.com/WASasquatch/was-node-suite-comfyui) 修改而来，仅作本地化改名与适配，功能与原套件保持一致。在此向原作者致谢。

---

## 来源与致谢（Attribution）

| 项目 | 内容 |
| --- | --- |
| 原项目名称 | WAS Node Suite |
| 原作者 | Jordan Thompson（WASasquatch） |
| 原项目地址 | https://github.com/WASasquatch/was-node-suite-comfyui |
| 原许可证 | MIT License |

本套件基于 MIT 协议在原项目基础上修改，保留原版权与许可声明（见 [`LICENSE`](./LICENSE)）。

---

## 功能简介

节点按类别划分，主要包括：

- **图像处理**：裁剪、缩放、旋转、滤镜、模糊、噪点、通道混合、风格化、无缝纹理等
- **图像生成与合成**：网格图、批量合成、马赛克/像素化、渐变、Perlin 噪声等
- **遮罩（Mask）**：遮罩生成、区域裁剪、腐蚀/膨胀、平滑、组合等
- **文本处理**：字符串拼接、查找替换、字典、分词、Token 解析、随机行等
- **采样与模型**：KSampler（WAS）、KSampler Cycle、各类输入开关、Loaders、LoRA 等
- **文件读写**：Image Save、Save Text File、Load Text File、Image Load、视频读写等
- **逻辑与数值**：布尔逻辑、数值运算、常量、随机数、条件判断等
- **附加节点**：BLIP 图像描述、SAM 图像分割、MiDaS 深度估计等

完整节点列表请参考原项目文档：[WAS Node Suite 文档](https://docs.getsalt.ai/md/was-node-suite-comfyui/)。

---

## 安装

1. 将本目录放置到 ComfyUI 的 `custom_nodes` 目录下：

   ```
   ComfyUI/custom_nodes/ComfyUI-CustomSave/
   ```

2. 安装依赖（在套件目录下执行）：

   - **便携版 / venv 环境：**
     ```
     path/to/ComfyUI/python_embeded/python.exe -s -m pip install -r requirements.txt
     ```
   - **系统 Python 环境：**
     ```
     pip install -r requirements.txt
     ```

3. 启动 / 重启 ComfyUI，节点会自动加载。

> 如需自动安装依赖，也可直接运行本目录下的 `install.bat`。

---

## 使用说明

- 节点默认位于 ComfyUI 的对应分类菜单中。
- **Save Image** 支持自定义路径与多种格式（PNG / JPG / WebP 等），并可在文件名中使用文本 Token。
- 部分节点首次运行会尝试自动安装依赖（如 `matplotlib`、`scikit-learn`、`pilgram`），请确保网络可用。

### 文本 Token

可在 **Save Text File**、**Save Image** 等节点中使用 Token 自定义文件名：

| Token | 说明 |
| --- | --- |
| `[time]` | 当前系统微秒时间戳 |
| `[time(格式)]` | 按 Python `datetime` 格式输出的当前时间 |
| `[hostname]` | 运行 ComfyUI 的主机名 |
| `[cuda_device]` | 当前 CUDA 设备 |
| `[cuda_name]` | 当前 CUDA 设备名称 |

示例：`[hostname]_[time]__[time(%Y-%m-%d__%I-%M%p)]`

---

## 配置（was_suite_config.json）

首次运行会在套件目录下生成 `was_suite_config.json`，可配置：

- `webui_styles`：导入 AUTOMATIC1111 WebUI 的 `styles.csv` 样式
- `wildcards_path`：自定义通配符目录
- `ffmpeg_extra_codecs`：视频节点的额外编码格式
- `use_legacy_ascii_text`：是否使用旧版 ASCII 文本输出

修改后需重启 ComfyUI 生效。

---

## 授权（License）

本项目基于 MIT License 发布，详见 [`LICENSE`](./LICENSE)。

由原作者节点修改而来，原版权与许可声明一并保留。
