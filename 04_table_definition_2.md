# テーブル定義書2
## 全体
- PKのカラム名はすべて「〇〇_id」ではなく「id」
 > PKのカラム名が全て「〇〇_id」となっていますが、正しくは「id」です。

## admins
- PKのINDEXに◯がない
 > PKのINDEXに◯がありません。
- カラム名に接頭辞「admin_」がついているものがあるが接頭辞は必要ない
 > カラム名に接頭辞「admin_」がついているものがありますが接頭辞は必要ありません。

## users
- カラム名に接頭辞「user_」がついているものがあるが接頭辞は必要ない
 > カラム名に接頭辞「user_」がついているものがありますが接頭辞は必要ありません。
- 「user_tel」などでカラム名に略語を使ってるが、略語は使うべきでない
 > 「user_f_name」,「user_tel」などでカラム名に略語を使われていますが、誰が見てもわかるようなカラム名に修正しましょう。
- 「member_status」データ型がintegerなのにDEFAULTがfalseになっている。true or falseで管理するなら、データ型はboolean
 > 「member_status」のデータ型がstringになっていますが、DEFAULTがFALSEになっています。退会しているか否かの2通りなら,データ型はbooleanが適しています。
- 「member_status」というカラム名では、会員の何のステータスを表しているか分からない
 > 「member_status」というカラム名では会員の何のステータスを表しているか分かりにくいので、修正しましょう。
- 「user_l_kana」,「user_f_kana」では何を表しているカラム名かわかりにくいので、カラム名にnameを付け加えるべき
 > 「user_l_kana」,「user_f_kana」では何を表しているカラム名かわかりにくいので、カラム名にnameを付け加えるべきです。

## ships
- PKのINDEXに◯がない
 > PKのINDEXに○がありません。
- カラム名に接頭辞「ship_」がついているものがあるが接頭辞は必要ない
 > カラム名に接頭辞「ship_」がついているものがありますが接頭辞は必要ありません。
- 「ship_code」とあるが,[users]と統一して「zip_code」としたほうがいい
 > 「ship_code」とあるが,[users]テーブルに合わせて「zip_code」としたほうがいいかと思います。

## products
- 在庫数はカラムで管理すべきでない
 > 在庫数はカラムで管理すべきではありません。
- 論理削除を考慮していない
 > 商品を削除した場合、該当するレコードはどうなりますか？
- 「stock_status」カラムは必要ない
 > 「stock_status」カラムは必要ですか？

## discs
- PKのINDEXに◯がない
 > PKのINDEXに○がない
- カラム名に接頭辞「disc_」がついているものがあるが接頭辞は必要ない
 > カラム名に接頭辞「disc_」がついているものがありますが接頭辞は必要ありません。
- FKが「products_id」となっているが、「product_id」が正しい
 > FKが「products_id」となっていますが、正しくは「product_id」です。

## songs
- 曲名をもつカラムを「song」としているが、「name」などにすべき
 > 「song」というカラム名では何を表しているかわかりにくいので、「name」などにしましょう。

## labels
- レーベル名をもつカラムを「label」としているが、「name」などにすべき
 > 「label」というカラム名では何を表しているかわかりにくいので、「name」などにしましょう。

## artists
- アーティスト名をもつカラムを「artist」としているが、「name」などにすべき
 > 「artist」というカラム名では何を表しているかわかりにくいので、「name」などにしましょう。

## genre
- ジャンル名をもつカラムを「genre」としているが、「name」などにすべき
 > 「genre」というカラム名では何を表しているかわかりにくいので、「name」などにしましょう。

## cart items
- テーブル名は「cart_items」が正しい
 > テーブル名は単語同士を_で区切って「cart_items」としましょう。
- PK「Cart item_id(正しくはid)」のINDEXに◯がない
 > PK「Cart item_id(正しくはid)」のINDEXに◯がありません。
- FKが「products_id」となっているが、「product_id」が正しい
 > FKが「products_id」となっていますが、正しくは「product_id」です。
- 「buy num」スネークケースになっていない&何を意味しているかわかりにくい
 > カラム名はスネークケース(単語の間を_でつなげる)で命名しましょう。
 > 「buy num」が何を表しているかわかりにくいので、「qunantity」などにしましょう。

## sell_details
- テーブル名は「order_details」としたほうが、何を表しているかわかりやすい
 > 「sell_details」では何を意味しているかわかりにくいので、「order_details」などとしましょう。
- FKが「products_id」となっているが、「product_id」が正しい。FKに◯がない
 > FKが「products_id」となっていますが、正しくは「product_id」です。
- [sell_details]が多で[sells]が1なので、FKとして「sell_id」が必要
 > sell_detailsが多でsellsが1なので、FKとして「sell_id」が必要です。
- 購入時の価格の情報を保持するカラムがない
 > 購入時の価格の情報を保持するカラムがありませんが、問題ないですか？

## sells
- テーブル名は「orders」としたほうが、何を表しているかわかりやすい
 > 「sells」では何を意味しているかわかりにくいので、「orders」などとしましょう。
- PKのINDEXに◯がない
 > PKのINDEXに◯がありません。
- [sell_details]が多で[sells]が1なのでFK「sell_details_Id」は必要ない
 > sell_detailsが多でsellsが1なのでFK「sell_details_Id」は必要ありません。
- 「pay」が何を意味しているかわかりにくいので、「payment_method」などにすべき
 > 「pay」が何を意味しているかわかりにくいので、「payment_method」などとしましょう
- 「total」が何を意味しているかわかりにくいので、「total_price」などにすべき
 > 「total」が何を意味しているかわかりにくいので、「total_price」などとしましょう。