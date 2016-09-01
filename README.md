# python-five91

A simple [591.com.tw](www.591.com.tw) wrapper.

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

- `region`: integer, default is `1`, please reference "Region code table".
- `kind`: integer, can be skipped, please reference "Kind code table".
- `section`: integer, can be skipped, please reference "Section code table".
- `rentprice`: integer, default is `0`, its the range of rent price, please reference "Rent price table".
- `pattern`: integer, means "格局" in chinese, please reference "Pattern code table".
- `first_row`: pagination related, please see "Pagination".
- `total_rows`: pagination related, please see "Pagination".

## Pagination

(under construction)

## Code Tables

### Region code table

(under construction)

### Kind code table

(under construction)

### Rent price table

(under construction)

### Pattern code table

(under construction)
