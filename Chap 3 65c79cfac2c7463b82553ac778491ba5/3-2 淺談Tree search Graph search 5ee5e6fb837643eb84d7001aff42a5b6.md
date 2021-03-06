# 3-2 淺談Tree search/ Graph search

### Tree search

Tree 假如沒有紀錄以探索過的，就會把問題複雜化：

![img/3-2-1](img/3-2-1.png)

上面的例子，

左邊圖其實是一個linear的問題

但是假如用tree 展開，又沒有標示重複節點

就會讓這個問題變成2^n 的複雜問題。

Solve: 用queue來紀錄已經探索過的states

更快的方式：建hash table紀錄，只要比較hash值就知道是否探索過。可是很花記憶體。

### Graph search

![img/3-2-2](img/3-2-2.png)

如果沒有探索過，也不在frontier （目前最前線待探索的nodes）裡面，才加進frontier。

- Loop invariant proof: 證明一定能夠找到goal
- State跟node的差別： node是程式上的，會紀錄更多資訊，例如 parent node是誰, 多少cost, depth, childen等等。 state沒有這些資訊。
- 不同strategy的差別在於把node 從 frontier拿出來時依循不同準則。 FIFO/LIFO/priority queue

### 評估strategy的指標：

1. Completeness: 是否總是能找到答案？
2. Optimality: 是不是總能找到最佳解？
3. Time complexity: 時間複雜度 （要找多少node才能找到答案？）
4. Space complexity: 空間複雜度（要用多少memory?） <- 大AI時代需要考量的問題
- Time 跟 Space 複雜度會用到的指標：

![img/3-2-3](img/3-2-3.png)