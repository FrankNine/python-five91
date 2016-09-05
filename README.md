# python-five91

A simple [591.com.tw](https://www.591.com.tw) wrapper.

## Disclaimer

- I don't work for or have any affiliation with 591.com.tw
- This module was implemented for educational purpose. It should not be used for crawling or downloading data from 591.com.tw.
- This module was tested in python3, and may not work well under python2.

## Install

```
pip install five91
```

## Usage

Basic search

```py
#!/usr/bin/env python3

from five91 import Rent591
import json

r = Rent591()
result = r.search(region=1)
print (json.dumps(result, indent=4, ensure_ascii=False))

# search result:
{
    "region": 1,
    "count": 1234,
    "main": [
        {
            "url": "https://...",
            "kind": "...",
            "title": "...",
            "area": 123.4,
            "price": 12345,
            "section": "..."
        },
        {
            "url": "https://...",
            "kind": "...",
            "title": "...",
            "area": 123.4,
            "price": 12345,
            "section": "..."
        },
        ...
        ...
    ]
    "recom": [
        {
            "url": "https://...",
            "kind": "...",
            "title": "...",
            "area": 123.4,
            "price": 12345,
            "section": "..."
        },
        {
            "url": "https://...",
            "kind": "...",
            "title": "...",
            "area": 123.4,
            "price": 12345,
            "section": "..."
        },
        ...
        ...
    ]
}
```

### Struct of search() result

- `region` : code of region, region is top level adminisrative division, such as "新北市", "台北市"...etc.
- `count`: total count of objects meet the search criteria.
- `main`: main search result, 40 objects per search query.
- `recom`: recommended search result, will not chaned when changing `firstRow` of a search query.

### Struct of each rent info

- `title`: as title.
- `url`: link to the rent-object info page.
- `kind`: may be one element of the list ['整層住家', '獨立套房', '分租套房', '雅房', '店面', '辦公', '住辦', '廠房'...]
- `area`: area size, unit in "坪".
- `price`: price, unit in NTD.
- `section`: sub division of region, ex. "中山區", "松山區"...etc.

### Search parameters

- `region`: integer, default is `1`, please reference "Region value-txt table".
- `kind`: integer, can be skipped, please reference "Kind value-txt table".
- `section`: integer, can be skipped, please reference "Section value-txt table".
- `rentprice`: integer, default is `0`, its the range of rent price, please reference "Rent value-txt table".
- `pattern`: integer, means "格局" in chinese, please reference "Pattern value-txt table".
- `first_row`: pagination related, please see "Pagination".
- `total_rows`: pagination related, please see "Pagination".
- `shType`: `hurryRent` = "急租"，`host` = "屋主"

## Pagination

(under construction)

## Variable Tables

### Region value-txt table

| value |   txt  |
|:-----:|:------:|
|   0   | 全台灣 |
|   1   | 台北市 |
|   3   | 新北市 |
|   6   | 桃園市 |
|   4   | 新竹市 |
|   5   | 新竹縣 |
|   21  | 宜蘭縣 |
|   2   | 基隆市 |
|   8   | 台中市 |
|   10  | 彰化縣 |
|   14  | 雲林縣 |
|   7   | 苗栗縣 |
|   11  | 南投縣 |
|   15  | 台南市 |
|   17  | 高雄市 |
|   12  | 嘉義市 |
|   13  | 嘉義縣 |
|   19  | 屏東縣 |
|   22  | 台東縣 |
|   23  | 花蓮縣 |
|   24  | 澎湖縣 |
|   25  | 金門縣 |
|   26  | 連江縣 |

### Section value-txt table

| value |   txt  |
|:-----:|:------:|
|   3   | 中山區 |
|   5   | 大安區 |
|   7   | 信義區 |
|   10  | 內湖區 |
|   8   | 士林區 |
|   4   | 松山區 |
|   1   | 中正區 |
|   9   | 北投區 |
|   12  | 文山區 |
|   2   | 大同區 |
|   11  | 南港區 |
|   6   | 萬華區 |

| value |   txt  |
|:-----:|:------:|
|   26  | 板橋區 |
|   38  | 中和區 |
|   50  | 淡水區 |
|   44  | 新莊區 |
|   43  | 三重區 |
|   34  | 新店區 |
|   37  | 永和區 |
|   27  | 汐止區 |
|   46  | 林口區 |
|   39  | 土城區 |
|   41  | 樹林區 |
|   47  | 蘆洲區 |
|   40  | 三峽區 |
|   48  | 五股區 |
|   45  | 泰山區 |
|   42  | 鶯歌區 |
|   28  | 深坑區 |
|   49  | 八里區 |
|   51  | 三芝區 |
|   30  | 瑞芳區 |
|   20  | 萬里區 |
|   21  | 金山區 |
|   33  | 貢寮區 |
|   31  | 平溪區 |
|   29  | 石碇區 |
|   52  | 石門區 |
|   36  | 烏來區 |
|   35  | 坪林區 |
|   32  | 雙溪區 |

### Kind value-txt table

| value |    txt   |
|:-----:|:--------:|
|   0   |   不限   |
|   1   | 整層住家 |
|   2   | 獨立套房 |
|   3   | 分租套房 |
|   4   |   雅房   |
|   5   |   店面   |
|   6   |   辦公   |
|   12  |   住辦   |
|   7   |   廠房   |
|   11  |   土地   |
|   5   |   攤位   |
|   8   |   車位   |
|   21  |   場地   |
|   24  |   其他   |

* search with kind value >= 5 is not supported.

### shType values

- `hurryRent`: "急租"
- `host`: "屋主"

### Rent price value-txt table

| value |      txt      |
|:-----:|:-------------:|
|   0   | 不限          |
|   1   | 5000元以下    |
|   2   | 5000-10000元  |
|   3   | 10000-15000元 |
|   4   | 15000-20000元 |
|   5   | 20000-40000元 |
|   6   | 40000元以上   |

### Pattern value-txt table

| value |   txt   |
|:-----:|:-------:|
|   0   |   不限  |
|   1   |   1房   |
|   2   |   2房   |
|   3   |   3房   |
|   4   |   4房   |
|   5   | 5房以上 |

### Area value-txt table

| value |    txt   |
|:-----:|:--------:|
|   0   | 不限     |
|   1   | 20坪以下 |
|   2   | 20-30坪  |
|   3   | 30-40坪  |
|   4   | 40-50坪  |
|   5   | 50坪以上 |

### Shape value-txt table

| value |    txt   |
|:-----:|:--------:|
|   1   |   公寓   |
|   2   | 電梯大廈 |
|   3   |  透天厝  |
|   4   |   別墅   |

### Role value-txt table

| value |     txt    |
|:-----:|:----------:|
|   1   | 屋主刊登   |
|   2   | 代理人刊登 |
|   3   | 仲介刊登   |

### Other value-txt table

|   value   |     txt    |
|:---------:|:----------:|
| cartplace | 有車位     |
| balcony_1 | 有陽台     |
| cook      | 可開伙     |
| pet       | 可養寵物   |
| trabus    | 近公車站   |
| lease     | 可短期租賃 |

### Option value-txt table

|    value   |     txt    |
|:----------:|:----------:|
| tv         | 有電視     |
| cold       | 有冷氣     |
| icebox     | 有冰箱     |
| hotwater   | 有熱水器   |
| washer     | 有洗衣機   |
| naturalgas | 有天然瓦斯 |
| four       | 有第四台   |
| broadband  | 有網路     |
| bed        | 床         |
| wardrobe   | 衣櫃       |
| sofa       | 沙發       |

## TODO

- Process of `img` search result
- Process of detail page to structure json info
- GeoData search 
