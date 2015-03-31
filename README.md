
#赛题与数据
---------------------------------------------------------------------------------------
##文件名称

###文件格式

    1. tianchi_mobile_recommend_train_item.csv
    2. tianchi_mobile_recommend_train_user.zip
    3. 选手结果数据样例.csv

##竞赛题目 
在真实的业务场景下，我们往往需要对所有商品的一个子集构建个性化推荐模型。在完成这件任务的过程中，我们不仅需要利用用户在这个商品子集上的行为数据，往往还需要利用更丰富的用户行为数据。定义如下的符号：

*U——用户集合

*I——商品全集

*P——商品子集，P ⊆ I

*D——用户对商品全集的行为数据集合

那么我们的目标是利用D来构造U中用户对P中商品的推荐模型。

##数据说明
竞赛数据包含两个部分。第一部分是用户在商品全集上的移动端行为数据（D）,表名为tianchi_mobile_recommend_train_user，包含如下字段：

 | 字段                       | 字段说明                | 提取说明       |
 |----------------------------|:-----------------------:|---------------:|
 | user_id                    | 用户标识                | 抽样&字段脱敏  |
 | item_id                    | 商品标识                |   字段脱敏     |
 | behavior_type              | 用户对商品的行为类型    |包括浏览、收藏、加购物车、购买，对应取值分别是1、2、3、4。|
 | user_geohash               | 用户位置的空间标识，可以为空   | 由经纬度通过保密的算法生成 |
 | item_category              | 商品分类标识            | 字段脱敏       |
 | time                       | 行为时间                | 精确到小时级别 |

第二个部分是商品子集（P）,表名为tianchi_mobile_recommend_train_item，包含如下字段： 

 |字段                              |字段说明                            |  提取说明   |
 |--------------------------------- |:----------------------------------:|------------:|
 | item_id                          | 商品标识                           |抽样&字段脱敏|
 | item_ geohash                    | 商品位置的空间标识，可以为空       |由经纬度通过保密的算法生成|
 | item_category                    | 商品分类标识                       |  字段脱敏 |

`训练数据包含了抽样出来的一定量用户在一个月时间之内的移动端行为数据（D），评分数据是这些用户在这个一个月之后的一天对商品子集（P）的购买数据。
参赛者要使用训练数据建立推荐模型，并输出用户在接下来一天对商品子集购买行为的预测结果。 `

###评分数据格式
具体计算公式如下：参赛者完成用户对商品子集的购买预测之后，需要将结果放入指定格式的数据表（非分区表）中，要求结果表名为：tianchi_mobile_recommendation_predict，包含user_id和item_id两列（均为string类型）,要求去除重复。例如：

###初赛数据
初赛阶段提供10000用户的完整行为数据以及百万级的商品信息；训练和预测的数据将会在4月20日进行一次切换（即切换为另一批10000用户的数据）。

###决赛数据
决赛阶段提供500万用户的完整行为数据以及千万级的商品信息。

###评估指标
比赛采用经典的精确度(precision)、召回率(recall)和F1值作为评估指标。具体计算公式如下：
***
其中PredictionSet为算法预测的购买数据集合，ReferenceSet为真实的答案购买数据集合。我们以F1值作为最终的唯一评测标准。


>[天池](http://tianchi.aliyun.com)
