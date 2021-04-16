中文 | [English](./README-EN.md)

请求地址：https://gateway.mdex.com/v2/<br/>
备用地址：https://gateway.mdex.cc/v2/

获取不同链数据参数：<br/>
mdex_chainid：128(HECO)、56(BSC)，默认：128

### 一、获取MDX代币最新流通量
```
mdex/circulation

参数：
无

返回示例：
228615002.31705
```
| 字段     | 说明 |
| -------- | ---------------- |
|无|纯数字的MDX总流通量|


### 二、获取MDEX相关统计数据
```
mdex/charts

参数：
mdex_chainid

返回示例：
{
    "result": {
        "fee_24hr": "6101451.5915617799824494785043093",
        "total_fees": "519527593.3513776",
        "volume_24hr": "2033817197.1872599941498261681",
        "total_volume": "173175864450.4592",
        "mdex_tvl": "2223538443.6082106",
        "mdex_info": {
            "price": "3.589065093420289509",
            "market": 717917031.7217036,
            "supply": 200028980.53808954
        },
        "reward_amount": 151066115.87037376,
        "destroy_amount": 23763518.670275524,
        "destory_price": 0,
        "total_destroy": "21187462.59235659203873915",
        "total_buy": 80142000,
        "heco_total_tvl": "2223543188.7940917",
        "bsc_total_tvl": "2657211329.661495",
        "total_chain_tvl": 4880754518.455587
    },
    "code": 0,
    "message": "Success",
    "extra": null
}
```
示例说明：
| 字段     | 说明             |
| -------- | ---------------- |
| Fee_24hr | 24小时交易手续费 |
| total_fees | 总交易手续费 |
| volume_24hr | 24小时交易额 |
| total_volume | 总交易额 |
| mdex_tvl | 当前链的流动性质押 |
| mdex_info.price | MDX现价 |
| mdex_info.market | MDX当前市值 |
| mdex_info.supply | MDX当前流通量 |
|reward_amount | 待奖励金额|
| destroy_amount | 待回毁金额 |
| destory_price | 回购均价 |
| total_destroy | 总回购金额 |
|total_buy | 总回购MDX数量 |
|heco_total_tvl| HECO链的总流动性质押 |
|bsc_total_tvl| BSC链的总流动性质押 |
|total_chain_tvl| 所有链的总流动性质押 |

### 三、获取所有流动性挖矿池列表
```
mingpool/swap

参数：
mdex_chainid

返回示例：
{
    "result": [
        {
            "pool_id": 0,
            "base_name": "WHT/HUSD",
            "pair": "0x3375aff2cacf683b8fc34807b9443eb32e7afff6",
            "pair_name": "HUSD/WHT",
            "token0": "0x0298c2b32eae4da002a15f36fdf7615bea3da047",
            "token0_decimal": 18,
            "token1": "0x5545153ccfca01fbd7dd11c0b23ba694d9509a6f",
            "token1_decimal": 18,
            "alloc_point": "1027",
            "alloc_mdx_amt": "53154133296010852817828",
            "total_quantity": "19576628010942810580676009278",
            "pool_quantity": "67410161137700056686583308",
            "pool_rate": "10.27",
            "fee_refund": 94.40117817937994
        },
        ......
    ],
    "code": 0,
    "message": "Success",
    "extra": null
}
```
示例说明：
| 字段     | 说明             |
| -------- | ---------------- |
|pool_id|池子ID|
|base_name| 池子名称 |
|pair|交易对地址|
|pair_name|交易对名称|
|token0|交易对第一个代币地址|
|token0_decimal|交易对第一个代币精度|
|token1|交易对第二个代币地址|
|token1_decimal|交易对第二个代币精度|
|alloc_point|当前池子权重|
|alloc_mdx_amt| 当前MDX总奖励|
|total_quantity|交易总额|
|pool_quantity|当前交易额|
|pool_rate|当前池子占比|
|fee_refund|当前池子交易手续费返还比例|

