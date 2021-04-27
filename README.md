中文 | [English](./README-EN.md)

请求地址：https://gateway.mdex.com/v2/<br/>
备用地址：https://gateway.mdex.cc/v2/


```
获取不同链数据参数：mdex_chainid = 128

HECO：128（默认）
BSC：56
```

### 一、获取MDX代币最新流通量
```
GET：mdex/circulation

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
GET：mdex_chainid

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

### 三、获取所有交易矿池列表
```
GET：mingpool/swap

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

### 四、获取所有流动性矿池列表
```
GET：mingpool/lps

参数：
mdex_chainid

返回示例：
{
    "result": {
        "0": {
            "pool_name": "WHT",
            "pool_apy": 0,
            "pool_tvl": 23685.934578122702,
            "pool_rate": 0,
            "pool_mdx": 0,
            "address": "0x5545153ccfca01fbd7dd11c0b23ba694d9509a6f",
            "pool_type": 1
        },
        "1": {
            "base_name": "HBTC/USDT",
            "pool_name": "HBTC/USDT",
            "pool_apy": 0.11815463665563869,
            "pool_tvl": 249367503.86806372,
            "pool_rate": 10.74,
            "pool_mdx": 81967.68,
            "address": "0xfbe7b74623e4be82279027a286fa3a5b5280f77c",
            "token0": "0x66a79d23e58475d2738179ca52cd0b41d73f0bea",
            "token1": "0xa71edc38d189767582c38a3145b5873052c3e47a",
            "pool_type": 1
        },
        ......
    },
    "code": 0,
    "message": "Success",
    "extra": null
}
```
示例说明：
| 字段     | 说明             |
| -------- | ---------------- |
|pool_id|池子ID|
|base_name| 池子显示名称（仅限LP池）|
|pool_name| 池子名称 |
|pool_apy|池子收益率(天)|
|pool_tvl|池子总质押资金|
|pool_rate|池子权重占比|
|address|池子单币（交易对）地址|
|pool_type|池子类型（1普通区/2创新区)|
|pool_mdx|MDX挖矿日产出|
|token0|交易对第一个代币地址（仅限LP池）|
|token1|交易对第二个代币地址（仅限LP池）|


### 五、获取董事会奖励池列表

```
GET：boardroom/reward/pool

参数：
mdex_chainid

返回示例：
{
    "result": {
        "boardroom_hmdx": {
            "0": "{\"pool_id\":0,\"pool_name\":\"MDX\",\"amount\":\"40000\",\"total_amount\":\"275000\",\"earned_token\":\"HMDX\",\"boardroom_type\":1,\"pool_tvl\":\"6349572.6225\",\"pool_apy\":229.93673540062053,\"pool_rate\":\"25\"}",
            "1": "{\"pool_id\":1,\"pool_name\":\"MDX/WBNB\",\"amount\":\"140000\",\"total_amount\":\"910000\",\"earned_token\":\"HMDX\",\"boardroom_type\":2,\"pool_tvl\":\"14604550.7395\",\"pool_apy\":349.8909409227993,\"pool_rate\":\"30\"}"
        },
        "boardroom_mdx": {
            "0": "{\"pool_id\":0,\"pool_name\":\"HMDX/MDX\",\"amount\":\"100000\",\"total_amount\":\"670000\",\"earned_token\":\"MDX\",\"boardroom_type\":2,\"pool_tvl\":\"12395654.4578\",\"pool_apy\":294.4580306291761,\"pool_rate\":\"10\"}",
            "1": "{\"pool_id\":1,\"pool_name\":\"MDX/USDT\",\"amount\":\"120000\",\"total_amount\":\"720000\",\"earned_token\":\"MDX\",\"boardroom_type\":2,\"pool_tvl\":\"14633240.5690\",\"pool_apy\":299.31852615665593,\"pool_rate\":\"35\"}"
        }
    },
    "code": 0,
    "message": "Success",
    "extra": null
}
```
示例说明：
| 字段     | 说明             |
| -------- | ---------------- |
|boardroom_hmdx|奖励HMDX池子|
|boardroom_mdx|奖励MDX池子|
|pool_id|池子ID|
|amount|奖励金额|
|total_amount|已奖励总金额|
|earned_token|奖励代币名称|
|boardroom_type|池子类型(1单币/2LP)|
|pool_tvl|池子当前TVL|
|pool_apy|收益率|
|pool_rate|权重比例|

### 六、获取Token最新价格

```
GET：token/price

参数：
mdex_chainid

返回示例：
{
    "result": {
        "0x7130d2a12b9bcbfae4f2634d864a1ee1ce3ead9c": {
            "address": "0x7130d2a12b9bcbfae4f2634d864a1ee1ce3ead9c",
            "symbol": "BTCB",
            "decimals": 18,
            "price": "53920.0958381121861529025898899511160399516143"
        },
        "0x55d398326f99059ff775485246999027b3197955": {
            "address": "0x55d398326f99059ff775485246999027b3197955",
            "symbol": "USDT",
            "decimals": 18,
            "price": 1
        },
        ......
    },
    "code": 0,
    "message": "Success",
    "extra": null
}
```
```
示例说明：
| 字段     | 说明             |
| -------- | ---------------- |
|address| Toekn地址|
|symbol|标识名称|
|decimals|精度|
|price|当前价格|



