---
title: どっかーふぁいるでろけーるを en_US.UTF-8 にする方法(多分)
description: ぷにゃにゃー！
pubDate: 2024-06-02T17:38:50.569097+09:00
importance: 10
---

`locale-gen` に `en_US.UTF-8` 渡すだけでいいっていうのは初めて知った。

``` dockerfile
ENV LANG "en_US.UTF-8"
RUN locale-gen ${LANG}
```

試してみたことはない…。
