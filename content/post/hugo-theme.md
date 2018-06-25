---
title: "Hugoでアカデミックなポートフォリオサイト兼ブログをつくってみた"
date: 2017-12-20T00:00:00+09:00
---

修士以降の学生で研究に取り組んでいると、自分のプロジェクトやpublicationをまとめたシンプルなウェブページが欲しくなってくる。Wordpressやstrikinglyみたいなサービスが出ているが、オリジナルのWebページを作りたいときには制約が多かったり、機能が多すぎたりすることがある。

HugoはGo言語で記述された、 __スゴイハヤイ静的ウェブジェネレータである。__ 記事やプロジェクトなどを __Markdown記法__ で記述することで投稿したり更新したりできるため、普段mdでノート取ってる方やQiitaの諸兄・諸姉には非常に使い勝手のいいWebジェネレータであると思う。

今回は `Academic` テーマをベースにオリジナルページを作成してみた。

ウェブサイトはこちら : [web](https://jotaros.github.io)


## 使い方（初めての人へ）

https://gohugo.io/getting-started/quick-start/
チュートリアルはここから

- brewでインストール

```sh
brew install hugo
```

- プロジェクトを生成

```sh
hugo new site yourSiteName
```


- テーマを導入

```sh
cd yourSiteName
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke

echo 'theme = "ananke"' >> config.toml
```


ここでは、yourSiteNameプロジェクト内のthemeフォルダに、submoduleとしてテーマプロジェクトを追加している。
テーマプロジェクト内は基本的には生成したプロジェクトと同様の構造となっており、exampleもあるので改造しやすい。
プロジェクトを追加したときに生成されるconfig.tomlを書き換えてテーマをアクティブにする必要がある。



- 記事を投稿

```sh
hugo new posts/my-first-post.md
```

config.tomlに以下の文言を追加して、

```toml
baseURL = "https://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
theme = "ananke"
```

- サイトを生成（ビルド）

```sh
hugo server -D
```


[localhost:1337](localhost:1337)にアクセスすると、生成されたウェブサイトが見れる。たったこれだけでWEBサイトが完成してしまう。


## Academicテーマの改造

インストールは、git submoduleで[Academicテーマ](https://themes.gohugo.io/theme/academic/)を`themes`フォルダに追加すればよい。exampleSiteの投稿（content）ツリーはこのようになっている。

```
├── exampleSite
│   ├── config.toml
│   ├── content
│   │   ├── home
│   │   │   ├── about.md
│   │   │   ├── contact.md
│   │   │   ├── hero.md
│   │   │   ├── posts.md
│   │   │   ├── projects.md
│   │   │   ├── publications.md
│   │   │   ├── publications_selected.md
│   │   │   ├── tags.md
│   │   │   ├── talks.md
│   │   │   └── teaching.md
│   │   ├── post
│   │   │   ├── _index.md
│   │   │   ├── faq.md
│   │   │   ├── getting-started.md
│   │   │   ├── managing-content.md
│   │   │   ├── migrate-from-jekyll.md
│   │   │   ├── widgets.md
│   │   │   └── writing-markdown-latex.md
│   │   ├── project
│   │   │   ├── deep-learning.md
│   │   │   └── example-external-project.md
│   │   ├── publication
│   │   │   ├── _index.md
│   │   │   ├── clothing-search.md
│   │   │   └── person-re-identification.md
│   │   ├── tags
│   │   │   └── academic
│   │   │       └── _index.md
│   │   └── talk
│   │       ├── _index.md
│   │       └── example-talk.md
```

トップページに現れるプロフィール画像や文言などもすべてmd記法で記述することが可能。

### cssでカスタマイズ

元のデザインも十分に良いのだが、自分風にカスタマイズしたい場合は、

1. (theme側ではなく)自分のプロジェクトの `static` フォルダに、 `custom.css` という名前でcssファイルを作成
2. 主に `partials/widjets` などの要素・クラスを見ながら、custom.cssを書きかえ
3. 必要に応じてテンプレートを書き換え（上級者向き）、削除などをする（talkしたことなければ消したりなど）。


このあたりの細かい作業が（Hugo初めてだったので）Hard-Codedになってしまったのは大いに反省なのだが、上に書いてあるフォルダ内のデータをいじれさえすれば、Academicのpostパターンを崩すことなくオリジナルのポートフォリオサイトが作成できる。

作成したウェブサイトがこちら：[web](https://jotaros.github.io)



## まとめ


- HugoはスゴイハヤイstaticWebジェネレータ
- mdで書けるため、普段qiitaにおられる諸兄・諸姉におすすめ
- Academicは研究者・学生向けのテンプレートとして有能
- 他のテンプレートエンジンと同様、partialsをいじってcssを書き換えるなどして簡易にオリジナルデザインに変更できる。





