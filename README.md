# CustomSave

一个基于 [ComfyUI](https://github.com/comfyanonymous/ComfyUI) 的 **图片保存节点**（Image Save）。

> **说明：** 本节点由原作者 [WAS Node Suite](https://github.com/WASasquatch/was-node-suite-comfyui) 修改而来，**仅保留 Image Save（图片保存）节点**，移除其余全部节点，保存功能与原版一致。在此向原作者致谢。

---

## 功能

**Image Save** 节点用于将生成的图片保存为文件，支持：

- 自定义输出路径与文件名前缀
- 多种保存格式：`png`、`jpg`、`jpeg`、`gif`、`tiff`、`webp`、`bmp`
- 可调质量 / DPI / 优化选项 / 无损 WebP
- 文件名自动编号（可设补零位数、编号位置）
- 嵌入 Prompt 与 Workflow 元数据
- 历史预览（可显示最近保存的图片）
- 文件名支持文本 Token（时间、主机名、CUDA 设备等）

---

## Image Save 节点参数

| 参数 | 说明 | 默认值 |
| --- | --- | --- |
| `images` | 输入的图片（IMAGE） | — |
| `盘符` | 输出盘符（如 `D:`；留空则按相对路径存到 ComfyUI/output） | `""` |
| `主文件夹` | 输出主文件夹，支持 Token；相对路径基于 ComfyUI/output | `""` |
| `副文件夹` | 输出副文件夹（拼接在主文件夹之后），支持 Token | `[time(%Y-%m-%d)]` |
| `文件名前缀` | 文件名前缀 | `ComfyUI` |
| `文件名后缀` | 文件名后缀（拼接在前缀之后） | `""` |
| `filename_delimiter` | 前缀与编号间的分隔符 | `_` |
| `filename_number_padding` | 编号补零位数（1–9） | `4` |
| `filename_number_start` | 编号放在前缀前 / 后 | `false` |
| `extension` | 保存格式 | `png` |
| `dpi` | DPI（1–2400） | `300` |
| `quality` | 质量（1–100） | `100` |
| `optimize_image` | 是否优化图片 | `true` |
| `lossless_webp` | WebP 无损 | `false` |
| `overwrite_mode` | 覆盖模式：`false` / `prefix_as_filename` | `false` |
| `show_history` | 是否显示历史保存的图片 | `false` |
| `show_history_by_prefix` | 历史预览是否按前缀过滤 | `true` |
| `embed_workflow` | 是否嵌入 Prompt / Workflow 元数据 | `true` |
| `show_previews` | 是否显示预览 | `true` |

**输出：** `images`（原图）、`files`（保存的文件路径列表）

---

## 文件名 Token

在 `主文件夹`、`副文件夹`、`文件名前缀`、`文件名后缀` 中可使用 Token。输出路径 = `盘符` + `主文件夹` + `副文件夹`，文件名前缀 = `文件名前缀` + `文件名后缀`：

| Token | 说明 |
| --- | --- |
| `[time]` | 当前系统微秒时间戳 |
| `[time(格式)]` | 按 Python `datetime` 格式输出的当前时间 |
| `[hostname]` | 运行 ComfyUI 的主机名 |
| `[cuda_device]` | 当前 CUDA 设备 |
| `[cuda_name]` | 当前 CUDA 设备名称 |

示例：`[hostname]_[time]__[time(%Y-%m-%d__%I-%M%p)]`

---

## 安装

1. 将本文件夹放到 ComfyUI 的 `custom_nodes` 目录下：

   ```
   ComfyUI/custom_nodes/ComfyUI-CustomSave/
   ```

2. 重启 ComfyUI 即可加载。

> 依赖仅 `pillow` 和 `numpy`，ComfyUI 自带，无需额外安装。

---

## 来源与致谢（Attribution）

| 项目 | 内容 |
| --- | --- |
| 原项目名称 | WAS Node Suite |
| 原作者 | Jordan Thompson（WASasquatch） |
| 原项目地址 | https://github.com/WASasquatch/was-node-suite-comfyui |
| 原许可证 | MIT License |

---

## 授权（License）

本项目基于 MIT License 发布，详见 [`LICENSE`](./LICENSE)。

由原作者节点修改而来，原版权与许可声明一并保留。
