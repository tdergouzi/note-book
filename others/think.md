# Think is power



1. 如何理解 “经典 AMM 中的流动性在从 0 到无穷大的整个价格范围内均匀分布” ？

用户在无论哪个价格位置利用了流动性（swap），在经典 AMM 中这里的流动性代表的是整个流动性，所以产生的收益由所有提供流动性的用户所有。关于 “流动性利用率较低” 这个衍生问题，理解为由于上述情况，对于单个在活跃价格位置提供了流动性的用户来说，其收益和在其他价格位提供了同样数量流动性的用户是一样的，但成本更高。



2. 如何理解 “Uniswap V3 将流动性集中在具有连续 `x * y = k` 曲线的固定范围内” ？



3. 如何理解 Uniswap V3 白皮书中 "This is simple to implement and allows liquidity to be efficiently aggregated, but means that much of the asserts held in a pool are never touched." ?

