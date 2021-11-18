# InformationSteganography-seu
东南大学网安学院信息隐藏(2021)第一分组大作业


## 题目要求
> 任务是实现对320*240的灰度图像(样本就用lena图像)进行信息隐藏设计,隐藏信息为“东南大学网络空间安全学院2021”，应用空间与非lsb信息隐藏方法进行实验并测试。对上述技术和方法进行实验、结果分析等，特别是对其的健壮性（抗攻击）进行分析

## 实现方法

这里采用的是GEMD(Generalised exploiting modification direction)信息隐藏算法，是一种大容量空域信息嵌入算法

1. 将载体图像进行分组，使每组包含 n 个可以调整的载体像素（g1，g2,...gn）,分别计算函数值 f； 
2. 从秘密数据 M 中截取（n+1）位的秘密数据，并将其转换成十进制格式； 
3. 计算差值 d： 
 
4. 若 d=0，则 x=1；若 d=2^n，则 x=2；若 0＜d＜2n，则 x=3,；若 d≥2^n，则 x=4；
5. 由x的取值决定对像素组的操作，基本上是灰度的加一减一

这里取N=3,这样嵌入的数据量一次就是4bit,恰好是半个字节，一个16进制位


## 文件说明
```
│  d2x.m  d转换为x(d,x含义具体见文献三)
│  imgAttack.m 检测伪装图像健壮性
│  LICENSE
│  pixelChange.m 转换像素组
│  README.md
│  Steganography.m 隐写及解隐文件(主)
│  tree.txt 文件树
│  
└─IMG
        lenna.bmp   载体图像
        lenna_h.bmp     伪装图像
```


## 参考文献

1. [Efficient Steganographic Embedding by Exploiting Modification Direction](https://ieeexplore.ieee.org/abstract/document/4020540)

2. [Data hiding based on generalised exploiting modification direction method](https://www.tandfonline.com/doi/full/10.1179/1743131X12Y.0000000011)

3. [基于GEMD的图像隐写算法效率研究](https://kns.cnki.net/kcms/detail/detail.aspx?dbcode=CMFD&dbname=CMFD202101&filename=1020306468.nh&uniplatform=NZKPT&v=yiRe1exwlgASAvQhT6RXK8I4_qVDO7eSjyPqEKZHEPPyUzq8eqJ7nQxpVdy6fXW_)
