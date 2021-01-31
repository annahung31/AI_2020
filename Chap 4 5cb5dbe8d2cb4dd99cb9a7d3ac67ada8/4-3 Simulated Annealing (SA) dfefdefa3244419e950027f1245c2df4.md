# 4-3 Simulated Annealing (SA)

中文名稱是 模擬退火法，名字來自於鑄鐵的時候，利用一開始高溫讓鐵有可塑性，允許各種形狀調整，當溫度下降，可塑性漸漸降低。

前面 steepest 的問題是當初始狀態在 小山峰（local optimum），他就只會找到小山峰山頂，沒辦法走到最高的山峰。所以 SA 引入 參數 `T` = temperture：

剛開始溫度高 ，`T` 大→ 有較高的彈性選擇下一步，不一定要非得往高處走 → 有機會換山峰

隨著時間溫度降低 ，`T` 漸小 → 選定山峰了，開始只能往高處走 → 找到 global optimum。

![4-3%20Simulated%20Annealing%20(SA)%20dfefdefa3244419e950027f1245c2df4/_2020-04-27_10.36.40.png](4-3%20Simulated%20Annealing%20(SA)%20dfefdefa3244419e950027f1245c2df4/_2020-04-27_10.36.40.png)

如果是相對高點（ delta E > 0 ) → 一定接受

如果是相對低點 ( delta E < 0) → 有一定的機率會接受，機率表示為  e^(`delta E` / `T` )

當 `T` 漸小 → (`delta E` / `T` ) 漸漸趨近於 - inf →  e^(`delta E` / `T` ) 趨近於 0 → 失去接受低點的彈性。

- 研究問題： `T` 要如何降，才能最有效找到global optimum?  ex: 變化劇烈的時候， 就下降慢一點。
- 理論上說只要 `T` 降得夠慢，就一定能找到最佳解，但是沒用啊，要降到天荒地老嗎QQ

### Code

![4-3%20Simulated%20Annealing%20(SA)%20dfefdefa3244419e950027f1245c2df4/_2020-04-27_10.42.56.png](4-3%20Simulated%20Annealing%20(SA)%20dfefdefa3244419e950027f1245c2df4/_2020-04-27_10.42.56.png)