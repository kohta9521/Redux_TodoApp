# SimpleHoiku_Hp コーディング規則
Simple株式会社のフロントエンド製作プロジェクトにて適用するコーディング規約をまとめます。

最終更新 : 2023/09/21
**Ver.0.1.0**


## この規約に関して

#### このドキュメントの目的
1. **コード品質の安定**
	- メンバー全員がある一定以上の品質でコーディングできる
1. **コミュニケーションコストの削減**
	- メンバー間の連絡や質問事項を減らす
1. **経験から得られる注意事項の共有**
	- 一度学んだことをメンバー間で共有する
#### 運営に関して
- メンバーは開発をするにあたり、この規約を守る必要がある
    - わからない点ああれば規約製作者及びメンバーに問い合わせる
- この規約はプロジェクトの進行やメンバーのスキルにより変更することが可能である
    - ただし変更を行う場合は全メンバーに変更点とその理由を共有し、また同じ内容を最下部パッチノートに追加する

#### 参考にしているWebページ

- [Markdown記法 チートシート - Qiita](http://qiita.com/Qiita/items/c686397e4a0f4f11683d)
- [ベストなコーディング規約の作り方](http://bonk.red/articles/project/coding_rule.html)
- [経験の浅いチームのためのHTML/CSSコーディング規約 - Qiita](http://qiita.com/WalkerEpps/items/9c9a1098404cd89c0068)
- [Googleが推奨しているHTML/CSSコーディングガイドラインをまとめてみました。 | NIWAKASOFT](http://niwakasoft.jp/column/coding_conventions/)
- [あなたのコーディング、大丈夫？ コーディング規約 HTML＋CSS編 | Web制作会社スタイル](http://www.hp-stylelink.com/news/2013/10/20131001.php)
- [HTML5 で省略できるタグ - Qiita](http://qiita.com/labocho/items/54fd70c73ced35c8ba49)

***

## 全体で共通の規約
#### エンコーディング
ソースコードのエンコードは **UTF-8(BOMなし)** を使用する。

#### インデント
スペースを2つ使う。
> Tabを使いたいという意見はあったが、調べれば調べるほどこちらが一般的だった。  

```html
<!-- 推奨 -->
<ul>
  <li>A
</ul>
```
```scss
/* 推奨 */
.selector {
  color: black;
}
```
> [Sublime Text 3 - インデントの設定（スペース・タブ） - 開発メモ - Webkaru](http://webkaru.net/dev/sublime-text-3-indent/)

#### コメント
規約から外れた書き方をする場合・他メンバーが理解しづらいと考えられる部分にはコメントを残す。

#### 1行1要素
可読性を保持するため1行に書く要素は1つに留める。

```html
<!-- 非推奨 -->
<ul>
  <li>A<li>B
</ul>

<!-- 推奨 -->
<ul>
  <li>A
  <li>B
</ul>
```

#### 大文字/小文字
タグやID、色コードなどの記述はDOCTYPE,キャメルケース使用時を覗いて小文字で行う。

```html
<!-- 非推奨 -->
<A HREF="#">ABC</A>

<!-- 推奨 -->
<a href="#">ABC</a>
```
```css
/* 非推奨 */
.SELECTOR{
  COLOR: #0DAC1A;
}
.MYSELECTOR{
}

/* 推奨 */
.selector{
  color: #0dac1a;
}
.mySelector{
}
```
#### 末尾の空白
動作の乱れが発生する場合があるため、末尾の空白は残さない。

#### プロトコル
http/httpsは両方のプロトコル上で利用できない場合を除き、省略する。

```html
<!-- 非推奨 -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- 推奨 -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

## HTMLコーディング規約

#### バージョン
**HTML5** を使用する。

#### Doctype宣言
必ず宣言する。

```html
<!DOCTYPE html>
```
#### 任意のタグの省略
Googleが推奨しているため採用する。
> [HTML5 で省略できるタグ - Qiita](http://qiita.com/labocho/items/54fd70c73ced35c8ba49)

```html
<!-- 非推奨 -->
<!DOCTYPE html>
<html>
  <head>
    <title>Spending money, spending bytes</title>
  </head>
  <body>
    <p>Sic.</p>
    <ul>
      <li>A</li>
      <li>B</li>
    </ul>
  </body>
</html>

<!-- 推奨 -->
<!DOCTYPE html>
<title>Saving money, saving bytes</title>
<p>Qed.
<ul>
  <li>A
  <li>B
</ul>

```
> li閉じタグは省略しないと予期しないマージンが入ることがある。

#### スタイルシートとスクリプトの属性の省略
typeは自動認識されるため記述しない。

```html
<!-- 非推奨 -->
<link rel="stylesheet" href="style.css"
  type="text/css">
<script src="smoothscroll.js"
  type="text/javascript"></script>

<!-- 推奨 -->
<link rel="stylesheet" href="style.css">
<script src="smoothscroll.js"></script>
```

#### スタイリング
外部CSSファイルを参照する。

```html
<!-- 非推奨 -->
<style type="text/css">
  .helpButton{
    border: 1px solid #999;
  }
</style>

<p style="color: red">
<big>
<center>
<font>
<tt>

<!-- 推奨 -->
<link rel="stylesheet" href="style.css">
```

#### 引用符
ダブルクオーテーションを使用する。

```html
<!-- 非推奨 -->
<a class='sns-button'>Sign in</a>

<!-- 推奨 -->
<a class="sns-button">Sign in</a>
```

#### 閉じないタグ
以下のタグは閉じてはいけない。

> 文法が間違っているため、予期しない問題が発生することがある。

```html
<!-- 推奨 -->
<br>
<hr>
<img>
<link>
<meta>
<input>
```

## CSSコーディング規約

#### プロパティ記述の際のスペース
プロパティ: _ 設定値;のようにスペースを利用する。

```scss
/* 非推奨 */
.nav-bottom{
  color:red;
}

/* 推奨 */
.nav-bottom{
  color: red;
}
```

#### 開きカッコの位置
開きカッコはセレクタと同じ行に置く。

```scss
/* 非推奨 */
.nav-bottom
{
  color: red;
}

/* 推奨 */
.nav-bottom{
  color: red;
}
```

#### 複数セレクタ指定の際の改行
セレクタごとに改行する。

```scss
/* 非推奨 */
.class1, .class2, .class3 {
  color: red;
}

/* 推奨 */
.class1,
.class2,
.class3 {
  color: red;
}
```

#### ルール間の改行
ルールとルールの間には改行を挟む。

```scss
/* 非推奨 */
.class1{
  color: red;
}
.class2{
  color: blue;
}

/* 推奨 */
.class1{
  color: red;
}

.class2{
  color: blue;
}
```

#### コメントアウトの記法
コメントアウトは、タグと文章の間にスペースを入れる。  
複数行に至る場合、タグと同じ行に文章を入れない。

```scss
/*非推奨*/
/*非
推
奨*/

/* 推奨 */
/*
推奨
 */
```

#### セレクタに使用する要素
出来る限り タグ、idをセレクタに使用しない。

#### 小数点数値の表記
小数点の数値0は省略する。

```scss
/* 非推奨 */
opacity: 0.8;

/* 推奨 */
opacity: .8;
```

#### プロパティの宣言順序
プロパティの宣言はアルファベット順に行う。

```scss
boader: 1px;
color: red;
margin: 10px;
padding:5px;
```

#### !importantの使用
!importantは**いかなる理由があっても使用しない。**  
使用する必要を感じた際は設計から見直す。

### id,classの命名定義
BEMにおけるBlock, Element, Modifierを次のように繋いで使用する。  
BEMに関する解説は下記参照。

```scss
.Block_Element-State
.Block_Element
.Block-State
```

グローバルな設定はBlockを「g」として記述する。

```scss
.g_Element
.g-State
```

長い名前に関してはキャメルケースを使用する。

```scss
.rightMenu
```

スタイルを示す命名は避ける。

```scss
/* 非推奨 */
.mb50
.red
```

#### BEMについて
CSS設計手法の一つ。  
拡張、再利用しやすいネーミングが特徴。


#### 考え方
以下の3つの形で捉える。

- Block（塊）
- Element（要素）
- Modifier（状態）

##### Block
コンテンツを含む大きな塊。

##### Element
Block内の要素。  
「 _ 」で繋ぐ。

##### Modifier
エレメントまたはブロックの状態。  
「 - 」で繋ぐ。

#### SCSSの利用
コーディングはSCSSで行い、HTMLではコンパイル後のCSSを読み込む。  
HTMLで読み込むCSSの数は極力少なくなるよう留意する。  

#### SCSSコンパイラ設定
アウトプットスタイルはexpandedを使用する。
> おすすめのコンパイラ：[フリーのSass,LessコンパイラKoala【Win,Mac】 | Sou-Lablog](http://blog.sou-lab.com/koala/)

#### カラーコード、フォントサイズの変数化
テーマ変更などに対応するため、カラーコード・フォントサイズは変数に置く。

```scss
$g-bgc: #ffffff;

background-color: $g-bgc;
```


### SCSS設計
基本的には[SMACSS](https://smacss.com/)を採用する。  

#### SMACSSについて
SCSS設計の一つ。  
今回はSCSSのファイル分割の基準として採用する。

#### 考え方
以下の4つの形で捉える。

- Base
- Layout
- Module
- State

> 本来であればThemeが5つ目として存在するが、今回は必要ないため省く。

##### Base
全体に共通する各要素のデフォルト値（背景色・文字色・フォントなど）を設定する。  
基本のリセットスタイルには[sanitize.css](http://coliss.com/articles/build-websites/operation/css/about-sanitize-css.html)を利用する。  
セレクタにタグ、idを使用してもよい。  
ただし、widthやmargin, paddingなどを設定しない。

##### Layout
おおまかなレイアウトを設定する。  
BEMでのBlockに対応する。  
セレクタにidを使用してもよい。  
場所に依存するセレクタにはならないよう留意する。

##### Module
レイアウトパターンに含まれるほぼすべての要素を示す。  
BEMでのElementに対応する。  
ボタンや見出し、リンクなど再利用されるオブジェクト全てを示す。

##### State
Moduleに対して状態変化をもたせる際に利用する。  
BEMでのModifierに対応する。  
Javascriptなどで要素に変化をもたせる場合などで利用する。

## ファイル構造

## 免責事項

app ディレクトリ以下の配置方法のみ選定  
components の分け方は別途  
2023/9/20

## Next.js ver 12

Next.js は react-router-dom の煩わしさを解決するために*ファイルシステムベースのルーティング*をサポートしている  
Next12 までは Pages ディレクト配下が自動でルートとして使用可能な仕様だった これを`Pages Router`と呼ぶ

以下に Pages Router の基本的な例を示す  
見てわかる通りファイル名と routing が一致している `_app.tsxやdocument.tsx`は本題と逸れるため除外している

```shell
src/
  pages/
    - index.tsx # "/"
    - about.tsx # "/about"
    work/
      - index.tsx # "/work"
      - [id].tsx # "/work/1"
```

---

## Next.js ver 13

最新の Next13 では Pages Router の代わりとして`App Router`が正式採用されている  
現在の公式ドキュメントでは App Router と Pages Router の両方が掲載されている  
今後は App Router を基本とするため、App Router を選択してドキュメントを読むようにする  
また Pages Router と App Router の知識が自信の頭で混ざり、混同することに気を付ける必要がある

以下は Pages Router と比較した App Router の変更点である  
1 app/配下に作成する必要がある  
2 ファイル名でのルーティングが不可となり`[ディレクトリ]/page.tsx`で Routing する必要がある  
3 app ディレクトリ以下に Routing に関係のないファイル(Components など)をおいても良い  
4 layout.tsx を筆頭に、ファイル名に従って特定の役割を果たすファイルが追加された

以下に App Router の基本的な例を示す  
root ページ以外は基本的に`ディレクトリ名/page.tsx`で構成する必要がある点に注目して欲しい

```shell
src/
  app/
    - page.tsx
    - layout.tsx
    about/
      - page.tsx
      - layout.tsx
    work/
      - page.tsx
```

## Route Group の設定

App Router は Routing に影響を与えないディレクトリを作成することが可能である  
先にも述べたように App Router は app/に routing に関係ないファイルを作成することが可能である

例を下記に示す

```shell
src/
  app/
    - page.tsx
    - layout.tsx
    compontns/
    helper/
    work/
      - page.tsx # "/work"
```

ここで懸念される問題は app/配下のディレクトリが routing 用ディレクトリとその他のディレクトリが混ざり合い見通しが悪くなる点である  
この問題を解決するために、Routing に関連する`ディレクトリ/ファイル`を Pages ディレクトリのようなものでまとめるという解決策がある  
個人的には Next12 の Pages ディレクトリへの回帰を思わせるこの手法は好みじゃないが以下に例を示す

```shell
src/
  app/
    - page.tsx
    - layout.tsx
    components/
    helper/
    pages/
      work/
        - page.tsx # "/pages/work"
        - layouot.tsx
      about/
        - page.tsx # "/pages/about"
```

上記の問題は全ての Routing の PATH に pages が含まれる点である。  
この問題を解決するために*Route Group*を使用する  
下記のように()で囲むことで routing の PATH に影響を与えることなくファイルを分けることが可能である

```shell
app/
  (pages)
    work/
      - page.tsx # "/work"
```

しかしながら、pages ディレクトリの中で`/about, /work, /contact`等ディレクトリを切らなければいけないのは変わらない点に覚えておいて欲しい

ここで断言しておきたいが、page.tsx というファイル名の制限から逃れるために  
react-router-dom を使って routing するのは react の複雑性への回帰であり悪手であるのはいうまでもない  
これを示唆する記事があるとかではなく、Next.js が解決した問題に回帰する選択肢が悪手であるということは議論の余地もないだろう  
Next.js 誕生の歴史的な背景を無視するのであれば素直に React を使うべきだ  
ちなみにこの主張を覆す著名な Next.js ver13 の実装例があればこっそり教えて欲しい

そもそも動くのかはテストしていない(おそらく動く)  
よって下記のような routing 方法は非推奨である

---

_ディレクトリ構成_

```shell
app/
  - page.tsx
  - layout.tsx
  pages
    - Index.tsx
    - About.tsx
    - Contact.tsx
```

_page.tsx_

```js
<BrowserRouter>
  <Routes>
    <Route path={'/'} element={<Index />} />
    <Route path={'/about'} element={<About />} />
    <Route path={'/contact'} element={<About />} />
  </Routes>
</BrowserRouter>
```

pageExtensions を使用して、routing する方法もあるが、next.js が決めた仕様を外れてまで採用するメリットがあるのかは疑問が残る  
新たに参画した人材を混乱させることにも繋がる

---

## ディレクトリ構成まとめ

以上のことを踏まえると Routing を考慮したディレクトリ構成は下記のような２通りの案が思いつく  
どちらを選んでも Next.js ver13 の仕様に従い Routing を行うため `ディレクトリ名/ファイル名`という構成が含まれるのは変わらない

案 1 は app ディレクトを routing 専用のディレクトリとして使用している  
案 2 は routing 以外のファイルも app ディレクトリの中に格納している

ここで注目すべきは src ディレクトリの存在である。  
案 1 は src ディレクトリの直近の配下に components や app など複数のディレクトリが存在する。  
案 2 は src/ディレクトの直近の配下には app しか存在しない  
src ディレクトリは使用するかしないかを決めることができるが、案 2 の運用では src ディレクトリを切る意味が無いとも言える  
`srcディレクトリを使用するのであれば、appディレクトリに全てのコードを詰め込むのではなく、複数のディレクトリで役割分担した方が視認性があがるため、案１を採用した方が良いように思える`

_Next.js が src ディレクトリをサポートしている理由はアプリケーションコードが、プロジェクトのルートに存在するプロジェクト構成ファイルから分離されるから (公式)_

因みに src ディレクトリ使用の可否は create-next-app を使用した際にインタラクティブに聞かれる  
create-next-app は Next.js 開発元の Vercel が開発・メンテナンスをしている  
_案 1_

```shell
src/
  components/
  app/
    - page.tsx
    - layout.tsx
    work/
      - page.tsx
      - layout.tsx
    about/
      - page.tsx
```

_案 2_

```shell
src/
  app/
    - page.tsx
    - layout.tsx
    components/
    (pages)
      work/
        - page.tsx
        - layout.tsx
      about/
        - page.tsx
```

## 想定される反対意見

`App Router`は`Pages Router`と違って routing 以外のページを置くことができるが、routing だけのために使用するのは Next.js の思想に逆行しているという主張

このような意見に対しては下記の見解を示しておく  
app router は src ディレクトリを用いずに使用することができる  
このような運用では、案 2 の実用性も見えてくる  
しかし、src ディレクトリを使用する場合は案 1 ほうが見通しがよくなる  
`App Router`は routine のみを格納する運用も、他のコード(Components 等)を一緒に置く運用も両方サポートされていると考えることができる  
そもそも Next.js の公式ドキュメントで app ディレクトリを routing 専用に使用するディレクトリ構成例が示されている

## ディレクトリ構成結論

今回は src ディレクトリ, App Router を使用している  
Routine 関連と他のコードを同一階層に配置すると、見通しが悪くなる問題に対応したい  
これらを加味し案 1 の下記構成を採用する

```shell
src/
  components/
  app/
    - page.tsx
    - layout.tsx
    work/
      - page.tsx
      - layout.tsx
    about/
      - page.tsx
```

## Vercel 社の教え

※ 公式ドキュメントより抜粋  
Next.js プロジェクトで独自のファイルやフォルダーを整理する場合、「正しい」方法も「間違った」方法もありません。  
最も簡単なポイントは、あなたとあなたのチームにとって効果的で、プロジェクト全体で一貫性のある戦略を選択することです。

## 参考資料

[公式 Documents](https://nextjs.org/docs)



***

## パッチノート（更新履歴）

##### Ver.0.1.0
このドキュメントに関する情報をまとめた

***

#### このドキュメントの規約（ただのロマン）
#####文末
「。」はつける。  
箇条書き、パッチノートではつけない。

##### バージョン値について
###### Ver1.0.0以前（Ver1.0.0公開と同時に削除）
- 以下の変更を行った場合、該当する値だけVer.0.b.cのb+する
	- [x] このドキュメントに関する情報をまとめる: 1
	- [x] 共通の規約をまとめる: 2
	- [x] HTMLに関する規約をまとめる: 2
	- [x] CSS に関する規約をまとめる: 2
	- [ ] JS  に関する規約をまとめる: 2
	- [ ] PHP,その他に関する規約をまとめる: 1
- 一度コミットしたものに変更を加えた場合、Ver.0.b.cのcを+1する

###### Ver1.0.0以降
- 変更・追記は全て別ブランチ制作/Pull Requestによるマージを行う
− 変更を行った場合、Ver.a.b.cのbを+1する
- 追記を行った場合、Ver.a.b.cのcを+1する
- Ver.a.b.cのaはこのドキュメントの最終更新年度（西暦下二桁）-15とする

