----------------------------------------------------------------------
■「MahjongUtil」：麻雀に関する機能を提供するSAORI
■Written by Don
　http://nikolat.herokuapp.com/
----------------------------------------------------------------------

■これは何をするものか

　麻雀に関する機能を提供するSAORIです。
　シャンテン数の計算、点数計算、待ち牌の判定などができます。

　入力・出力の値となる牌の表記はUMP(Universal Mahjong Protocol)に準拠します。
　https://osdn.net/projects/openmj/wiki/UMP

■動作環境

・Windows10

■使用方法

□shanten:シャンテン数の計算

　シャンテン数を計算します。
　入力された手牌に対し最小となるシャンテン数をResultに、
　算出した元となる雀頭、面子、塔子の組み合わせをValue0以降に返します。
　(七対子の場合は"chitoitsu"、国士無双の場合は"kokushimusou"をValue0以降に返します)
　入力する牌の数に制限はありません。13枚でも14枚でも可能です。
　シャンテン数0はテンパイ、-1は和了を意味します。

　・呼び出し：
　　Argument0　　　shanten
　　Argument1　　　手牌

　・結果
　　Result　　 　　シャンテン数
　　Value0以降 　　算出した元となる雀頭、面子、塔子の組み合わせ(","区切り)
　　　　　　　 　　先頭は雀頭(無い場合は空)

　・例1
　　Argument0: shanten
　　Argument1: 1m2m3m5p6p7p8p9p9p2s3s4s4s
　　　↓
　　Result: 1
　　Value0: 9p9p,1m2m3m,5p6p7p,2s3s4s
　　Value1: 9p9p,1m2m3m,6p7p8p,2s3s4s
　　Value2: 4s4s,1m2m3m,5p6p7p,8p9p,2s3s
　　Value3: 4s4s,1m2m3m,5p6p7p,9p9p,2s3s
　　Value4: 4s4s,1m2m3m,6p7p8p,9p9p,2s3s
　　Value5: 4s4s,1m2m3m,7p8p9p,5p6p,2s3s
　　Value6: ,1m2m3m,5p6p7p,8p9p,2s3s4s
　　Value7: ,1m2m3m,5p6p7p,9p9p,2s3s4s
　　Value8: ,1m2m3m,6p7p8p,9p9p,2s3s4s
　　Value9: ,1m2m3m,7p8p9p,5p6p,2s3s4s

　　※上記の例ではValue0とValue7、Value1とValue8が同じ組み合わせを意味しますが、
　　　雀頭の有無を区別する際に有用なので敢えて別物として出力しています。
　　　また、9p9p,1m2m3m,5p6p7p,2s3s,3s4s等のパターンも存在すべきところですが、
　　　全パターンを網羅しようとすると処理時間が膨大になり実用に耐えないため、
　　　面子の数が最大となる場合のみ出力する仕様となっています。

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
　　Value0以降 　　算出した元となる雀頭、面子、塔子の組み合わせ(","区切り)
　　　　　　　 　　先頭は雀頭(無い場合は空)

　・例
　　Argument0: shanten_normal
　　Argument1: 1m9m1p9p1s9s1z2z3z4z5z6z7z7z
　　　↓
　　Result: 7
　　Value0: 7z7z
　　Value1: ,7z7z

□score:点数計算

　点数を計算します。
　算出した元となる符、翻、および役の情報をValue0以降に返します。
　(役満の場合は何倍役満であるか、および役満の情報をValue0以降に返します)

　・呼び出し：
　　Argument0　　　score
　　Argument1　　　手牌(13枚)
　　Argument2　　　和了牌
　　Argument3　　　場風牌
　　Argument4　　　自風牌
　　Argument5　　　ドラ牌(複数指定可)
　　Argument6　　　親か否か
　　Argument7　　　ツモか否か
　　Argument8　　　立直か否か
　　Argument9　　　ダブル立直か否か
　　Argument10 　　一発か否か
　　Argument11 　　鳴きの無い1巡目のツモか否か
　　Argument12 　　海底牌(河底牌)か否か
　　Argument13 　　嶺上開花か否か
　　Argument14 　　槍槓か否か
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
　　Argument3: 1z
　　Argument4: 2z
　　Argument5: 9m9p
　　Argument6: 1
　　Argument7: 1
　　Argument8: 0
　　Argument9: 0
　　Argument10: 0
　　Argument11: 1
　　Argument12: 0
　　Argument13: 0
　　Argument14: 0
　　　↓
　　Result: 192000
　　Value0: 4
　　Value1: 四暗刻,1
　　Value2: 字一色,1
　　Value3: 大三元,1
　　Value4: 天和,1

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
　ありがとうございます。

　　csaori
　　　https://github.com/ponapalt/csaori


■配布条件等

license.txtを見てください。

■更新履歴

・まだ未完成なので完成したら正式に公開します。

