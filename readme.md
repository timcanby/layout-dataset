データセットの概要 {#データセットの概要 .ListParagraph}
==================

1 概要
----

### 1.1 データセットの提供元

本データセットは、国立国会図書館デジタルコレクション（以下「デジコレ」という。）&lt;[*http://dl.ndl.go.jp/*](http://dl.ndl.go.jp/)&gt;が提供している資料画像データの中から、「古典籍資料」「明治期以降刊行資料」の2種類を利用する。

アノテーションデータについては当館職員が新規に作成したものを利用する。

### 1.2 データセットの内訳

データセットの内訳は以下のとおり。

                       画像数
  -------------------- ----------
  古典籍資料           約xx画像
  明治期以降刊行資料   約xx画像

### 1.3 データセットの権利

古典籍資料、明治期以降刊行資料ともに著作権保護期間満了資料のみを対象とした。

2 データセットの構成
------------------

### 2.1 データセット

> データセットは画像ごとに以下の2種類を含む。

(1) 資料画像(高精細jpeg画像)

(2) アノテーションデータ(xml形式)

### 2.2 アノテーションデータの形式

Pascal
VOC形式でレイアウトの矩形情報とラベル名を記述したxmlを画像ごとに提供する。1600\*1200サイズの画像から資料全体の含まれる矩形領域を記述した例を以下に挙げる。

  ----------------------------------------------------
  &lt;?xml version="1.0"?&gt;
  
  &lt;annotation&gt;
  
  &lt;folder&gt;kotenseki&lt;/folder&gt;
  
  &lt;filename&gt;3510690\_36&lt;/filename&gt;
  
  &lt;path&gt;kotenseki/3510690\_36.jpg&lt;/path&gt;
  
  &lt;size&gt;
  
  &lt;width&gt;1600&lt;/width&gt;
  
  &lt;height&gt;1200&lt;/height&gt;
  
  &lt;depth&gt;3&lt;/depth&gt;
  
  &lt;/size&gt;
  
  &lt;object&gt;
  
  &lt;name&gt;1\_overall&lt;/name&gt;
  
  &lt;bndbox&gt;
  
  &lt;xmin&gt;300&lt;/xmin&gt;
  
  &lt;ymin&gt;149&lt;/ymin&gt;
  
  &lt;xmax&gt;1299&lt;/xmax&gt;
  
  &lt;ymax&gt;1080&lt;/ymax&gt;
  
  &lt;/bndbox&gt;
  
  &lt;/object&gt;
  
  &lt;/annotation&gt;
  ----------------------------------------------------

同一資料内に複数のレイアウトが存在する場合、xml内にobjectを複数記述することで対応する。

付与されるラベル情報は「古典籍資料」と「明治期以降刊行資料」で異なるため、「3各資料に関する詳細情報」を参照すること。

3 各資料に関する詳細情報
----------------------

### 3.1 古典籍資料について

#### (1) 特徴 {#特徴 .ListParagraph}

明治期より前に出版された出版物であり、浮世絵や和書・漢籍資料が含まれる。また、マイクロ資料を再デジタル化した場合など、強いノイズの乗った資料も存在する。

浮世絵の中に文字が書き込まれているなど、複数のレイアウトの重なりがある場合が多い。

#### (2) 予測対象となるレイアウトのラベル {#予測対象となるレイアウトのラベル .ListParagraph}

  No   ラベル名          説明
  ---- ----------------- --------------------------------------
  1    1\_overall        資料範囲全体
  2    2\_handwritten    草書体（くずし字等）のテキストライン
  3    3\_typography     楷書体・行書体のテキストライン
  4    4\_illustration   イラスト
  5    5\_stamp          印影（蔵書印等）

### 3.2 明治期以降刊行資料について

#### (1) 特徴 {#特徴-1 .ListParagraph}

明治期以降に出版された、冊子の形態をとる出版物である。マイクロ資料をデジタル化した資料など、強いノイズの乗った資料が多く存在する。

多くは昭和前期より前に刊行された資料であるが、一部戦後に刊行された刊行物を含む。

#### (2) 予測対象となるレイアウトのラベル {#予測対象となるレイアウトのラベル-1 .ListParagraph}

  No   ラベル名          説明
  ---- ----------------- ---------------------------------------------
  1    1\_overall        資料範囲全体
  2    4\_illustration   イラスト（写真を含む。）
  3    5\_stamp          印影（蔵書印等）
  4    6\_headline       見出し
  5    7\_caption        図表見出し
  6    8\_textline       6\_headline, 7\_caption以外のテキストライン
  7    9\_table          表

※ラベル名の先頭の数字は両資料で通し番号である。