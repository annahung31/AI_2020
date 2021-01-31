# 3-8 Best-first search- Greedy search

選當下最好的

- Greedy search
- A* search

[https://lh4.googleusercontent.com/2raKPcKm_60LuJ7zCtPWwNxUVYS1Vx3_F2tE9O6sW6dOFTcRFW6Y4iaLrRagR8cEJbzLrqoa54q6NxKhOs7sG4Ij39D12VC69jBaQntk8ZJtMenjmp7Idva2-5yNthDIHC0e-gJ-](https://lh4.googleusercontent.com/2raKPcKm_60LuJ7zCtPWwNxUVYS1Vx3_F2tE9O6sW6dOFTcRFW6Y4iaLrRagR8cEJbzLrqoa54q6NxKhOs7sG4Ij39D12VC69jBaQntk8ZJtMenjmp7Idva2-5yNthDIHC0e-gJ-)

f(n): 每個節點依據的func

h(n): 激勵函數

g(n): path cost

前面提到的uniform cost，是每一步考慮path cost, 其實就是g(n)

所以A* = greedy + uniform cost

### Example

上面捷運的例子中， 把與北車的直線距離當作h(n)

### Properties

[https://lh4.googleusercontent.com/_vQ7QJDOWq7dSwKm1QvdefSUwIPbesAa8Evbtaq-FNg-OuzoELC5gm4ZL2jxrmKuNmXpUsdFmShI1RtmexNiRaHWxVgVxE7Muwx2kI1VyL7oh30PmoNgAvlmBSwej2APQfYNH00h](https://lh4.googleusercontent.com/_vQ7QJDOWq7dSwKm1QvdefSUwIPbesAa8Evbtaq-FNg-OuzoELC5gm4ZL2jxrmKuNmXpUsdFmShI1RtmexNiRaHWxVgVxE7Muwx2kI1VyL7oh30PmoNgAvlmBSwej2APQfYNH00h)

沒有completeness:例如從中山國中開始，要去北車，但是因為松山機場的h(n)= 75 < 南京東路(77)，所以會選擇往松山機場，可是再來就沒路了，只會返回中山國中，進到無窮loop裡面。

如果用Graph, 紀錄拜訪過的點，可能會好一點，但仍有可能發生無窮迴圈的情況。

[https://lh5.googleusercontent.com/QAfiekjYqlkj11WeVtDTetXrN2ZNuelYmNl3214d9Q07iqWY7ZquORsvASQG2lOgx6dfW-fmGlgMDO5lUnCbJtQ9SShFnSaEOxt18bvAuI1WQgy4nsw9CrCCCuznc2w35gYRPIL7](https://lh5.googleusercontent.com/QAfiekjYqlkj11WeVtDTetXrN2ZNuelYmNl3214d9Q07iqWY7ZquORsvASQG2lOgx6dfW-fmGlgMDO5lUnCbJtQ9SShFnSaEOxt18bvAuI1WQgy4nsw9CrCCCuznc2w35gYRPIL7)

- 影響Time/space 複雜度的重要因素：一個好的激勵函數h(n)。