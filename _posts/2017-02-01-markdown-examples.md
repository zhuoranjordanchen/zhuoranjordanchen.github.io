---
title:  "DID顶刊(Management Science)论文复现---消费券刺激政策的效果"
layout: post
---

> **作者：陈卓然(中山大学)**
> **邮箱：chenzhr25@mail2.sysu.edu.cn**

> **文献来源**：Qiao Liu, Qiaowei Shen, Zhenghua Li, Shu Chen (2021) Stimulating Consumption at Low Budget: Evidence from a Large-Scale Policy Experiment Amid the COVID-19 Pandemic. *Management Science* 67(12):7291-7307. https://doi.org/10.1287/mnsc.2021.4119

[toc]

## 论文发现

本文通过DID的方法探究数字消费券对刺激消费产生的作用，文章发现 RMB 1的政府补贴能够促进RMB 3.4到5.8的超额消费，并且这一影响在多轮的消费券派发的过程中一直持续。

## 政策背景

文章选择的政策实施地为浙江省的省会杭州，杭州是全国第一批实施数字消费券的城市之一。

在2020年3月26日，杭州市政府宣布将要在3月27日到4月30日分三轮发放价值5亿元的数字消费券，所有杭州的居民均有资格领取，每个人每一轮只能领取一次。

第一轮价值200万元的数字优惠券大礼包在3月27日8:00 发放，每一个优惠券大礼包中包括五张单独的“花四十减十元”的代金券券，其有效期是从3月27日到4月2日，每一个优惠券大礼包中政府补贴50元，优惠券可以用于杭州几乎全部的实体商家。

第二轮优惠券大礼包是在4月3日10:00中发放，总价值为150万元，每个大礼包中包含三种不同的代金券，分别为 “RMB 100-20”, "RMB 200-35" 和 “RMB 300-45”, 每一个优惠券大礼包中政府补贴100元.

第三轮优惠券大礼包从4月10日的10:00发放，总价值也是150万元，其规则和第一轮的优惠券一致，每一个优惠券大礼包政府补贴 50元。

![](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/20230324144130.png)

## 实证策略和数据

### 实证策略

文章的实证目标是评估短期政府优惠券项目的效果，作者拟采用DID的方法来评估获得消费券对于居民消费的影响。

文章面临的识别难题在于消费券并不是随机分配的，那些获得消费券的人可能和那些没有获得消费券的人之间本身便存在着很多消费行为上的差异。为了缓解类似的自选择问题，作者构建了一个控制组：在优惠券发放的当天，那些尝试去获得消费券但是最终失败的人群。

首先对于第一轮消费券发放，作者选取的处理前窗口期为3月20日至3月26日，处理后窗口期为3月27日至4月2日，其基本的计量模型如下：
$$
y_{i t}=  \alpha_0+\alpha_1 \text { Treat }_i+\alpha_2 \text { Post }_t+\alpha_3 \text { Treat }_i \times \text { Post }_t+\gamma X_{i t}+\varepsilon_{i t} (1)
$$
被解释变量 $y_{it}$ 代表消费者 $i$ 在时期 $t$ ($t=1$ 表示处理前；$t=2$ 表示处理后) 中的花费，变量 $Treat_i$  是一个指示变量(等于1代表处理组，等于0代表控制组)，系数 $\alpha_1$ 捕捉到处理组和控制组之间在消费上存在的基准差异，$Post_t$ 是一个哑变量(指示是否时期 $t$ 是消费券的兑换期)，系数 $\alpha_2$ 捕捉到时期之间花费存在的时间趋势，$X_{it}$ 表示其他可能影响花费的个体特征，如性别、年龄、2019年9月到2020年2月之间的平均每月花费，以及在3月初 (3月1日到3月19日) 的总花费，**标准误在个体层面进行聚类**。

作者们主要感兴趣的参数为 $\alpha_3$ ，这一参数估计了在消费券的兑换期中，处理组的消费者相较于控制组的消费者的平均过度花费。

为了评估政策有效性，作者定义了一个效率比:
$$
r=\frac{\alpha_3}{\text { amount of subsidy }}
$$
其中分母表示根据实际真正兑换的消费券来计算的平均每一份优惠券大礼包政府的平均补贴额度，比如说因为在第一轮中平均每人兑换3.5张代金券，因而平均补贴额度就是35元。从而效率比 $r$ 便捕捉了1元的政府补贴在拉动额外消费方面究竟多么有效，也就是这一政策的成本--收益比，这一比例非常相似于 MPC (额外的收入中有多大的比例消费者会用于消费)。

作者进一步探究了消费券的跨期影响，具体而言，作者们追踪了一个在第一轮中收到但是在第二轮中没有收到消费券大礼包的人们组成的随机样本，并且作者们将观察期延长到第一轮消费券到期之后的一周(4月3日到4月9日)，相应的控制组是那些在3月27日尝试获得消费券，但是一直到4月9日都没能获得消费券的人们组成的一个随机样本，回归模型如下所示：
$$
y_{i t}=  \alpha_0+\alpha_1 \text { Treat }_i+\alpha_2 \text { Post }_t+\alpha_3 \text { Post2 }_t+\alpha_4 \text { Treat }_i 
 \times \text { Post }_t+\alpha_5 \text { Treat }_i \times \text { Post2}_t+\gamma X_{i t}+\varepsilon_{i t} (2)
$$
模型1和模型2中的主要差异在于我们加入一个后兑换期 (4月3日到4月9日): $Post2_t$。

这次我们感兴趣的参数为 $\alpha_5$，这一参数估计了优惠券的滞后效应，如果这一参数是负的，那么意味着相较于控制组而言，处理组会减少他们在消费券到期之后一周的花费。因此优惠券两期的净效应为 $\alpha_4 + \alpha_5$

### 数据

作者在个体层面的数据来源于支付宝，但是由于阿里巴巴的数据保密协议，文章的原始数据不能公开，因而我们下面复现的数据来源于作者提供的合成数据(不能复现原文结果)，首先是描述性统计分析：

```R
## Summary Statistic for sample data
ddtsummstat<-stargazer(sample_data[,c(
  'user_gender'
  ,'user_age'
  ,'pay_amt_3up'
  ,'pay_amt6m'
)]
,covariate.labels =
  c('Gender'
    ,'Age'
    ,'Spending in March'
    ,'Average monthly spending'
  )
,median = FALSE
,iqr = FALSE
,title = "Sample data "
,digits=3
,omit.summary.stat = c("min","max","p25","p75")
)
```

其中`stargazer`各个选项的含义如下：`covariate.labels`表示输出表格中的变量标签；`median`表示变量的中位数是否会显示在描述性统计表格当中；`iqr` 表示每一个变量的25分位数和75分位数是否会显示在描述性统计表格中；`omit.summary.stat` 指明哪些描述性统计量会在描述性统计表格中省略。

![](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/20230324165744.png)

上表比较了那些至少兑换过一次的代金券的个体和那些成功获得消费券大礼包却没有兑换代金券的个体之间存在的差异：那些兑换优惠券的群体往往更多是女性、过去有着更高的消费、并且年龄要更大一些。作者进一步将第一轮和第二轮消费券中的控制组和处理组进行对比。

![](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/20230324170639.png)

作者发现控制组和处理组之间存在本身就存在较为显著的差异，比如控制组平均而言呈现更低的花费，为解决这一问题，作者采用倾向得分匹配的方法(PSM)来创建了一个更为类似的控制组，作者用来匹配的变量有年龄、性别、过去六个月的平均每月购物的商家的种类数，三月早期的总花费以及是否一个人拥有花呗账户。作者基于以上变量的Logistic回归计算了倾向得分并采用最近邻匹配的办法：

```R
## psm code
######matching sample
# Wave I 
data_for_0327N_0401N_g = read.csv('data_for_0327N_0401N_g')
psm_0327N_0401N <- matchit(coupon ~ user_age+user_gender+pay_amt6m+off_pay_amt6m+
                             pay_amt_3up+off_pay_amt_3up+hb_amt_1m6m+hb_credit_amt6m+avg_class_cnt,
                           data = data_for_0327N_0401N_g,method="nearest", ratio = 1,replace = FALSE
                           ,caliper=0.0001,discard = 'both')
# ## Wave II
d14_g = read.csv('d14_g.csv')
psm_test4_1_class <- matchit(coupon ~ user_age+user_gender+pay_amt6m+off_pay_amt6m+
                               pay_amt_3up+off_pay_amt_3up+hb_amt_1m6m+hb_credit_amt6m+avg_class_cnt,
                             data = d14_g,method="nearest", ratio = 1,replace = FALSE
                             ,caliper=0.0001,discard = 'both')

```

作者还进一步将处理组和控制组在两轮处理前后的花费的时序图绘制出来：


```R
daily_series = read.csv('wave1_daily_series.csv')
daily_series$dt  = factor(substr(daily_series$report_date,5,8))
options(repr.plot.width=12, repr.plot.height=4,repr.plot.res=150,repr.plot.quality=100,repr.plot.pointsize=14)
ggplot(data=daily_series, mapping=aes(x=dt, y=consum, group=type)) +
  geom_line(aes(linetype=type,color=type),size=1)+
  geom_point(aes(color=type))+
  theme_bw()+
  theme(legend.position="top")+
  theme(title=element_text(size=13),axis.text.x=element_text(size=12),axis.text.y=element_text(size=12),legend.text= element_text(size=12)  )+
  theme(panel.grid=element_blank(),panel.border=element_blank(),axis.line=element_line(size=0.1,colour='black'))+
  xlab('Date')+
  ylab('Amount')
```

![image-20230325211500314](D:\Stata17\personal\连享会推文\推文blog\推文30-MS消费券论文复现\image-20230325211500314.png)

```R
daily_series = read.csv('wave2_daily_series.csv')
daily_series$dt  = factor(substr(daily_series$report_date,5,8))
options(repr.plot.width=12, repr.plot.height=4,repr.plot.res=150,repr.plot.quality=100,repr.plot.pointsize=14)
ggplot(data=daily_series, mapping=aes(x=dt, y=consum, group=type)) +
  geom_line(aes(linetype=type,color=type),size=1)+
  geom_point(aes(color=type))+
  theme_bw()+
  theme(legend.position="top")+
  theme(title=element_text(size=13),axis.text.x=element_text(size=12),axis.text.y=element_text(size=12),legend.text= element_text(size=12)  )+
  theme(panel.grid=element_blank(),panel.border=element_blank(),axis.line=element_line(size=0.1,colour='black'))+
  xlab('Date')+
  ylab('Amount')
```



![](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/20230325211352.png)

## 主要回归结果

### 获得消费券的短期影响

$$
y_{i t}=  \alpha_0+\alpha_1 \text { Treat }_i+\alpha_2 \text { Post }_t+\alpha_3 \text { Treat }_i \times \text { Post }_t+\gamma X_{i t}+\varepsilon_{i t} 
$$

```R
# Baseline model Wave I (md1=payment; md2= offline; md3= online)
md1 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d14)
md2 = felm(off_pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d14)
md3 = felm(on_pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d14)
table<-stargazer(
  md1,
  md2,
  md3,
  no.space = TRUE,
  title=" The average effect on spending Wave II full sample results ", align=FALSE,
  omit.stat=c("LL","ser","f")
)


## PSM Sample
d_matched = data.table(read.csv('wave2_d_matched.csv'))
md1 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched)
md2 = felm(off_pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched)
md3 = felm(on_pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched)

table<-stargazer(
  md1,
  md2,
  md3,
  no.space = TRUE,
  title=" The average effect on spending Wave II PSM sample results ", align=FALSE,
  omit.stat=c("LL","ser","f")
)
```

![](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/20230325212907.png)

交互项 $Treat \times Post$ 衡量的是在7天优惠券兑换期内的处理效应。

第(1)列表明处理组中的人们在7天优惠券兑换期内平均要比控制组的人们多花费124.6元，如果采用匹配样本，结果为144.1元，这一结果在统计意义和经济意义上都是显著的，作者认为政府在每个优惠券大礼包中补贴的35元可以换来消费者额外花费124.6元，这意味着效率为3.5.

第2列和第3列将总花费分解为线下消费和线上消费，不难看出线下消费替代掉了线上消费，这是因为消费券只能用于线下消费。

下表反映了第二轮的结果：

![](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/20230325215616.png)

第二轮的分析和第一轮类似，此处不再赘述。作者通过使用匹配样本进一步将消费细化为五大种类

![image-20230325215955622](D:\Stata17\personal\连享会推文\推文blog\推文30-MS消费券论文复现\image-20230325215955622.png)

通过对消费进行细化分析，不难看出绝大多数消费者会将消费券用于吃喝等小额消费上面，也就是更多的花费在服务业等受到疫情影响较大的部门。

### 消费券的动态影响

作者在这一节中重点考虑的问题是消费券所诱导的消费是否会挤出消费者在随后几期的消费，换言之，消费券的处理效应是否存在跨期替代性。

为此作者在那些第一轮中获得消费券但是在第二轮中没能获得消费券的人群中随机抽取100000个人作为处理组，然后追踪他们在消费券过期之后一周(4月3日到4月9日)内的消费情况，控制组中包括100000个个体，他们在3月27日到4月9日尝试获得消费券但是失败了。作者采用的估计方程为：
$$
y_{i t}=  \alpha_0+\alpha_1 \text { Treat }_i+\alpha_2 \text { Post }_t+\alpha_3 \text { Post2 }_t+\alpha_4 \text { Treat }_i 
 \times \text { Post }_t+\alpha_5 \text { Treat }_i \times \text { Post2}_t+\gamma X_{i t}+\varepsilon_{i t}
$$

```R
## table7 code
d14wave1 = read.csv('d14wave1.csv')
model1 = felm(pay_amt~couponE+couponL+post+couponE:post+couponL:post+user_age+user_age2+user_gender+pay_amt6m
              +pay_amt_3up|0|0|user_id,data=d14wave1)

table<-stargazer(
  model1,
  no.space = TRUE,
  title="Early vs. Late split sample ", align=FALSE
  ,omit.stat=c("LL","ser","f")
)


d14w1min10 = read.csv('d14w1min10.csv')
d14w2min3 = read.csv('d14w2min3.csv')

model1 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data =d14w1min10)
model2 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data =d14w2min3)
model3 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data =data_for_0327N_0401N[pay_amt6m>=10000])

table<-stargazer(
  model1,
  model2,
  model3,
  no.space = TRUE,
  title="robust checks", align=FALSE
  ,omit.stat=c("LL","ser","f")
)
```



![](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/20230325221438.png)

表7的第一列的估计结果显示处理组要比控制组在优惠券有效期内平均而言多花费103.9元，而在优惠券过期之后的一周内少花费11.1元，但是在随后一周内的结果在统计上并不显著。

为了解决另外一个可能存在的替代性问题：跨期替代效应可能存在于更长的时期。作者利用最后一轮消费券(第五轮：4月30日发起，7天的兑换期) 来进一步检验滞后效应，这一轮消费券提供三张花40减10元的代金券，在这一轮之后再没有消费券的发放，因此作者随机抽取了100000个获得消费券的个体作为处理组以及那些尝试获得但是没能获得消费券的个体作为控制组，并且追踪了他们在消费券兑换期之后4周的消费行为，结果呈现在上表7的第二列，由于在处理期之后的四个月中交互项的系数均不显著，因此消费券并没有挤出效应。

### 消费者群体的异质性

```R
#### Age
p20 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[user_age<=30])
p21 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[user_age>30&user_age<=40])
p22 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[user_age>=41])

#######Huabe Usage
p16 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched1)
p17 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched2)
p18 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched3)
p19 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched4)

####Online Ratio Terciles
p13 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[on_ratios_rank==1])
p14 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[on_ratios_rank==2])
p15 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[on_ratios_rank==3])

####Monthly Spending Terciles
p10 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[pay_rank==1])
p11 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[pay_rank==2])
p12 = felm(pay_amt~coupon+post+coupon:post+user_age+user_age2+user_gender+pay_amt_3up+pay_amt6m|0|0|user_id,data = d_matched[pay_rank==3])

```

![](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/20230326192507.png)

作者根据每月的花费、线上支付的倾向、年龄以及使用是否花呗将全部样本分组进行回归，结果如上图所示。

### 稳健性检验

作者进行的稳健性检验为检验消费券申请时间的先后对于后续消费者花费是否有影响，作者将处理组均等分为两份 `Early` & `Late`。Early 表示在成功申请时间的前半部门时间，Late 表示在成功申请时间的后半部分时间。

```R
model1 = felm(pay_amt~couponE+couponL+post+couponE:post+couponL:post+user_age+user_age2+user_gender+pay_amt6m+pay_amt_3up|0|0|user_id,data=d14wave1)

```

![image-20230326200211777](D:\Stata17\personal\连享会推文\推文blog\推文30-MS消费券论文复现\image-20230326200211777.png)

上表显示两组处理效应的差别并不大，因此消费券的申请时间并不会对后续消费者花费产生影响。





