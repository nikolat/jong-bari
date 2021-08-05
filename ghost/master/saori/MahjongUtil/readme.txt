----------------------------------------------------------------------
■「MahjongUtil」：麻雀に関する機能を提供するSAORI
■Written by Don
　http://nikolat.herokuapp.com/
----------------------------------------------------------------------

■これは何をするものか

　麻雀に関する機能を提供するSAORIです。
　シャンテン数の計算、和了点計算、待ち牌の判定などができます。

　入力・出力の値となる牌の表記はUMP(Universal Mahjong Protocol)に準拠します。
　https://osdn.net/projects/openmj/wiki/UMP

■動作環境

・Windows10

■使用方法

□shanten:シャンテン数の計算

　シャンテン数を計算します。
　入力された手牌に対し最小となるシャンテン数をResultに、
　算出した元となる雀頭、面子、塔子、孤立牌の組み合わせをValue0以降に返します。
　(七対子の場合は"chitoitsu"、国士無双の場合は"kokushimusou"をValue0以降に返します)
　入力する牌の数に制限はありません。1枚でも13枚でも14枚でも15枚でも可能です。
　シャンテン数0はテンパイ、-1は和了を意味します。

　・呼び出し：
　　Argument0　　　shanten
　　Argument1　　　手牌

　・結果
　　Result　　 　　シャンテン数
　　Value0以降 　　算出した元となる雀頭、面子、塔子、孤立牌の組み合わせ(","区切り)
　　　　　　　 　　先頭は雀頭(無い場合は空)、塔子(対子)との重複分は除外

　・例1
　　Argument0: shanten
　　Argument1: 1m2m3m5p6p7p8p9p9p2s3s4s4s
　　　↓
　　Result: 1
　　Value0: 9p9p,1m2m3m,5p7p,6p8p,2s3s4s,4s
　　Value1: 9p9p,1m2m3m,5p6p,7p8p,2s3s4s,4s
　　Value2: 9p9p,1m2m3m,6p7p8p,5p,2s4s,3s4s
　　Value3: 9p9p,1m2m3m,6p7p8p,5p,2s3s,4s4s
　　Value4: 9p9p,1m2m3m,6p7p8p,5p,2s3s4s,4s
　　Value5: 9p9p,1m2m3m,5p6p7p,8p,2s4s,3s4s
　　Value6: 9p9p,1m2m3m,5p6p7p,8p,2s3s,4s4s
　　Value7: 9p9p,1m2m3m,5p6p7p,8p,2s3s4s,4s
　　Value8: 4s4s,1m2m3m,7p8p9p,5p6p,9p,2s3s
　　Value9: 4s4s,1m2m3m,5p6p7p,8p9p,9p,2s3s
　　Value10: ,1m2m3m,7p8p9p,5p6p,9p,2s3s4s,4s
　　Value11: ,1m2m3m,5p6p7p,8p9p,9p,2s3s4s,4s


　・例2
　　Argument0: shanten
　　Argument1: 2p2p3p3p4p4p5p5p6p6p7p7p8p8p
　　　↓
　　Result: -1
　　Value0: 2p2p,3p4p5p,3p4p5p,6p7p8p,6p7p8p
　　Value1: 5p5p,2p3p4p,2p3p4p,6p7p8p,6p7p8p
　　Value2: 8p8p,2p3p4p,2p3p4p,5p6p7p,5p6p7p
　　Value3: chitoitsu

□shanten_normal:シャンテン数の計算(七対子と国士無双を除外)

　七対子と国士無双を除外したシャンテン数を計算します。
　仕様はshantenと一緒です。

　・呼び出し：
　　Argument0　　　shanten_normal
　　Argument1　　　手牌

　・結果
　　Result　　 　　シャンテン数
　　Value0以降 　　算出した元となる雀頭、面子、塔子、孤立牌の組み合わせ(","区切り)
　　　　　　　 　　先頭は雀頭(無い場合は空)、塔子(対子)との重複分は除外

　・例
　　Argument0: shanten_normal
　　Argument1: 1m9m1p9p1s9s1z2z3z4z5z6z7z7z
　　　↓
　　Result: 7
　　Value0: 7z7z,1m,9m,1p,9p,1s,9s,1z,2z,3z,4z,5z,6z

□shanten_yaku:シャンテン数の計算(役がある場合)

　役があるシャンテン数を計算します。
　いくつかの役に対するシャンテン数を計算し、その中で最小となるシャンテン数をResultに、
　算出した元となる特定の役に対するシャンテン数をValue0以降に返します。

　現時点で算出対象としている役は以下の通りです。
　・七対子
　・国士無双
　・門前清自摸和
　・役牌
　・断ヤオ九
　・対々和
　・混一色

　役牌の場合は役牌の手持ちが0枚でも理論上3枚引いてくれば役ができますが、
　手持ちに役牌の刻子または対子がある場合のみ計算対象としています。
　副露判断に使用されることを想定している事情によるものです。

　・呼び出し：
　　Argument0　　　shanten
　　Argument1　　　手牌
　　Argument2　　　場風牌
　　Argument3　　　自風牌
　　※Argument2以降は省略可

　・結果
　　Result　　 　　シャンテン数
　　Value0以降 　　役、シャンテン数の組み合わせ(","区切り)

　・例1
　　Argument0: shanten_yaku
　　Argument1: 1m2m3m5p6p7p8p9p9p2s3s4s4s
　　　↓
　　Result: 1
　　Value0: 七対子,4
　　Value1: 国士無双,10
　　Value2: 対々和,6
　　Value3: 断ヤオ九,3
　　Value4: 混一色,7
　　Value5: 門前清自摸和,1

　・例2
　　Argument0: shanten_yaku
　　Argument1: 1m3m3m5m6m8m2s3s1z2z2z<3m4m5m>
　　Argument2: 1z
　　Argument3: 2z
　　　↓
　　Result: 2
　　Value0: 役牌,2
　　Value1: 断ヤオ九,3
　　Value2: 混一色,2

□score:和了点計算

　和了点を計算します。
　算出した元となる符、翻、および役の情報をValue0以降に返します。
　(役満の場合は何倍役満であるか、および役満の情報をValue0以降に返します)
　(嶺上開花においてツモ符2符を認めるルールとしています)

　・呼び出し：
　　Argument0　　　score
　　Argument1　　　手牌(13枚)
　　Argument2　　　和了牌
　　Argument3　　　場風牌
　　Argument4　　　自風牌
　　Argument5　　　ドラ牌(複数指定可)(ドラ表示牌ではない)
　　Argument6　　　ツモか否か
　　Argument7　　　1: 立直, 2: ダブル立直
　　Argument8　　　一発か否か
　　Argument9　　　槍槓か否か
　　Argument10 　　嶺上開花か否か
　　Argument11 　　海底牌(河底牌)か否か
　　Argument12 　　鳴きの無い1巡目のツモか否か
　　※Argument3以降は省略可

　・結果
　　Result　　 　　点数
　　Value0　　 　　符
　　Value1　　 　　翻
　　Value2以降 　　役、翻の組み合わせ(","区切り)

　　※役満の場合は以下の通り
　　Result　　 　　点数
　　Value0　　 　　役満の倍数
　　Value1以降 　　役満、倍数の組み合わせ(","区切り)

　・例1
　　Argument0: score
　　Argument1: 1m2m3m1p2p3p1s1s2s3s3s4s4s
　　Argument2: 2s
　　　↓
　　Result: 5200
　　Value0: 40
　　Value1: 3
　　Value2: 一盃口,1
　　Value3: 三色同順,2

　・例2
　　Argument0: score
　　Argument1: 3z3z3z4z4z5z5z5z6z6z6z7z7z
　　Argument2: 7z
　　Argument3: 2z
　　Argument4: 1z
　　Argument5: 9m9p
　　Argument6: 1
　　Argument7: 0
　　Argument8: 0
　　Argument9: 0
　　Argument10: 0
　　Argument11: 0
　　Argument12: 1
　　　↓
　　Result: 192000
　　Value0: 4
　　Value1: 四暗刻,1
　　Value2: 大三元,1
　　Value3: 天和,1
　　Value4: 字一色,1

□machi:待ち牌の判定

　待ち牌を判定します。

　・呼び出し：
　　Argument0　　　machi
　　Argument1　　　手牌(13枚)

　・結果
　　Result 　　　　待ち牌

　・例1
　　Argument0: machi
　　Argument1: 1m1m1m2m3m4m5m6m7m8m9m9m9m
　　　↓
　　Result: 1m2m3m4m5m6m7m8m9m

　・例2
　　Argument0: machi
　　Argument1: 1m1m4m5m6m7m8m<1m2m3m>(9m9m9m9m)
　　　↓
　　Result: 3m6m9m

　　※上記の例では9mが4枚使われているため9mで和了ることはできません。
　　　待ちから除外する処理は呼び出し元の責任で行ってください。

■謝辞

　SAORIサンプルクラス「CSAORI」を使用させていただきました。

　　csaori
　　　https://github.com/ponapalt/csaori

　麻雀アプリ「電脳麻将」の開発ブログを参考にさせていただきました。

　　電脳麻将
　　　https://github.com/kobalab/Majiang

　ありがとうございます。

■配布条件等

license.txtを見てください。

■更新履歴

・2021-07-29 v1.0.0
　Initial Release

・2021-08-05 v1.0.1
　純正でない九蓮宝燈と13面待ちでない国士無双がW役満となっていた不具合の修正

