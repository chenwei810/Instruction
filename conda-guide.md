# Conda 與 CUDA 完整使用指南

## 目錄
- [基礎知識](#基礎知識)
- [Conda 安裝與設定](#conda-安裝與設定)
- [基本操作](#基本操作)
- [環境管理](#環境管理)
- [套件管理](#套件管理)
- [CUDA 安裝指南](#cuda-安裝指南)
- [疑難排解](#疑難排解)
- [最佳實踐](#最佳實踐)

## 基礎知識

### 什麼是 Conda？
Conda 是一個開源的套件管理系統和環境管理系統，主要用於：
1. 安裝各種程式套件
2. 執行套件更新
3. 建立獨立的開發環境
4. 在不同環境之間切換

### Conda 的優點
- **跨平台**：支援 Windows、macOS 和 Linux
- **環境隔離**：避免不同專案之間的套件衝突
- **多語言支援**：支援 Python、R、Ruby、Lua、Scala 等
- **整合性高**：可同時管理多個版本的 Python 和相關套件

## Conda 安裝與設定

### 選擇版本
1. **Anaconda**（推薦新手）
   - 完整版本，包含常用科學計算套件
   - 佔用空間約 3GB

2. **Miniconda**（推薦進階使用者）
   - 最小安裝版本
   - 只包含 Conda 和 Python
   - 佔用空間小

### 安裝步驟
1. 下載安裝檔
   - Anaconda: https://www.anaconda.com/products/distribution
   - Miniconda: https://docs.conda.io/en/latest/miniconda.html

2. 執行安裝
   ```bash
   # 驗證安裝
   conda --version
   ```

## 基本操作

### 環境管理基礎指令
```bash
# 建立新環境
conda create --name myenv python=3.8

# 啟動環境
conda activate myenv

# 關閉環境
conda deactivate

# 列出所有環境
conda env list
```

### 套件管理基礎指令
```bash
# 安裝套件
conda install numpy

# 安裝特定版本
conda install numpy=1.19.2

# 更新套件
conda update numpy

# 移除套件
conda remove numpy
```

## CUDA 安裝指南

### 前置檢查
```bash
# 檢查 NVIDIA 顯示卡
nvidia-smi
```

### 安裝步驟

1. **建立 CUDA 環境**
   ```bash
   # 建立新環境
   conda create -n cuda_env python=3.8
   conda activate cuda_env
   ```

2. **安裝 CUDA 工具**
   ```bash
   # 安裝 CUDA toolkit
   conda install cudatoolkit

   # 安裝 cuDNN
   conda install cudnn
   ```

3. **安裝深度學習框架**
   ```bash
   # PyTorch
   conda install pytorch torchvision torchaudio cudatoolkit -c pytorch

   # 或 TensorFlow
   conda install tensorflow-gpu
   ```

### 驗證安裝
```python
import torch
print(f"CUDA 是否可用: {torch.cuda.is_available()}")
print(f"CUDA 版本: {torch.version.cuda}")
```

## 疑難排解

### Conda 常見問題
```bash
# 環境啟動失敗
conda env remove --name myenv
conda env create -f environment.yml

# 套件衝突
conda install --no-deps package_name

# 清理快取
conda clean --all
```

### CUDA 常見問題
1. CUDA 不可用
   ```bash
   # 重新安裝 CUDA toolkit
   conda uninstall cudatoolkit
   conda install cudatoolkit
   ```

2. 版本衝突
   ```bash
   # 重建環境
   conda deactivate
   conda env remove -n cuda_env
   conda create -n cuda_env python=3.8
   ```

## 最佳實踐

### 環境管理
1. 每個專案使用獨立環境
2. 避免在 base 環境安裝太多套件
3. 使用有意義的環境名稱

### 套件管理
1. 固定重要套件的版本
2. 定期更新環境設定檔
3. 優先使用官方頻道

### CUDA 相關
1. 確保驅動程式版本相容
2. 選擇穩定版本的 CUDA
3. 定期更新驅動程式

### 環境設定檔案範例
```yaml
name: cuda_env
channels:
  - pytorch
  - conda-forge
  - defaults
dependencies:
  - python=3.8
  - cudatoolkit
  - pytorch
  - torchvision
  - torchaudio
  - cudnn
```

## 實用資源
- [Conda 官方文件](https://docs.conda.io/)
- [NVIDIA CUDA 文件](https://docs.nvidia.com/cuda/)
- [PyTorch 安裝指南](https://pytorch.org/get-started/locally/)

## 注意事項
1. 定期更新 Conda 和相關套件
2. 保持環境的整潔和獨立
3. 注意 CUDA 版本相容性
4. 定期備份環境設定檔

---

這份指南整合了 Conda 的基本使用方法和 CUDA 的安裝步驟。建議根據需求逐步學習和實踐。如有問題，請參考相關章節的疑難排解部分。
