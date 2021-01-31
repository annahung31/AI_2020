# 5-3 Alpha-beta pruning

不錯的影片： [https://www.youtube.com/watch?v=l-hh51ncgDI](https://www.youtube.com/watch?v=l-hh51ncgDI) 

[https://www.youtube.com/watch?v=J1GoI5WHBto](https://www.youtube.com/watch?v=J1GoI5WHBto) 

一步一步推導，看看結果是不是跟 影片答案一樣

### Psudo code

![5-3%20Alpha-beta%20pruning%203683d6b432f140da994a2f9a80ccfe99/_2020-04-29_7.38.46.png](5-3%20Alpha-beta%20pruning%203683d6b432f140da994a2f9a80ccfe99/_2020-04-29_7.38.46.png)

6,8 行 是為了更新 alpha

7    行 發生cutoff (當 alpha/beta 交錯沒有交集，就回傳值，不再往下做 → pruning )

![5-3%20Alpha-beta%20pruning%203683d6b432f140da994a2f9a80ccfe99/_2020-04-29_7.40.32.png](5-3%20Alpha-beta%20pruning%203683d6b432f140da994a2f9a80ccfe99/_2020-04-29_7.40.32.png)

上面的 psudo code 可以發現 max 跟 min plater 的部分其實有很多相似，所以可以結合在一起。

差別：

1.  一個找 min, 一個找 max → 用 加一個負號解決

2. 一個更新 alpha, 一個更新 beta → 傳入 func 時 alpha beta 互換

### Main idea of alpha-beta pruning

其實是很符合真實情況的，因為假如對player來說，有某一個情況比另一個情況更有利，那比賽中player一定會選擇有力的那條路，因此不利的情況根本不會發生，也就不用去探討了。

### Performance

![5-3%20Alpha-beta%20pruning%203683d6b432f140da994a2f9a80ccfe99/_2020-04-29_7.45.24.png](5-3%20Alpha-beta%20pruning%203683d6b432f140da994a2f9a80ccfe99/_2020-04-29_7.45.24.png)

- 就算 pruning 都不發生，最糟也就退回跟 MinMaxㄧ樣而已。
- Best case:

![5-3%20Alpha-beta%20pruning%203683d6b432f140da994a2f9a80ccfe99/_2020-04-29_7.28.35.png](5-3%20Alpha-beta%20pruning%203683d6b432f140da994a2f9a80ccfe99/_2020-04-29_7.28.35.png)

第一層一定需要展開所有的branch, 第二層理想狀況就是每看第一個branch就發生cutoff, 於是平均來說展開的branch數為1。 → O(b^(m/2))  

也就是 effictive branch factor  `b` 變成 `根號b` 。假設原本每次都要展開9個 branch，現在平均只要展開 3個 就好了。

或者說，因為原本是 `m` ，變成 `m/2`  本來用來搜尋 2層的時間，現在可以搜尋 4層（兩倍）。

Best case 實務上蠻容易達成的，只要用iterative deepening, 每一次展開都使用 激勵函數 h 來預測哪一邊比較好，然後 reorder 讓好的先做，就很有機會達到 Best case。 因此，實務上 alpha-beta pruning 的 Time complexity 我們都用 best case 來討論。