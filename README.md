# CppCoreGuidelines-Ja
Japanese translation of rule titles from "C++ Core Guidelines"

C++ Core Guidelines の日本語訳

Here is a Japanese translation of (mostly only) rule titles (for now) from [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) as of April 16, 2018 by kanda.motohiro@gmail.com. This translation is disributed under the [LICENSE](https://github.com/isocpp/CppCoreGuidelines/blob/master/LICENSE).
The LICENSE is very restrictive but according to this [issue discussion on translation](https://github.com/isocpp/CppCoreGuidelines/issues/1065), publishing a translation is permitted.

以下は、C++ Core Guidelines の規則の（ほぼ）タイトルだけを訳したものです。ライセンスファイルによれば、訳をこのように公開することは不可能なのですが、引用したイシューでは、許可されているようです。

私は、以下のスライドで、C++ Core Guidelines を知りました。感謝します。

[Boost.勉強会#19東京 Effective Modern C++とC++ Core Guidelines](https://www.slideshare.net/ShintarouOkada/boost19-effective-modern-cc-core-guidelines)

## おまけ

### NR.X: ダメ：全ての例外は発生する最も近くで捕捉しよう

##### Example, bad

    try {
        std::string s{"Hello, World\n"};
        //std::string S(1024*1024*1024, 'a');
    } catch (const std::bad_alloc& e) {
        fprintf(stderr, "failed to allocate string. %s. C is exception free!\n", e.what());
        exit(1);
    }

main で例外を捉えました。どこで何が起きたかは、わかりません、というのも困るけど。やっぱり、C++ にも、バックトレースほしいよね。

### 先生は言われた。

* 劣った人はただ規則に従う。
* ほどほどの人は、規則の意味を考えて取捨選択し、必要な時は新しい規則を作る。
* 優れた人は、その挙動の全てが、 best practice になる。

// 論語のもじりなのだが、主張は道家みたいになった。

### もうひとつ、あとがき

C++ は進化し続けています。古い言語仕様、ライブラリ、実装にもとづいたアドバイスの多くは今では有害です。

このガイドラインも例外ではありません。これは、二つの不確定要素を含みます。コンセプトと GSL です。いずれも、C++17 には含まれません。あなたのプロジェクトで、それらに依存する規則を採用した場合、例えば、五年後にどうなるかは不明です。

### 参考

[Google C++ スタイルガイド 日本語全訳](https://ttsuki.github.io/styleguide/cppguide.ja.html)
これ、面白い。訳した方に感謝。
出力の関数引数は、参照でなくて、ポインタを使う。 // 私もその方が好き。
例外は使わない。

以上
