## github 運用メモ
::ProjectName= Star Region (master)  
::github= https://github.com/lucida3rd/skill_memo  
::Admin= Lucida（twitter: @lucida3rd）  
::Twitter URL= https://twitter.com/lucida3rd  
::Homepage=  https://lucida3web.wixsite.com/prof  
::Message= https://marshmallow-qa.com/lucida3poi  


<a id="iRet"></a>
## 目次
* [よく使うコマンド](#iFrequentlyUseCommands)
* [githubへのpush](#iGithubPush)
* [Pull Request手順](#iGithubPullRequest)

* [githubへのサインイン](#iGithubSignin)
* [cloneしたリモートを元に戻す(#iRestoreClonedRemote)
* [githubマークダウン書式（確認）](#iMarkdownFormat)

* [免責事項](#iDisclaimer)




<a id="iFrequentlyUseCommands"></a>
## よく使うコマンド

ブランチを消す
```
$ git branch -d [ブランチ名]
```
  

リモートが自分のリポジトリかを確認する。
```
$ git remote -v
origin  https://github.com/[自分のリポジトリ名].git (fetch)
origin  https://github.com/[自分のリポジトリ名].git (push)
```
  

ローカルリポジトリの状態を表示する(変更ありとか)
```
$ git status
```
  

ローカルリポジトリとリモートリポジトリの変更差分を表示する
```
$ git diff
```
  

コミットの確認(最新から10件まで)
```
$ git log -n 10
```
  




<a id="iGithubPush"></a>
## githubへのpush（タグ管理）

1.ブランチを切り替える場合
```
$ git branch
(現在のブランチ表示)

$ git branch [新しいブランチ名]
$ git checkout [ブランチ名]
(切り替え先のブランチ表示)
```
  

2.ローカルリポジトリの状態確認
```
$ git remote -v
$ git branch
$ git status
$ git diff
```
  

3.ファイルの追加、変更、削除をする
```
ファイルの追加
$ git add [ファイル名]

ファイルの削除
$ git rm [ファイル名]

ファイル名変更
$ git mv [変更元ファイル名] [変更先ファイル名]
```
この操作をしたあとコミットしないと、当然masterには反映されない  
  

4.コミットする+タグ付き
```
$ git tag -a [タグ] -m "(コメント)'
$ git tag
```
  
あるいは、タグなしコミット（-aは更新したファイル全てコミット）
```
$ git commit -a -m "(コメント)"
```
  
コミットに後からタグをつける場合
```
$ git log -n 10
$ git tag -a [タグ] -m "(コメント)" [コミット名]
```
  

5.githubへプッシュ
```
$ git push origin [タグ]
```
  
タグなしの場合はブランチを共有する
```
$ git push origin [ブランチ名]
```
  




<a id="iGithubPullRequest"></a>
## Pull Request手順

1.ブランチを切り替える
```
$ git branch
(現在のブランチ表示)

$ git branch [作業用ブランチ名]
$ git checkout [作業用ブランチ名]
(切り替え先のブランチ表示)
```
  

2.コミットする
```
$ git commit -a -m "(コメント)"
```
  

3.リモートの変更を取り込む
```
$ git fetch
$ git rebase [リモートのmasterリポジトリ名]
  
ここで競合した場合は再編集してpushすること
$ git push origin [作業用ブランチ名]
```
  

4.githubのwebページ上でpull requestを作成する  

5.masterに反映する
```
$ git fetch
$ git merge [リモートのmasterブランチ名]

競合があれば解消してコミットする
$ git tag -a [タグ] -m "(コメント)" [コミット名]
$ git push origin [作業用ブランチ名]
```
  
作業用ブランチの変更を、masterに反映する
```
$ git fetch
$ git rebase origin/[作業用ブランチ名]
```
  

6.ローカルを更新する
```
$ git checkout [masterブランチ名]
$ git pull
$ git fetch
$ git rebase [リモートのmasterリポジトリ名]
```
  




<a id="iGithubSignin"></a>
## githubへのサインイン（初回のみ？）
push時にgithubへのサインインが求められることがある。  
その場合、アクセストークンを作ることでサインインできる。  
  
1.githubにログインする。  
  
2.setting→deveroper setting→Personal access tokensにアクセス。  
  
3.generate new tokenをクリック  
  
4.repo、admin:repo_hook、delete_repoをチェック  
  
5.tokenをクリックする。  
  
6.トークンをコピーしたものでサインインする。  
  




<a id="iRestoreClonedRemote"></a>
## cloneしたリモートを元に戻す
```
$ git remote -v
$ git remote rm origin
$ git remote add origin git@github.com:[githubの自リポジトリ名]
$ git remote -v
```
  




<a id="iLabels"></a>
## ラベル運用
githubのデフォルトのラベルの意味。  

| Label | 説明 |
----|---- 
| bug | 予期しない問題または意図しない動作を示す |
| documentation | ドキュメンテーションに改善や追加が必要であることを示す |
| duplicate | 同様の Issue あるいはプルリクエストを示す |
| enhancement | 新しい機能のリクエストを示す |
| good first issue | 初回のコントリビューターに適した Issue を示す |
| help wanted | メンテナーが Issue もしくはプルリクエストに助けを求めていることを示す |
| invalid | Issue あるいはプルリクエストに関連性がなくなったことを示す |
| question | Issue あるいはプルリクエストにさらなる情報が必要なことを示す |
| wontfix | Issue あるいはプルリクエストの作業が継続されないことを示す {




<a id="iMarkdownFormat"></a>
## githubマークダウン書式（確認）

**＜見出し＞**  

# 見出し1
## 見出し2
### 見出し3
#### 見出し4
##### 見出し5
###### 見出し6
  
  

**＜Block 段落＞**  
空白行を挟む  
  
段落1
  
段落2
  
```
段落1
(空行)
段落2
```
  
  

**＜Br 改行＞**  
改行の前に半角スペース を2つ記述  
  
hoge fuga  
(↑↑↑スペース2つ↑↑↑)  
piyo
  
```
hoge fuga  
(↑↑↑スペース2つ↑↑↑)  
piyo
```
  
  

**＜Blockquotes 引用＞**  
先頭に>を記述。ネストは>を多重に記述  
  
> 引用  
> 引用
>> 多重引用
  
```
> 引用
> 引用
>> 多重引用
```
  
  

**＜Code コード＞**  
`バッククオート` 3つ、あるいはダッシュ~３つで囲む  
  
```

code's

```
  
  

**＜インラインコード＞**  
`バッククオート` で単語を囲むとインラインコードになる  
  
これは`インラインコード`だ  
  
  

**＜pre 整形済みテキスト＞**  
半角スペース4個もしくはタブで、コードブロックをpre表示  
  
    class Hoge
        def hoge
            print 'hoge'
        end
    end
  
```
    class Hoge
        def hoge
            print 'hoge'
        end
    end
```
  
  

**＜Hr 水平線＞**  
アンダースコア_ 、アスタリスク*、ハイフン-などを3つ以上連続して記述  
  
hoge
***
hoge
___
hoge
---
  
```
hoge
***
hoge
___
hoge
---
```
  
  

**＜Ul 箇条書きリスト＞**  
ハイフン-、プラス+、アスタリスク*のいずれかを先頭に記述  
ネストはタブで表現  
  
- リスト1
	- リスト1_1
		- リスト1_1_1
		- リスト1_1_2
	- リスト1_2
- リスト2
- リスト3
  
```
- リスト1
    - リスト1_1
        - リスト1_1_1
        - リスト1_1_2
    - リスト1_2
- リスト2
- リスト3
```
  
  

**＜Ol 番号付きリスト＞**  
番号.を先頭に記述  
ネストはタブで表現  
  
1. 番号付きリスト1
	1. 番号付きリスト1-1
	1. 番号付きリスト1-2
1. 番号付きリスト2
1. 番号付きリスト3
  
```
1. 番号付きリスト1
    1. 番号付きリスト1-1
    1. 番号付きリスト1-2
1. 番号付きリスト2
1. 番号付きリスト3
```
  
  

**＜強調＞**  
アスタリスク*もしくはアンダースコア_1個で文字列を囲む  
  
これは *イタリック* です  
これは _イタリック_ です  
  
```
これは *イタリック* です
これは _イタリック_ です
```
  
アスタリスク*もしくはアンダースコア_2個で文字列を囲む  
  
これは **ボールド** です  
これは __ボールド__ です  
  
```
これは **ボールド** です
これは __ボールド__ です
```

アスタリスク*もしくはアンダースコア_3個で文字列を囲む  
  
これは ***イタリック＆ボールド*** です  
これは ___イタリック＆ボールド___ です  
  
```
これは ***イタリック＆ボールド*** です
これは ___イタリック＆ボールド___ です
```
  
  

**＜Link リンク＞**  
[表示文字](URL)でリンクに変換 
  
[Google](https://www.google.co.jp/)
  
```
[Google](https://www.google.co.jp/)
```
  
  

**＜外部参照リンク＞**  
URLが長くて読みづらくなる場合や同じリンクを何度も使用する場合は、リンク先への参照を定義できる 

[yahoo]: http://www.yahoo.co.jp "yahoo desu"
[yahoo japan][]


```
[Googleを見る][Google]
[Google]: http://www.yahoo.co.jp
```
  
  

**＜Images 画像＞**  
先頭の!で画像のと認識  
画像の大きさなどの指定をする場合はimgタグを使用  
  
```
![alt](画像URL)
![代替文字列](URL "タイトル")
```
  
  

**＜Table 表＞**  
  
| TH1 | TH2 |
----|---- 
| TD1 | TD3 |
| TD2 | TD4 |
  
```
| TH1 | TH2 |
----|---- 
| TD1 | TD3 |
| TD2 | TD4 |
```
  
  




<a id="iDisclaimer"></a>
## 免責事項
* アーカイブなどに含まれるファイル類は消したりしないでください。誤動作の原因となります。
* 当ソースの改造、改造物の配布は自由にやってください。その際の著作権は放棄しません。
* 未改造物の再配布は禁止とします。
* 当ソースを使用したことによる不具合、損害について当方は責任を持ちません。全て自己責任でお願いします。
* 当ソースの仕様、不具合についての質問は受け付けません。自己解析、自己対応でお願いします。
* 使用の許諾、謝辞については不要です。
* その他、ご意見、ご要望については、Twitterに記載してある"マシュマロ"までお送りください。






--------------------------------------------------------------

$ git fetch --tags origin
$ git merge [自ブランチ名]  ※いるのか？？？



2.gitから最新のリポジトリを引っ張り、タグを表示する。
$ git fetch --tags

3.ローカルを退避して、ブランチを切り替えたあと、退避を戻す。
提供されている最新バージョンがv1.6.1として、
v1.6.0からv1.6.1へのバージョンアップを行う仮定で手順を記載。
$ git status           //ローカルリポジトリの内容を確認する
$ git stash save       //変更を一時退避する
$ git checkout v1.6.1  //ブランチをv1.6.1に切り替える
$ git stash pop        //退避を戻して、退避を消す
$ git branch           //ブランチの一覧を表示する




