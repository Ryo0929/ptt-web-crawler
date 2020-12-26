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

* 執行man_crawling.ipynb

```commandline
root_url="DDF/index.html"
board="marvel"

article_id_list=get_article_ids(root_url,board)
crawling_data_by_ids(board,article_id_list)
```

Output include a list of ID txt file and `BOARD_NAME-ID.json` 

### 說明
```
get_article_ids(root_url,board)
```
get_article_ids 會依照目錄階層結構爬取文章的url放入list中，並寫入txt檔案
![image](https://github.com/Ryo0929/ptt-web-crawler/blob/master/800px-Sorted_binary_tree_breadth-first_traversal.png)
```
crawling_data_by_ids(board,article_id_list)
```
crawling_data_by_ids 會去爬取該list中的id，並將結果產出.json檔案
