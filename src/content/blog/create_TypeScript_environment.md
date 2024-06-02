---
title: TypeScript の環境を作る
description: TypeScript の環境構築をしたさがあるが、環境構築とはいったい…？
pubDate: 2024-06-02 16:08:29.521540800 +0900
---

TypeScript の環境を作ってみよう。  
とりあえず、現在の `node` と `npm` のバージョンを表示してみる:

    $ node --version
    v22.2.0
    
    $ npm --version
    10.4.0

私は Windows 11 で MSYS2 上の MSYS bash でいろんなことをするのが好きだが、NodeJS は Scoop でインストールしている。

## 環境構築とは…？

とりあえず、あなたが TypeScript を学びたいが環境構築が難しいと思っているとしよう。

そもそも、環境ってなんなんだ…？  
TypeScript の環境構築って何をやれば良いんだろうね。  
`typescript` をインストールするだけじゃダメなんだろうか？

わからない。

## 実行できればいい場合

`tsc` で `*.ts` ファイルを `*.js` ファイルに変換したいとか、実行したいだけなら以下のように打てば良い:

    $ npm install -g typescript

そうすると、`tsc` コマンドが使えるようになるはずだ。

グローバルに NPM でインストールできるコマンドをいんすとーるするのはうんぬんかんぬんということをブログのエントリに書いている人がいるが、
実のところ、好みの問題であって、ほにゃほにゃさんがこう言ってるからと、必ずコードを試すためにプロジェクトを毎回作って

    $ npm install --save-dev typescript

とやらなきゃいけないというわけではない。  
TypeScript を学んでいると、1 ファイルにちょいちょい書いて実行するといったことをした方が理解しやすいはずだ。  
私がそうだっただけで、他の人がどうかはわからないが。

1 ファイルに TypeScript コードを書いてトランスパイル(`tsc`)からの実行(`node`)がめんどくさいというのは本当にそうである。

あるいは、Deno を使うと TypeScript をそのまま実行できる。  
Deno も Scoop でインストールしているので、以下のようなへろーわーるどなコードを

``` typescript
console.log('Hello, World!');
```

例えば `hello.ts` というファイルに保存したものを Deno で実行したい場合は以下のように打つ:

    $ deno run ./hello.ts
    Hello, World!

Deno のバージョンはこんな感じ:

    $ deno --version
    deno 1.44.0 (release, x86_64-pc-windows-msvc)
    v8 12.6.228.3
    typescript 5.4.5

Deno に似たやつとして、Bun というのもあった気がするけれどもそっちの方はやったことがない。

## 新しく TypeScript を使ったプロジェクトを作りたい場合

例えば、`hogepiyo` というディレクトリに `*.ts` ファイルを置いて実行したい場合:

    $ mkdir ./hogepiyo
    $ cd ./hogepiyo

上でもやった通り、以下のように打つと開発ほにゃららで `typescript` が `./hogepiyo` にインストールされる。

    $ npm install --save-dev typescript

すると、以下のような `package.json` が作成される。

    $ cat ./package.json
    {
      "devDependencies": {
        "typescript": "^5.4.5"
      }
    }

それで上でも書いたようなへろーわーるどな TypeScript コードを `main.ts` に書き込む。

    $ cat ./main.ts
    console.log('Hello, World!');

`npx` を前につけて、`main.ts` をトランスパイルしてみよう:

    $ npx tsc ./main.ts

`ls` で JavaScript ファイルを見てみると、あった。

    $ ls ./main.js
    ./main.js

さて、`main.ts` と `main.js` の内容は同じである。  
これはコードの内容を考えるのがめんどかったためで、他意はない。

実行してみると:

    $ node ./main.js
    Hello, World!

へろーわーるどが出力された。

## まとめ

Deno った方がはやい。
