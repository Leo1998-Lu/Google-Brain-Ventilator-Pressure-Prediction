### [Google Brain: Ventilator Pressure Prediction](https://www.kaggle.com/c/jane-street-market-prediction/overview) ###
2021 Kaggle Research Prediction Competition: Google Brain - Ventilator Pressure Prediction(Final ***Rank 206/2605*** teams)

![image](https://user-images.githubusercontent.com/57436423/142562333-cd20bd05-ef98-4454-9d97-62badf8eb0fe.png)

### Solution: FE+LSTM ###
- 比赛类型：结构化数据、时间序列比赛
- 竞赛任务：模拟连接到患者肺部的呼吸机，对呼吸机的气压进行预测
- 特征构造：   
1．	相关特征历史滑窗及统计量 shift()    
2．	时序累计值 cumsum()    
3．	时序滞后差值 diff()   
4．	关键特征时序 Kmeans聚类   
- 评价指标：**|X-Y|**  
- 模型：**深层LSTM** 

![image](https://user-images.githubusercontent.com/57436423/142562824-88341fc9-6db3-471c-8a00-16b07059b95f.png)


本次比赛中提供了**千万级别**的呼吸机生成的时序数据，每个时间序列代表大约 3 秒的呼吸，并给出了两个控制信号、产生的气道压力和肺的相关属性，要求预测呼吸过程中回路的气道压力。

- 上分Trick:  
1.**随机权重Blending**: 根据线上LB得分进行随机加权融合，LB得分越高相应随机权重选择的阈值范围越大。   
2.**K近邻气压值拟合**：将模型预测值与训练集中出现过相应最接近的数值进行替换，达到模拟呼吸机的特性目的。   

#### Final Rank: 173/4245 ####
使用深层LSTM结构结合时序特征（滑窗、滞后、累积统计量等）对呼吸器压力进行预测，并使用随机权重Blending和K近邻数值拟合等Trick带队SOLO取得铜牌。
![image](https://user-images.githubusercontent.com/57436423/142563642-ab375d49-708e-406b-9380-e4da3d7ef85d.png)

