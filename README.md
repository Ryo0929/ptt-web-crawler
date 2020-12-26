# ptt-web-crawler (PTT 網路版爬蟲-精華區爬蟲)

### [原版本在此](https://github.com/jwlin/ptt-web-crawler)


* 爬取精華區目錄下所有文章
* JSON 格式輸出

輸出 JSON 格式
```
{
    "article_id": 文章 ID,
    "article_title": 文章標題 ,
    "author": 作者,
    "board": 板名,
    "content": 文章內容,
    "date": 發文時間,
    "ip": 發文位址,
    "message_count": { # 推文
        "all": 總數,
        "boo": 噓文數,
        "count": 推文數-噓文數,
        "neutral": → 數,
        "push": 推文數
    },
    "messages": [ # 推文內容
      {
        "push_content": 推文內容,
        "push_ipdatetime": 推文時間及位址,
        "push_tag": 推/噓/→ ,
        "push_userid": 推文者 ID
      },
      ...
      ]
}
```

### 範例

爬取 Marvel 板 精華區 知識區 (https://www.ptt.cc/man/marvel/DDF/index.html)

* 執行jupyter notebook

```commandline
root_url="DDF/index.html"
board="marvel"

article_id_list=get_article_ids(root_url,board)
crawling_data_by_ids(board,article_id_list)
```


Output would be `BOARD_NAME-ID.json`
