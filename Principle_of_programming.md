# [Principle of programming](https://www.amazon.co.jp/%E3%83%97%E3%83%AA%E3%83%B3%E3%82%B7%E3%83%97%E3%83%AB-%E3%82%AA%E3%83%96-%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9F%E3%83%B3%E3%82%B03%E5%B9%B4%E7%9B%AE%E3%81%BE%E3%81%A7%E3%81%AB%E8%BA%AB%E3%81%AB%E3%81%A4%E3%81%91%E3%81%9F%E3%81%84%E4%B8%80%E7%94%9F%E5%BD%B9%E7%AB%8B%E3%81%A4101%E3%81%AE%E5%8E%9F%E7%90%86%E5%8E%9F%E5%89%87-%E4%B8%8A%E7%94%B0-%E5%8B%B2/dp/4798046140)

## 1.前提
- コード自体がドキュメントである
- ソフトウェアは本質的に複雑であるため、完璧なものにはなりえない

## 2.原則
- KISS(修正容易性)
- DRY(ロジックやデータの抽象化でダブりを防ぐ)
- 単純性　＞　汎用性
- 書きやすさより、読みやすさ
- 関数の抽象度を揃える(抽象度の高い関数の中で具体的な処理を書くと可読性ダウン)
- 名前は、効果と目的を説明する

## 3.思想
- セオリー
```
  1. コミュニケーション
  2. シンプル
  3. 柔軟性
```
- 何のために"それ"を使うのか?
- ロジックと「ロジックが操作するデータ」はなるべく近くに置く(同じ関数、同じモジュール等)  
  → なぜなら、データとデータ操作の修正タイミングは同時期であることが多いから
- 抽象(現状まだあまり良く理解していない)
- カプセル化(データとロジックをグルーピング)  
  → 影響度、何をしているか、が明確になり扱いやすくなる
- 情報隠蔽で複雑性を下げる
- パッケージ化(カプセル化したモジュール群をさらにグルーピングする)
- 関心の分離(MVC等)
- 充足性、完全性、プリミティブ性(表現が十分かつ完璧かつ純粋か)
- ポリシーと実装の分離(ポリシー: ビジネスロジックやモジュールに対する引数を選択する部分)  
  → ポリシーは不安定で実装は安定的
- インターフェースと実装の分離(インターフェース: 機能の定義)
- 定義は1度きり
- 分割統治(問題を小さくするためにモジュールの責務で分割する)
- 設計原理
```
  1. 単純原理
    → シンプル、局所的な完全性を重視する
  2. 同型原理
    → 形に統一性を持たせる(処理の順番、引数の数等)
  3. 対称原理
    → 形の対称性にこだわる
  4. 階層原理
    → 同じレベルの処理は同じレベルの階層に書き抽象階層構造のあるコードにする
      上位レベルから見た下位レベルのコードは「それを外部から見ている」イメージ
  5. 線形原理(透明原理)
    → 処理の流れは直線にこだわる
  6. 証明原理
    → ロジックが正しく明瞭であること
  7. 安全原理
```
- UNIX思想(実践的な技の集合)
```
  1. モジュール化の原則(クリーンなインターフェースを持つシンプルなモジュールを作る)
    → これにより問題を局所化する
  2. 明確化の原則(3回以上解読しなければいけないコードは書かない(またはコメントを書く))
  3. 組み立て部品の原則(独立性を持たせる)
  4. 分離の原則(メカニズムとポリシーの分離)
    → webアプリの場合、フロントエンドがポリシーでバックエンドがメカニズム
  5. 単純性の原則(とにかくシンプルに)
  6. 倹約の原則(コードは小さく保つ)
  7. 透明性の原則(コード動作状況の見える化)
  8. 安定性の原理(コードはきちんと簡潔に人に説明できるようになっているか)
  9. 表現性の原則(複雑さはデータに寄せて、ロジックはできるかぎり単純にする)
  10. 驚き最小の原則(インターフェースはユーザーの既知を活用し学習コストを抑える)
    → 「+」は加算の記号であるという共通認識がある
  11. 沈黙の原則(重要な情報のみを出力表示)
  12. 修復の原則(動作はエラー時も見える化されているべき、エラーが出たら先の処理へは行かない)
  13. 経済性の原理(ハード、ソフト、設備をきちんと整え、ルールをなるべく設けない)
  14. 生成の原理(「コードを書く」コードを用意し時短、ミス削減)
  15. 最適化の原則(コードをまず正しいものを書きその次に速く動作する方法を模索する)
  16. 多様性の原則(ソフトウェアに唯一の正しい方法はない)
  17. 拡張性の原則(拡張できる設計にする、機能は予測で追加しない)
```
- UNIX哲学(設計の哲学)
```
  1. 小は美なり
    → シンプルで扱いやすいソフトウェアは価値が高い
  2. 1つ1仕事
  3. 速攻プロトタイプ(アイデアがものになりそうかなるべく早く書いてみる)
    → そのあと試行錯誤していく
  4. 効率性より移植性
  5. データはテキスト(バイナリファイルで持たない)
  6. レバレッジ・ソフトウェア(他人のコードを借りるなど少ない労力で大きな効果を得る)
  7. シェルスクリプト活用
  8. 対話インターフェース回避(ユーザーを拘束しない)
    → 入力待ち、入力値処理、コード肥大化のデメリットしかない
  9. フィルタ化(全てのソフトウェアは入力ストリームをデータとし受け取り、加工し出力する)
```

## 4.視点
- 凝集度  
  → たまたま同じだった処理をモジュールでまとめない/モジュール内での関連性を最大に、モジュール間での関連性を最小に
- 結合度(モジュールのブラックボックス化、相互依存しない)
- モジュールは冪等性と安全性を担保すべき  
  → 何回同じ操作をしても同じ結果になり、操作対象の状態を変化させないことでブラックボックス化する
- 直行性(コード同士には独立性と分離性を持たせる)
- 可逆性(「やっぱやめた」ができるように特定技術に依存しない)
- コードの臭い  
  → 臭いコードはリファクタリングが必要(同じ処理コードの重複、長すぎる処理、大きすぎるモジュール、多すぎるモジュール、名前不整合なモジュール)
- 技術的負債  
  → 時間がかかっても綺麗なコードを書くことで未来の負担を減らす  
  → 素早く書いた汚いコードはその後の機能追加、削除、リファクタリングで結局時間を取られる

## 5.習慣
- プログラマの3大美徳 怠慢、短気、傲慢
```
  怠慢: 後でみんなが楽できるようにする
       人がやらなくていいことは自動化
  短気: コンピューターにサボらせない
  傲慢: 綺麗なコードにこだわる
  
  頭脳労働のハードワークは報われない
```
- ボーイスカウトの規則(来たときより綺麗にして帰る)
- パフォーマンスチューニングはしない  
  → 可読性を代償には払えないから
- エゴレスプログラミング(人に優しくコードに厳しく)
- 1度に複数の作業をしない(コツコツ進めることを高速化していく)
- ツール(API等)の多様性は善  
  → 自然言語が複雑なのは複雑な現実を単純化するため  
  → 常にシンプルではなく、シンプルさをどこに置くかが大事  
  → ツールの場合ツール側が複雑さを受け入れクライアント側はシンプルに

## 6.手法
- 曳光弾(即座に正確なフィードバックを受ける)  
  → ソフトウェアの場合、一部でも本番をリリースしユーザーのフィードバックを集める
- 契約による設計(関数において引数は呼び出す側が、処理・戻り値は関数自身が条件を守る)
- 防御的プログラミング(~だろう、でコードしない、しっかりガード節を書く・エラーを無視しない等)
- ドックフーディング(ユーザー視点で自ら味見)
- ラバーダッキング(口で説明しながらデバッグ、説明できない箇所は理解できていない箇所)
- コンテキスト(名前で理解できるように、何のためにそれがあるのか・それをするのかの共有)  
  → デバッグはコードのみに原因を求めるのではなく、ライブラリとの関係、実行環境の関係などコンテキストにも目を向ける   
   1つ1つが正しくても全体として妥当でない場合があるため

## 7.法則
- ブルックスの法則(「人×月」 = 「月×人」にはならない)
- コンウェイの法則(アーキテクチャは組織に従う)
- 割れた窓の法則(悪いコードは放置せず改修)
- エントロピーの法則(コードは自然と腐っていく)
- 80-10-10の法則(ユーザーが求めるものの80%はすぐ作れる、10%は時間がかかる、10%は実現不可能)
- ジョシュアツリーの法則(名前がないもの、名前を知らないもの、は見ることができない)
- セカンドシステム症候群(Ver.2に注意!多機能主義にならない)  
  → ユーザーは基本機能の安定と基本機能の使い勝手の良さを求める
- 車輪の再開発(再開発すべきときとすべきでないときの場合分けが必要)
- ヤクの毛刈り(本当の問題、目的を忘れないようにメモをとったりコメントを書いたり工夫する)
