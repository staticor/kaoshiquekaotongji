# kaoshiquekaotongji
# 基于2019年二建考试缺考数据验证考室超排的想法

>文章里面有数学公式老师查看时建议添加chrome插件 [MathJax Plugin for Github
](https://github.com/orsharir/github-mathjax 'mathjax')

## 前言

近年来参加各项人事考试的考生人数逐年增加，考试组织工作的痛点也逐渐凸显出来，这个痛点就是考点的稀缺。能够满足我们要求的考点，首先要容量大，最好能够提供100间以上的考室；其二参与组织的工作人员要有能够管控整个考点各项事务的能力；其三考点的监考人员有好奇心且认真负责。随着近年来社会整体物价水平的上涨，为了保留住这样的考点我们已经将费用从每间教室`400元/2个小时`上涨到了`600元/2个小时`，已经接近了财政给我们的`700元/2个小时`每间教室的上限。为了降低考场租凭费用，我想从考生的缺考率入手，通过对准考证号进行超排来降低考室的缺考率，以达到减少考室降低考场租凭费用的目的。

下面我将分为三个部分来完成：
1. 首先清理成绩数据得出某一科考试某个考区的考生缺考率；
2. 再分析该考区教室里缺考考生的分布情况，
3. 最后根据数据推算出考生超排后的情况

> 准考证号超排：目前按照部考试中心的要求,考生的准考证号是由考试科目编号、省编号、考区编号、考点编号、考室编号和考生座位号组成的，如：`151232300101`就为考试科目`1`是`51`省`23`市`23`考点`001`考室`01`座位,其中考生的座位号的上限是`30`;准考证号超排就是指将一个考室30个座位号的上限提高到30个以上。

### （一）确定筛选出的考区

首先我对整体的成绩数据做了清理，并确定以`《建设工程法规及相关知识》`这一科考试的`公路工程`专业求出了各个考区的缺考率，如下所示：

#### 《建设工程法规及相关知识》（科目一）

##### 专业：公路工程

| 考区 | 参考人数 | 缺考人数 | 缺考率 |
| :-: | :-: | :-: | :-: | 
| 乐山 | 742    | 205   | 0.276280 |
| 内江 | 448 | 119 | 0.265625 |
| 凉山 | 883 | 213 | 0.241223 |
| 南充 | 1133  | 286 | 0.252427|
| 宜宾 | 1219 | 271 | 0.222313|
| 巴中 |  803 | 145 | 0.180573|
| 广元 | 710 | 147 | 0.207042|
| 广安 | 908 | 216 | 0.237885|
| 德阳 | 1056 | 303 | 0.286932|
| 成都 | 11535 | 3562 |0.308799|
| 攀枝花 | 392 | 94 | 0.239796|
| 泸州 | 1158 | 264 | 0.227979|
| 甘孜 | 106 | 32 | 0.301887|
| 直属考区 | 14756 | 4625 | 0.313432|
| 眉山 | 554 | 133 | 0.240072|
| 绵阳 | 2274 | 544 | 0.239226|
| 自贡 | 476 | 135 | 0.283613|
| 资阳 |327| 91 | 0.278287|
| 达州 | 777| 189 | 0.243243|
|遂宁 | 605|167 | 0.276033|
|阿坝州|  74 |   29 | 0.391892|
|雅安   | 296  |  65 | 0.219595|


![公路工程专业科目1缺考统计](https://raw.githubusercontent.com/mousestone/kaoshiquekaotongji/master/%E5%85%AC%E8%B7%AF%E5%B7%A5%E7%A8%8B%E4%B8%93%E4%B8%9A%E7%A7%91%E7%9B%AE1%E7%BC%BA%E8%80%83%E7%BB%9F%E8%AE%A1.png)

其中我选取了参考人数最多的`直属考区`来作为分析的总体样本。

### （二）确定教室里缺考考生的分布情况

我依照准考证号的编排规则，准考证号的倒数3-5位为考生所在的考室号，重新对数据进行了分组，并对同一教室内缺考考生的数量做了统计，数据中共有562间考室，缺考的情况为不缺考、缺考1个人、缺考2个人、···、全部缺考，统计图如下：


![公路专业科目1缺考教室数统计](https://raw.githubusercontent.com/mousestone/kaoshiquekaotongji/master/%E5%85%AC%E8%B7%AF%E4%B8%93%E4%B8%9A%E7%A7%91%E7%9B%AE1%E7%BC%BA%E8%80%83%E6%95%99%E5%AE%A4%E6%95%B0%E7%BB%9F%E8%AE%A1.png)

通过以上数据可以看出，一间教室里的缺考人数情况，教室最多缺考19人，最少是没缺考；其中出现有10人缺考的情况最多，因此定义：

$$F_n(n:0-20)$$ 

为此次考试中教室有缺考n个人的数量，

$User_n(n:0-20)$

为此次考试教室中出现缺考的人数，计算出均值和方差：

$\mu$ = $\sum_{n=0}^{20}\qquad$($F_n$ * $User_n$)$/$$\sum_{n=0}^{20}\qquad$($F_n$)

$\mu$ = $8.275800711743772$

$std$ $\approx$ $3$ 
对于考室出现n个人缺考的概率为：

$P_n$ $=$ $F_n$ $/$ $\sum_{n=0}^{20}\qquad$$($$F_n$$)$ 

![公路专业科目1缺考概率统计](https://raw.githubusercontent.com/mousestone/kaoshiquekaotongji/master/%E5%85%AC%E8%B7%AF%E4%B8%93%E4%B8%9A%E7%A7%91%E7%9B%AE1%E7%BC%BA%E8%80%83%E6%A6%82%E7%8E%87%E7%BB%9F%E8%AE%A1.png)

#### （三）测试超排

根据上述得出的均值为$\mu = 8.2758$ 方差为$std \approx 3$,我按照均值和均值的向上、下一个标准差取值得到3个测试数据`5`、`8`、`11`，作为准考证号超排的个数进行测试，测试出超排后的缺考人数。


#### 测试1:
测试用例： 保持现有数据，将35人为一个教室，组成一间教室，来测试最后出现缺考人数为负的现象发生。

测试结果：原数据总缺考人数为`4625`,超排`5`人后会,实际缺考为`1815`人，大约可以节约出$（4625-1815）/ 30 \approx 93$间考室。
![公路专业科目1超排5人后的统计](https://raw.githubusercontent.com/mousestone/kaoshiquekaotongji/master/%E5%85%AC%E8%B7%AF%E4%B8%93%E4%B8%9A%E7%A7%91%E7%9B%AE1%E8%B6%85%E6%8E%925%E4%BA%BA%E5%90%8E%E7%9A%84%E7%BB%9F%E8%AE%A1.png)


#### 测试2:
测试用例： 保持现有数据，将38人为一个教室，组成一间教室，来测试最后出现缺考人数为负的现象发生。

测试结果：原总缺考人数`4625`,超排`8`人后会出现缺考`207`人，大约可以节约出$(4625-207)/30 \approx 147$间考室。

![公路专业科目1超排8人后的统计](https://raw.githubusercontent.com/mousestone/kaoshiquekaotongji/master/%E5%85%AC%E8%B7%AF%E4%B8%93%E4%B8%9A%E7%A7%91%E7%9B%AE1%E8%B6%85%E6%8E%928%E4%BA%BA%E5%90%8E%E7%9A%84%E7%BB%9F%E8%AE%A1.png)

#### 测试3:

测试用例：保持现有数据，将41人为一个教室，组成一间教室，来测试最后出现缺考人数为负的现象发生。

测试结果：原总缺考人数`4625`,超排`11`人后会出现缺考`-1401`人，那么现在就还差了约47间考室。
![公路专业科目1超排11人后的统计](https://raw.githubusercontent.com/mousestone/kaoshiquekaotongji/master/%E5%85%AC%E8%B7%AF%E4%B8%93%E4%B8%9A%E7%A7%91%E7%9B%AE1%E8%B6%85%E6%8E%9211%E4%BA%BA%E5%90%8E%E7%9A%84%E7%BB%9F%E8%AE%A1.png)



#### 测试结果和不足
结论：

通过这个三项测试可以看出，基于测试一、二是可以通过超排准考证号来实现减少考室数，从而节省考场租凭费用的想法是可行的。

不足：

目前这个数据只是一年的数据，应该将这一年的数据当作样本，同时多使用几年的数据来推测整体数据。


#### 自己觉得不确定的地方，希望得到金老师的提示：

1. 首先此次数据分析得出的均值为8.27和标准差为3，整个推理的过程是不是合理的？
2. 我不知道可以用什么方法或者工具来验证我的结论？
3. 如果问题1的推理是正确的，那么我想应用这个结果，来推测下一次考试的时候同样的考区同样的考点可能出现异常情况的概率，比如说用z分布求出小于均值的一个标准差出现的概率和小于均值的两个标准差出现的概率，然后用这两个概率直接乘以拟定的缺考人数，得到期望的缺考人数后我就可以根据这个数据来计算我需要备用的考场数量了；这样的想法合理吗？

