---
title: hexo algolia运行失败解决,献给所有有缘人
tags: [resolution]
---

被白白坑了挺不舒服的，找遍了全网，英文说明档，英文站，才找到解决方案，故献给有缘人。
<!-- more -->

> 吐槽：按着next的官方文档加上几个个人博客上的内容在更新个人站，到了algolia实现站内搜索这一步，花了大概1个多小时，原因是，官方说明档里漏了需另设一个API key，随后运行hexo algolia报错，提示需要环境变量，set an`HEXO_ALGOLIA_INDEXING_KEY` environment variable,balabala之类的。但是我TM翻了大概5-6个博主，也都没写这一步，难不成，自己也不知道怎么解决，但是写篇文章装出自己会了的样子，假装自己很努力？

正话：
先提一下，之前有一步：
```
algolia:
  applicationID: 'applicationID'
  apiKey: 'apiKey'
  adminApiKey: 'adminApiKey'
  indexName: 'indexName'
  chunkSize: 5000
  ```
  这个的，是复制这段代码到根目录的——config里，而不是文件里本身就包含了的。
  [hexo algolia运行报错解决方案](https://github.com/iissnan/theme-next-docs/issues/162)

## 以下文字和链接中内容相同

实施步骤如下：

	1. 创建APIKeyHEXO_ALGOLIA_INDEXING_KEY

		* 进入Algolia的API Keys页面ALL API KEYS选项卡
		* 创建APIKey

			* Description：HEXO_ALGOLIA_INDEXING_KEY
			* Indices：<此处选择之前创建的Index>
			* ACL：Add records，Delete records，List indices，Delete index
	2. 设置环境变量HEXO_ALGOLIA_INDEXING_KEY
$ export HEXO_ALGOLIA_INDEXING_KEY=<此处为第1步创建的APIKey>（windows百度环境变量添加法，系统变量）
	3. 执行Algolia命令
$ hexo algolia
(node:16231) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
INFO [Algolia] Testing HEXO_ALGOLIA_INDEXING_KEY permissions.
INFO Start processing
INFO [Algolia] Identified 1 posts to index.
INFO [Algolia] Start indexing...
INFO [Algolia] Indexing done.
