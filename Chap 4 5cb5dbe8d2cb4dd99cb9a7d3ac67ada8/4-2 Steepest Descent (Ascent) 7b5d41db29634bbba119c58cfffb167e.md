# 4-2 Steepest Descent (Ascent)

也就是 Gradient descent

### Example

舉商人旅行問題為例：

![4-2%20Steepest%20Descent%20(Ascent)%207b5d41db29634bbba119c58cfffb167e/_2020-04-27_8.56.14.png](4-2%20Steepest%20Descent%20(Ascent)%207b5d41db29634bbba119c58cfffb167e/_2020-04-27_8.56.14.png)

SWAP-2: 任選兩個邊調換。

給定 n 個 city，以及init state，一直做 SWAP-2，計算 tour 長度，挑長度較短的。

Example 2 :

![4-2%20Steepest%20Descent%20(Ascent)%207b5d41db29634bbba119c58cfffb167e/_2020-04-27_10.26.06.png](4-2%20Steepest%20Descent%20(Ascent)%207b5d41db29634bbba119c58cfffb167e/_2020-04-27_10.26.06.png)

在 scale 不大的時候， 例如 n ≤ 10^6, 可以找到解法。

但是不一定能夠找到最佳解。

### Performance

![4-2%20Steepest%20Descent%20(Ascent)%207b5d41db29634bbba119c58cfffb167e/_2020-04-27_9.06.35.png](4-2%20Steepest%20Descent%20(Ascent)%207b5d41db29634bbba119c58cfffb167e/_2020-04-27_9.06.35.png)

Ｑ：只能找到 local optimum

解法： random start，多做幾次。 Cost的計算： 成功一次的cost + 失敗多次的 cost。

解法2:  → [SA](https://www.notion.so/4-3-Simulated-Annealing-SA-dfefdefa3244419e950027f1245c2df4)

Ｑ：有 Zig-zagging的問題（走Z字形路徑，浪費時間）

解法： 用 momentum 紀錄歷史路徑，走路的當下不只看相對高點，也要看歷史路徑。