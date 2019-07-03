# 人脸识别中的常见softmax函数
一表流

|Name|Loss公式($g_i$)|权重/特征归一|论文|
|--|--|--|--|
|softmax|$$\frac{1}{N}\sum_i-log\frac{e^{w_{y_i}·x_i}}{\sum_ke^{w_k·x_i}}$$|N/N||
|NormFace|同softmax|Y/Y|[arxiv](https://arxiv.org/abs/1704.06369) ACMMM 2017|
|L softmax|$$\frac{1}{N}\sum_i-log\frac{e^{\|\|w_{y_i}\|\|·\|\|x_i\|\|·cos(m·\theta_{y_i, i})}}{e^{\|\|w_{y_i}\|\|·\|\|x_i\|\|·cos(m·\theta_{y_i, i})} + \sum_{k \neq y_i}e^{\|\|w_k\|\|·\|\|x_i\|\|·cos\theta_{k, i}}}$$ 首次提出angular margin|N/N|[arxiv](https://arxiv.org/abs/1612.02295) ICML 2016|
|A softmax|$$\frac{1}{N}\sum_i-log\frac{e^{\|\|x_i\|\|·cos(m·\theta_{y_i, i})}}{e^{\|\|x_i\|\|·cos(m·\theta_{y_i, i})} + \sum_{k \neq y_i}e^{\|\|x_i\|\|·cos\theta_{k, i}}}$$ 增加weight norm|Y/N|[arxiv](https://arxiv.org/abs/1704.08063) CVPR 2017|
|AM softmax|$$\frac{1}{N}\sum_i-log\frac{e^{s·(cos(\theta_{y_i, i})-m)}}{e^{s·(cos(\theta_{y_i, i})-m)} + \sum_{k \neq y_i}e^{cos\theta_{k, i}}}$$ 增加feat norm和scale，margin由乘法变为加法|Y/Y|[arxiv](https://arxiv.org/abs/1801.05599) ICLRw 2018|
|CosFace|同AM-Softmax，和AM-Softmax接近同时发布|Y/Y|[arxiv](https://arxiv.org/abs/1801.09414) CVPR 2018|
|ArcFace|$$\frac{1}{N}\sum_i-log\frac{e^{s·cos(\theta_{y_i, i}+m)}}{e^{s·cos(\theta_{y_i, i}+m)} + \sum_{k \neq y_i}e^{cos\theta_{k, i}}}$$ 类似AM softmax，将margin由cos外移到内|Y/Y|[arxiv](https://arxiv.org/abs/1801.07698) CVPR 2019|
|Adaptive Face|$$\frac{1}{N}\sum_i-log\frac{e^{s·(cos(\theta_{y_i, i})-m_{y_i})}}{e^{s·(cos(\theta_{y_i, i})-m_{y_i})} + \sum_{k \neq y_i}e^{cos\theta_{k, i}}} - \lambda\frac{1}{K}\sum_km_k$$ 将margin参数化，与类别相关|Y/Y|[pdf](http://openaccess.thecvf.com/content_CVPR_2019/papers/Liu_AdaptiveFace_Adaptive_Margin_and_Sampling_for_Face_Recognition_CVPR_2019_paper.pdf) CVPR 2019|

todo Decision Boundary
