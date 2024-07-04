# [The Art of Readable Code](https://mcusoft.files.wordpress.com/2015/04/the-art-of-readable-code.pdf)

## 読みやすさの基本定理/鍵となる考え
```
    コードは他の人(未来の自分含む)が最短時間で理解できるように書かなければならない
```

## 命名
名前は短いコメントと考えてみる。
```
    明確な単語を選ぶ
    tmpなど汎用的な名前を避ける(特別な場合を除く)
    具体的な命名で物事を詳細に説明する
    変数名に適切な情報を追加する(ミリ秒なら末尾に_msなど)
    スコープの大きな変数には長い名前をつける
    文字列やアンダースコア自体に意味を持たせる(メンバー変数には末尾に"_"をつけるなど)
```

## 美しさ
```
    読み手が慣れているパターンと一貫性のあるレイアウトを使う
    複数のコードブロックで同じようなことをする(似ているコード)なら見た目も似せる
    コードの「列」の整理
    縦の線を視覚的な手すりにする
    定義の順番,処理の順番を揃える
    空行を使いコードが何をしているかで分ける
    一貫性 > 正しさ
```

## コメント
`優れたコード > ひどいコード + 優れたコメント`

### 何を書くべきか
```
    コードを理解するのに役立つのなら何を書いてもいい
    宣言の宣言になってしまうコメントや、"すぐ"わかる処理のコメントは要らない
    自分の考え、頭の中で考えていたことをコメントに記録する
    コードの欠陥にコメントをつける
    なぜこの実装になっているのかコメントする
    ファイルやクラスには「全体像」のコメントをする
```
| 記法   | 意味                   |
| ------ | ---------------------- |
| TODO:  | 後で手をつける         |
| FIXME: | 既知の不具合           |
| HACK:  | 綺麗ではない解決策     |
| XXX:   | 大きな問題を含んでいる |

### どうすれば正確に簡潔に書けるのか
```
    代名詞「それ」「これ」は避ける
    関数はできるだけ正確に例などを交えて説明する
    コードの意図を高レベルで説明する(なぜその処理をしているのか)
    情報密度の高い単語を使う
```

## 制御フロー
```
    条件式は左辺が調査対象の式(変化する)で右辺が比較対象の式(あまり変化しない)
    つまり、より安定した値を右辺に置く
```
```python
    if(length > 10)
```
`条件式はなるべく肯定形を先に処理`
```python
    if(a == b):
        ...
    else:
        ...
```
```
    ただエラーログ等先に注目すべきものがある場合は否定形の条件式を持っても良い
    ガード節の実装
    早めに返してネストを削除する
    複雑な3項演算子を作らない
```

## 巨大な式の分割
### 説明変数を用意する
bad
```python
    if line.split(':').strip() == 'root':
        処理...
```
good
```python
    username = line.split(':').strip()
    if username == 'root':
        処理...
```

### ド・モルガンの法則を使う
bad
```python
    if (not(a and not b)):
```
good
```python
    if(not a or b):
```

## 変数
### 変数がいらないとき
- 複雑な式を分割していないとき
- 明確になっていない
- 一度しか使っていないので重複コードの削除になっていない

```
    中間結果を保持する変数はなるべく使わず、早くreturnすることで解決する(タスクはできるだけ早く完了したほうが良い。)
    制御フロー変数を使わない
    スコープはなるべく小さくする(一度に考えなければならない変数をなるべく減らす)
    クラスのメンバ変数は"ミニグローバル変数"
    定数を使う
```

## 無関係の下位問題を抽出する
```
    そのコードブロックの高レベルの目標はなにか?
    高レベルな目標に対し、無関係の下位問題を解決しているコードが相当量あれば、それは関数として抽出する
    下位問題は完全に自己完結していて、アプリケーションからどの様に使われるかを知らない関数にすることで、再利用可能でテストしやすくなる
    プロジェクト固有のコードから汎用コードを分離する
```

## 1度に1つのことを
```
    コードはできるだけ小さくした"タスク"を1つずつ行うように設計する
    関数内に複数のタスクがある場合、関数内で領域を分け
    読みにくいコードがあれば、そこで行われているタスクを列挙し分割を行う
```

## コードに思いを込める
```
    1. コードを簡単な言葉で説明する
    2. その説明の中で使っている言葉、キーワードに注目する
    3. その説明に合わせてコードを書く
```
※ 簡潔なコードを書くには、ライブラリが何を提供してくれているのか知る必要がある

## 短いコードを書く
```
    最も読みやすいコードとは、何も書かれていないコードである。
    「要求の削除」と「より単純な問題の解決」を心がける
    コードの「重量」を意識する。軽量で機敏にしておく。
    最も簡単に問題を解決できるような要求を考える
    たまに標準ライブラリのドキュメントを読んでみて、どんなことができそうか考えてみる
```

## テストと読みやすさ
```
    インターフェースを意識してシンプルに書く
    どの行でエラーが出て、期待した値はどのようなもので実際の値は何だったのかが出力されるとわかりやすい
    望んだ出力方法がない場合、自分で作る
    入力値は有効で単純なものに
    カバレッジが100%になることはない(パレートの法則)
```
### テストしやすいコード
```
    明確なインターフェースを持つ
    状態を持たない
    「セットアップ」がない
    テスト時に検査したいデータが隠されていない
```