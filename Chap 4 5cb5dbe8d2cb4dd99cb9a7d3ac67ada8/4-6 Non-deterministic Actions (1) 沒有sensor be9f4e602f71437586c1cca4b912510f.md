# 4-6 Non-deterministic Actions (1) :沒有sensor

做一個動作，可能有不同的結果

AND node: 因為不知道你會去哪個state, 要求你兩邊都一定要走到goal

Loop: 可能陷入無窮迴圈

OR 只要走一支 （原本的動作）

AND 要兩條都走（因為不確定性造成的選擇）

Ex2:

很滑的房間

如果 loop 來源是機率問題，就一直試。

如果來源是 因為有些東西無法觀測, 例如兩房間之間有門，有時會開有時不會，也沒有 sensor 可以觀測 →  試到一定次數就放棄

 

## 觀察能力

belief states: 是一個 state的集合，你相信目前世界的狀態是其中之一。

### 如果完全沒有辦法觀測（沒有sensor）

其實通常比較可信賴，因為不用倚賴sensor。（因為萬一sensor壞掉，就會失敗）

做一些action的時候， belief 就會變化

例如吸塵器世界：

原本總共有8種可能狀態，當吸塵器往右移，就剩下四種可能

開始吸→ 剩下兩種可能

![4-6%20Non-deterministic%20Actions%20(1)%20%E6%B2%92%E6%9C%89sensor%20be9f4e602f71437586c1cca4b912510f/_2020-04-27_11.51.24.png](4-6%20Non-deterministic%20Actions%20(1)%20%E6%B2%92%E6%9C%89sensor%20be9f4e602f71437586c1cca4b912510f/_2020-04-27_11.51.24.png)

在 deterministic 世界中， 轉換過程中 belief state 不是變少就是保持一樣，不會變多。

但如果是 non-deterministic，belief state 就可能變多，因為有機率發生不同的情況。

這樣就很難找出solution，因為很難把 belief state 縮小到只剩 goal state。

解決：裝 sensor → [With sensor](4-7_Non-deterministic-action.md)