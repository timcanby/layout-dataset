データセットの概要
==================
このデータセットは以下のURLから公開している<br/>
古典籍資料：https://lab.ndl.go.jp/dataset/dataset_kotenseki.zip

明治以降刊行資料:https://lab.ndl.go.jp/dataset/dataset_kindai.zip


1.概要
----

### 1.1 データセットの提供元

本データセットは、国立国会図書館デジタルコレクション（以下「デジコレ」という。）&lt;[*http://dl.ndl.go.jp/*](http://dl.ndl.go.jp/)&gt;が提供している資料画像データの中から、「古典籍資料」「明治期以降刊行資料」の2種類を公開している。

アノテーションデータについては当館職員が新規に作成したものを公開している。

### 1.2 データセットの内訳

データセットの内訳は以下のとおり。

  |資料の種類                   | 画像数
  |-------------------|----------
  |古典籍資料 (https://lab.ndl.go.jp/dataset/dataset_kotenseki.zip)          |約1200画像
  |明治期以降刊行資料(https://lab.ndl.go.jp/dataset/dataset_kindai.zip)    |約800画像

### 1.3 データセットの権利

古典籍資料、明治期以降刊行資料ともに著作権保護期間満了資料のみを対象とした。

2 データセットの説明
------------------

### 2.1 データセットの構成

データセットは画像ごとに以下の2種類を含む。

(1) 資料画像(高精細jpeg画像)

(2) アノテーションデータ(xml形式)

**ディレクトリ命名規則**

variousを除く各ディレクトリ名は資料のPID(Persistent Identifier)を意味し、例えば2534020であれば

http://dl.ndl.go.jp/info:ndljp/pid/2534020

とすることで当該資料のデジコレ上のURLとしてアクセスできる。

**ファイル命名規則**

(PID)_(コマ番号)
となっている。
例えば2534020_3は、http://dl.ndl.go.jp/info:ndljp/pid/2534020
のコマ番号3にある。

**PIDと資料名の対応表**

デジコレの書誌データは以下から提供している。

https://www.ndl.go.jp/jp/dlib/standards/opendataset/index.html

各メタデータは以下から、

http://dl.ndl.go.jp/files/dataset/dataset_201907_k_internet.zip


http://dl.ndl.go.jp/files/dataset/dataset_201907_t_internet.zip

それぞれダウンロード可能である。


### 2.2 アノテーションデータの形式

Pascal
VOC形式でレイアウトの矩形情報とラベル名を記述したxmlを画像ごとに提供する。1600\*1200サイズの画像から資料全体の含まれる矩形領域を記述した例を以下に挙げる。

```xml
<?xml version="1.0"?>
<annotation>
  <folder>kotenseki</folder>
  <filename>3510690_36</filename>
  <path>kotenseki/3510690/3510690_36.jpg</path>
  <source>
    <database>NDLDocL</database>
  </source>
  <size>
    <width>1600</width>
    <height>1200</height>
  </size>
  <segmented>0</segmented>
  <object>
    <name>1_overall</name>
    <bndbox>
      <xmin>300</xmin>
      <ymin>149</ymin>
      <xmax>1299</xmax>
      <ymax>1080</ymax>
    </bndbox>
  </object>
</annotation>
```

同一資料内に複数のレイアウトが存在する場合、xml内にobjectを複数記述することで対応する。

付与されるラベル情報は「古典籍資料」と「明治期以降刊行資料」で異なるため、「3各資料に関する詳細情報」を参照すること。

3 各資料に関する詳細情報
----------------------

### 3.1 古典籍資料について

#### (1) 特徴

明治期より前に出版された出版物であり、浮世絵や和書・漢籍資料が含まれる。また、マイクロ資料を再デジタル化した場合など、強いノイズの乗った資料も存在する。

浮世絵の中に文字が書き込まれているなど、複数のレイアウトの重なりがある場合が多い。

#### (2) 予測対象となるレイアウトのラベル

  |No  | ラベル名          |説明
  |----| -----------------| --------------------------------------
  |1   | 1\_overall       | 資料範囲全体
  |2   | 2\_handwritten   | 草書体（くずし字等）のテキストライン
  |3   | 3\_typography    | 楷書体・行書体のテキストライン
  |4   | 4\_illustration  | イラスト
  |5   | 5\_stamp         | 印影（蔵書印等）

### 3.2 明治期以降刊行資料について

#### (1) 特徴
明治期以降に出版された、冊子の形態をとる出版物である。マイクロ資料をデジタル化した資料など、強いノイズの乗った資料が多く存在する。

多くは昭和前期より前に刊行された資料であるが、一部戦後に刊行された刊行物を含む。

#### (2) 予測対象となるレイアウトのラベル

  |No   |ラベル名          |説明
  |---- |-----------------| ---------------------------------------------
  |1    |1\_overall       | 資料範囲全体
  |2    |4\_illustration  | イラスト（写真を含む。）
  |3    |5\_stamp         | 印影（蔵書印等）
  |4    |6\_headline      | 見出し
  |5    |7\_caption       | 図表見出し
  |6    |8\_textline      | 6\_headline, 7\_caption以外のテキストライン
  |7    |9\_table         | 表

※ラベル名の先頭の数字は両資料で通し番号である。
