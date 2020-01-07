# テーブル定義書1
## 全体
- PKのカラム名はすべて「〇〇_id」ではなく「id」
 > PKのカラム名は「〇〇_id」ではなく「id」としましょう。
- テーブル名の先頭の文字が大文字になっている
 > テーブル名の先頭の文字が大文字になっているので小文字に修正しましょう。
- created_atが全てユーザ登録日時になっている
 > created_atが全てユーザ登録日時になっています。正しいカラム説明に修正しましょう。
- updated_atが全てユーザ更新日時になっている
 > updated_atが全てユーザ更新日時になっています。正しいカラム説明に修正しましょう。
- カラム名ににテーブル名と同じワードを入れない
 > カラム名にテーブル名と同じワードを入れないようにしましょう。
- カラム名に略語は使うべきでない
 > カラム名に略語は使わずに、誰が見ても意味がわかるようなカラム名にしましょう。

## Admin
- テーブル名が単数形になっている
 > テーブル名が単数形になっているので、複数形「admins」としましょう。
- 「admin_id(正しくはid)」のPK,AUTO INCREMENt,INDEXに◯が入っていない
 > 「admin_id(正しくはid)」のPK,AUTO INCREMENt,INDEXに◯が入っていいません。

## Users
- カラム名に「user_」という接頭辞がついているが接頭辞は必要ない
 > カラム名に「user_」という接頭辞がついていますが、必要ありません。
- 「user_f_name」,「user_f_kana」の NOT NULLに◯が入っていない
 > 「user_f_name」,「user_f_kana」の NOT NULLに◯が入っていませんが、なにか理由はありますか？
- 「user_f_name」,「user_tel」などでカラム名に略語を使ってるが、略語は使うべきでない
 > 「user_f_name」,「user_tel」などでカラム名に略語を使われていますが、誰が見てもわかるようなカラム名に修正しましょう。
- 「user_tel」がinteger型になっている,正しくはstring型
 > 「user_tel」内のデータ(電話番号)に「-(ハイフン)」は含めますか？「-」を含めた場合のデータ型もintegerですか？
- 「zip_code」がinteger型になっている,正しくはstring型
 > 「zip_code」内のデータ(郵便番号)に「-(ハイフン)」は含めますか？「-」を含めた場合のデータ型もintegerですか？
- 「member_status」のデータ型がstringになっているが,DEFAULTがFALSEになっている。退会しているか否かの2通りなら,データ型はbooleanが適している。
 > 「member_status」のデータ型がstringになっていますが、DEFAULTがFALSEになっています。退会しているか否かの2通りなら,データ型はbooleanが適しています。
- 「member_status」というカラム名では会員の何のステータスを表しているか分からない。
 > 「member_status」というカラム名では会員の何のステータスを表しているか分かりにくいので、修正しましょう。
- 配送先を複数登録することを考慮してない
 > ユーザーが複数の住所を持つ場合はどうしますか？

## Products
- カラム名に「product_」という接頭辞がついているが接頭辞は必要ない
 > カラム名に「product_」という接頭辞がついているが接頭辞は必要ありません。
- 「genre_id」,「label_id」,「artist_id」はFK
 > 「genre_id」,「label_id」,「artist_id」はFKです。
-  [Products]が1で[Discs]が多なので「disc_id」は必要ない
 > Productsが1でDiscsが多なので「disc_id」は必要ありません。
- 「cd_image」はrefileを使うなら「cd_image_id」とする必要がある。またデータ型はstringのほうが好ましい
 > 「cd_image」はrefileを利用しますか？利用する場合はrefileの命名規則に則りカラム名をつけてください。
- 「stock_status」のデータ型はintegerにして、enumで管理したほうがいい
 > 「stock_status」のデータ型はintegerにして、enumで管理したほうが無駄がなくなります。
- 在庫数はカラムで管理するべきでない
 > 在庫数カラムがありますが、在庫数はカラムで管理するべきではありません。

## Discs
- 「disc_id(正しくはid)」のINDEXに◯がない
 > 「disc_id(正しくはid)」のINDEXに◯がありません。
- FKが「products_id」となっていますが、「product_id」にすべき
 > FKが「products_id」となっていますが、正しくはproduct_id」です。
- ディスク番号はどのように管理するか。「track_num」がディスク番号のことならば、カラム名が適切でない
 > 「track_num」となっていますが、ディスクの番号を把握したいはずなので、適切なカラム名に修正しましょう。

## Songs,Labels,Genre,Cart item
- PKである「id」が抜けている
 > PKである「id」が抜けています。

## Songs
- 曲名をもつカラムを「song」としているが、「name」などにすべき
 > 「song」というカラム名では何を表しているかわかりにくいので、「name」などにしましょう。
- 「song」のデータ型がintegerになっているが,正しくはstring
 > 「song」のデータ型がintegerになっていますが、正しくはstringです。

## Labels
- FK「product_id」は必要ない
 > FK「product_id」は必要ありません。
- レーベル名をもつカラムを「label」としているが、「name」などにすべき
 > 「label」というカラム名では何を表しているかわかりにくいので、「name」などにしましょう。

## Artists
- FK「product_id」は必要ない
 > FK「product_id」は必要ありません。
- 「artist」のデータ型がintegerになってるが、正しくはstring
 > 「artist」のデータ型がintegerになっていますが、正しくはstringです。
- アーティスト名をもつカラムを「artist」としているが、「name」などにすべき
 > 「artist」というカラム名では何を表しているかわかりにくいので、「name」などにしましょう。
- FKはAUTO INCREMENtではない,INDEXにする必要もない
> FKはAUTO INCREMENtではありません。INDEXにする必要もありません。

## Genre
- FK「product_id」は必要ない
 > FK「product_id」は必要ありません。
- テーブル名が単数形になっている
 > テーブル名をRailsの命名規則に則り、複数形にしましょう。
- FKはAUTO INCREMENtではない,INDEXにする必要もない
 > FKはAUTO INCREMENtではありません。INDEXにする必要もありません。
- 「genre」のデータ型がintegerになってるが、正しくはstring
 > 「genre」のデータ型がintegerになっていますが、正しくはstringです。
- ジャンル名をもつカラムを「genre」としているが、「name」などにすべき
 > 「genre」というカラム名では何を表しているかわかりにくいので、「name」などにしましょう。

## Cart item
- テーブル名が単数形になっている。_で区切ってcart_itemとするのが正しい
 > テーブル名は複数形にし、単語と単語を_(アンダーバー)で区切って「cart_items」としましょう。
- FKが「products_id」となっていますが、「product_id」にすべき
 > FKが「products_id」となっていますが、正しくは「product_id」です。
- FKはAUTO INCREMENtではない,INDEXにする必要もない
 > FKはAUTO INCREMENtではありません。INDEXにする必要もありません。
- 「buy num」となっているが「buy_num」とする必要がある
 > 「buy num」とありますが、_で区切って「buy_num」としましょう。
- 「subtotal」は必要ない
 > 「subtotal」カラムは必要ありません。

## Buy details
- テーブル名が「受注詳細」の意味になっていないので「order_details」などにするべき
 > テーブル名が「受注詳細」の意味になっていないので「order_details」などとしましょう。
- [Buy details]が多で[Buy]が1なので、FKとして「buy_id」が必要
 > [Buy details]が多で[Buy]が1なので、FKとして「buy_id」が必要です。
- 「buy num」が何を表しているかわかりにくい&スネークケースになっていない。「qunantity」などにするべき
 > カラム名はスネークケース(単語の間を_でつなげる)で命名しましょう。
 > 「buy num」が何を表しているかわかりにくいので、「qunantity」などにしましょう。

## Buy
- テーブル名が「受注」の意味になっていないので「orders」などにするべき
 > テーブル名が「受注」の意味になっていないので「orders」などとしましょう。
- Buy detailsで述べたとおり、[Buy details]が多で[Buy]が1なのでFK「buy_details_Id」は必要ない
 > Buy detailsで述べたとおり、[Buy details]が多で[Buy]が1なのでFK「buy_details_Id」は必要ありません。
- 「pay」のデータ型はintegerにして、enumで管理したほうがいい
 > 「pay」のデータ型はintegerにして、enumで管理したほうが無駄がなくなります。
- 「pay」が何を意味しているかわかりにくいので、「payment_method」などにすべき
 > 「pay」が何を意味しているかわかりにくいので、「payment_method」などにしましょう。
- 「buy_at」はcreated_atと同じなので、必要ない
 > 「buy_at」はcreated_atと同じ内容なので、必要ありません。
- 「stock」が何を表しているかわからないので、「total_price」などにすべき
 > 「stock」が何を意味しているかわかりにくいので、「total_price」などにしましょう。
- 送付先住所はあるが、郵便番号と宛名がない
 > 郵便番号と宛名カラムが抜けている。


# 指摘事項
## Users
- 「user_tel」がinteger型になっている,正しくはstring型
 > 「user_tel」がinteger型になっていますが、正しくはstring型です。
- 「zip_code」がinteger型になっている,正しくはstring型
 > 「zip_code」がinteger型になっていますが、正しくはstring型です。
    - integer型であっていますか？など、考えさせるような記述の方が良いです。
    もしくはなぜstringなのかを記述してあげましょう。
## Products
- 「cd_image」はrefileを使うなら「cd_image_id」とする必要がある。またデータ型はstringのほうが好ましい
    - cd_imageはrefileを利用しますか？利用する場合はrefileの命名規則に則りカラム名をつけてください。など答えを教えない方が良いと思います！