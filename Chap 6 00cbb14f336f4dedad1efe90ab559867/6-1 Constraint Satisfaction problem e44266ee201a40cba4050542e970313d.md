# 6-1 Constraint Satisfaction problem

Constraint Graph

有一些Variable, 

對應到一些 domain，

有一些constraint 

找出符合constraint的解

例子：

![6-1%20Constraint%20Satisfaction%20problem%20e44266ee201a40cba4050542e970313d/_2020-04-30_8.54.08.png](6-1%20Constraint%20Satisfaction%20problem%20e44266ee201a40cba4050542e970313d/_2020-04-30_8.54.08.png)

![6-1%20Constraint%20Satisfaction%20problem%20e44266ee201a40cba4050542e970313d/_2020-04-30_8.41.34.png](6-1%20Constraint%20Satisfaction%20problem%20e44266ee201a40cba4050542e970313d/_2020-04-30_8.41.34.png)

### 找 most constrained variable

找到具有最少 legal value 的那個 variable 開始做，成功率就比較高，因為它就會給其他人constraint。

 → `mininum remaining values` (MRV)  

例如在上面的例子裡，該選中間那塊開始，因為他有最多鄰居

![6-1%20Constraint%20Satisfaction%20problem%20e44266ee201a40cba4050542e970313d/_2020-04-30_8.51.41.png](6-1%20Constraint%20Satisfaction%20problem%20e44266ee201a40cba4050542e970313d/_2020-04-30_8.51.41.png)

反之，假如從限制最少的variable出發，那一路上就一直都挑限制少的先做，並且考慮把選擇留給限制少的

### Chronological backtracking

搜尋失敗時，返回上一層

### Backjumping

不止返回上一層，而是返回到導致失敗的那一個node ( conflict set )