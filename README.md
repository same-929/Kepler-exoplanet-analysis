# 开普勒系外行星凌星信号检测

本项目使用开普勒太空望远镜公开的光变曲线数据，通过**相位折叠**和 **3-sigma 阈值法**自动检测系外行星的凌星信号,并与**机器学习方法** (随机森林) 进行对比。

## 最终成果
-[Kepler_analysis.ipynb](https://github.com/user-attachments/files/27438832/Kepler_analysis.ipynb)
-[Kepler_analysis.html](https://github.com/user-attachments/files/27438835/Kepler_analysis.html)
- 真实行星 (Kepler-10b) VS 假阳性 (KOI-1684.01) 对比图: <img width="1400" height="400" alt="real_vs_false" src="https://github.com/user-attachments/assets/3440e198-28f5-4f48-8448-ce29245fba13" />

## 主要结果

### 1. 阈值法 (3-sigma,基于光变曲线)
- 相位折叠后, Kepler-10b 在相位 0 附近出现明显的 V 形凹陷。
- 检测到凌星候选点数量: **37** 个
- 召回率: **0.10%**
- 误报率: **0.06%**
- 假阳性目标 KOI-1684.01 无规则凹陷,方法有效。

### 2. 机器学习 (随机森林,基于 KOI 表)
使用 NASA 公开的 KOI 表,选择周期 (`koi_period`) 、半径 (`koi_prad`) 、恒星温度 (`koi_steff`) 、信噪比 (`koi_model_snr`) 四个特征,训练随机森林分类器区分真实行星与假阳性。

**测试集表现**:
- 准确率: **88.60%**
- 召回率: **84.31%**
- 精确率: **81.47%**
- AUC: **94.50%**
- 误判的假阳性样本主要集中在周期、半径、信噪比等特征与真实行星重叠的区域,后续可通过增加凌星时长、深度等特征进一步优化模型。

**特征重要性**: `koi_prad` (行星半径) 和 `koi_model_snr` (信噪比) 贡献最大。

### 3. 方法对比
- **阈值法**: 无需训练,可解释性强,适合单目标快速筛选,但对浅凌星不敏感。
- **机器学习**: 能综合多特征,召回率和精确率更高,但需要大量标注数据。
  
## 数据来源
NASA Exoplanet Archive - Kepler-10b (真实行星) ，KOI-1684.01 (假阳性）

## 运行环境
- Python 3.9+
- 依赖库见 `requirements.txt`
  
## 运行方法
1. `pip install -r requirements.txt`
2. `jupyter notebook kepler_analysis.ipynb`

## 文件说明
- `Kepler_analysis.ipynb`: 完整代码 (含注释、图表)
- `Kepler_analysis.html`: 导出的结题报告
- `real_vs_false.png`: 真假信号对比图
- `requirements.txt`: Python 依赖列表

## 结果示例
<img width="1000" height="400" alt="transit_detection" src="https://github.com/user-attachments/assets/d8e7f34d-056b-4177-b96c-a06b55bc6419" />
<img width="1000" height="400" alt="folded_lightcurve" src="https://github.com/user-attachments/assets/c92ca965-a998-4a2c-90c9-34d07b8c0231" />

## 作者
@same-929

## 许可证
MIT
