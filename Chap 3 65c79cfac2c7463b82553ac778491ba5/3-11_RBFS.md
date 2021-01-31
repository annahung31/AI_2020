# 3-11 RBFS

重點在於，會記得第二好的選擇，有backtrack的能力。

當一直往下探索發現不對時，能夠回到那個第二好的選擇。

![3-11%20RBFS%20e6b372788b2446989351bd993a4d0ce4/_2020-04-26_10.24.33.png](3-11%20RBFS%20e6b372788b2446989351bd993a4d0ce4/_2020-04-26_10.24.33.png)

重點在 8~ 13行！

`f_limit`  是 目前最好的選擇（最低的 cost）

## 例子推導

看下面的例子

![3-11%20RBFS%20e6b372788b2446989351bd993a4d0ce4/_2020-04-26_10.29.44.png](3-11%20RBFS%20e6b372788b2446989351bd993a4d0ce4/_2020-04-26_10.29.44.png)

一開始是古亭(58)，此時 `f_limit` 是 無窮大。

expand 古亭： 有 `中正紀念堂` 跟 `東門` 兩個 successors。

[9] 此時 `best.f` 是 東門 (68)， 

[10] 因為  min(`best.f`, `f_limit`) = `best.f`，所以繼續往下。

[11] `alternative` 是 succesors中第二好的選擇：也就是 `中正紀念堂` ， `alternative` = 73

[12] 遞迴往下，這時候換成 `東門` 為 init，

並且比較  min(`f_limit`,`alternative`) = `alternative` = 73，成為新的 `f_limit` 。

展開東門： 共有四個successors， `best.f` = 80  ，是 `忠孝新生` ，

`best.f` > `f_limit` → `東門` 的 f 改成 80，跳到 `alternative = 中正紀念堂` ，此時的 `f_limit` 修改為 80。

expand 中正紀念堂， `best` 是 台大醫院， `best.f` 是 85， 比 `f_limit` 大， 則 `f_limit` 改為 85，跳回 剛剛的 `alternative=東門` 。

東門往下expand, 再次得到 `best` 是忠孝新生，此時 `best.f` < `f_limit` ，沒事，繼續往下。

忠孝新生往下expand, 得到 `best` 是善導寺，此時  `best.f` < `f_limit` ，沒事，繼續往下。

善導寺往下expand, 得到 `best` 是台北車站，此時  `best.f` < `f_limit` ，沒事，繼續往下

台北車站 往下expand, 發現是Goal，結束。

### Properties

- Complete 跟 Optimal 跟 A* 一樣（複習 → [A*](3-9_best-first-search.md)）
- time complexity 取決於跳來跳去換path的頻率。

    而且會需要把 忘記的node 再重新跑一次，感覺還是不太優啊。 → 改進： [Memory-Bounded Search](3-12_Memory-Bounded_search.md)

- Space:  跟 DFS類似，接近linear:   O(bd)