---
title: あの世がどういうものか
description: ぷにゃにゃー！
pubDate: 2024-06-02T19:20:58.062055+09:00
importance: 10
---

を記述するかもしれないコード:

``` raku
my $amount-of-world = (1..132).pick;

my @reasons         = <別の世界 異界 平行世界>;

say "あの世は {$amount-of-world} つある。あの世とは{@reasons.pick}であり、接している世界の数である。";
```

ある日実行してみた結果:

    あの世は 55 つある。あの世は別の世界であり、接している世界の数である。
