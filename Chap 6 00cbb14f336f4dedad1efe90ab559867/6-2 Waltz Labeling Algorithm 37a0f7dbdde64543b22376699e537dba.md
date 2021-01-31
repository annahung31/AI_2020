# 6-2 Waltz Labeling Algorithm

判斷木塊的相對位置

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.03.51.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.03.51.png)

對電腦來說， 掃描所有的邊，(edge labeling) 並討論這些邊如何建構出物體，彼此間的相對關係。

每一個邊都是一個 variable，並且可以依照這個邊的性質給他label

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.06.29.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.06.29.png)

+: 連接兩個面，在最高點

-:連接兩個面，在最低點

→ : 白邊在左邊

不同的邊，就會建構出不同形狀

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.09.05.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.09.05.png)

另一種方式，是把每個頂點視為一個 variable, 去找出它可能是哪種邊界組合起來的

挑一個頂點開始，找出它的可能性，而且要考慮他旁邊的另外一個頂點，兩點共用的邊性質需相同。

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.31.30.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.31.30.png)

### 搜尋的另一種表示法

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.33.04.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.33.04.png)

試將WA 畫成紅色 → 叫他的鄰居把紅色拿掉

constraint propagation ( 限制會隨著選項越來越少而增加)

→ Arc consistency 

 

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.39.44.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.39.44.png)

在這一步，因為 NT 跟 SA 只能有一個人是藍色，而 SA 跟 NSW 又是鄰居必須不同色，所以我們知道， NSW 一定不能是藍色，只能是紅色。

那當NSW是紅色，則 V 一定不能是紅色，所以移除紅色選項。一直往下check

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.42.15.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.42.15.png)

### Arc consistency Psudo code

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.43.07.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_9.43.07.png)

叫 AC-3 是因為他們出到第三版 paper 才真的沒有bug

### k-consistency

你永遠至少還有k個  legel value

### Critical ratio

![6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_10.11.01.png](6-2%20Waltz%20Labeling%20Algorithm%2037a0f7dbdde64543b22376699e537dba/_2020-04-30_10.11.01.png)

R 大 跟 R小都容易成功，但是在某個 R 會很難做