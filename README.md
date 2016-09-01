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
result = r.search()
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
