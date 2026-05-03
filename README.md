# 开普勒系外行星凌星信号检测

本项目使用开普勒太空望远镜公开的光变曲线数据，通过**相位折叠**和 **3-sigma 阈值法**自动检测系外行星的凌星信号,并与假阳性目标对比。

## 最终成果
- [Kepler_analysis.ipynb](https://github.com/user-attachments/files/27311798/Kepler_analysis.ipynb)
- [Kepler_analysis.html](https://github.com/user-attachments/files/27311805/Kepler_analysis.html)
- 真实 VS 假阳性对比图: <img width="1400" height="400" alt="real_vs_false" src="https://github.com/user-attachments/assets/3440e198-28f5-4f48-8448-ce29245fba13" />

## 主要结果
- 相位折叠后, Kepler-10b 在相位 0 附近出现明显的 V 形凹陷。
- 阈值法检测到 **37** 个凌星候选点,召回率 **0.10%**, 误报率 **0.06%**。
- 假阳性目标 KOI-1684.01 无规则凹陷,方法有效。

## 数据来源
NASA Exoplanet Archive - Kepler-10b (真实行星) ，KOI-1684.01 (假阳性）

## 运行方法
1. `pip install -r requirements.txt`
2. `jupyter notebook kepler_analysis.ipynb`

## 文件说明
- `Kepler_analysis.ipynb`: 完整代码 (含注释、图表)
- `Kepler_analysis.html`: 导出的结题报告
- `real_vs_false.png`: 真假信号对比图
- `requirements.txt`: Python 依赖列表

## 作者
@same-929

## 许可证
MIT
