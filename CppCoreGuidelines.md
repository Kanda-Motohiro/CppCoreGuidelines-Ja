Here is a Japanese translation of (mostly only) rule titles (for now) from [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) as of April 16, 2018 by kanda.motohiro@gmail.com. This translation is disributed under the [LICENSE](https://github.com/isocpp/CppCoreGuidelines/blob/master/LICENSE).
The LICENSE is very restrictive but according to this [issue discussion on translation](https://github.com/isocpp/CppCoreGuidelines/issues/1065), publishing a translation is permitted.

以下は、C++ Core Guidelines の規則の（ほぼ）タイトルだけを訳したものです。ライセンスファイルによれば、訳をこのように公開することは不可能なのですが、引用したイシューでは、許可されているようです。

### <a name="Rp-direct"></a>P.1: アイディアは直接コードで表現しよう

### <a name="Rp-Cplusplus"></a>P.2: ISO Standard C++ で書こう

### <a name="Rp-what"></a>P.3: 意図を表現しよう

### <a name="Rp-typesafe"></a>P.4: 理想的には、プログラムは静的に型安全であるべきです

### <a name="Rp-compile-time"></a>P.5: 実行時チェックより、コンパイル時チェックをするようにしよう

### <a name="Rp-run-time"></a>P.6: コンパイル時にチェックできないものは、実行時にチェック可能であるべきです

### <a name="Rp-early"></a>P.7: 実行時エラーは早めに捕捉しよう

### <a name="Rp-leak"></a>P.8: 資源は決してリークしないこと

### <a name="Rp-waste"></a>P.9: 時間や領域をむだにしないこと

### <a name="Rp-mutable"></a>P.10: 変更可能なデータより変更不可能なデータを選ぼう

### <a name="Rp-library"></a>P.11: 汚い構成要素は、コード中にちりばめないで、カプセル化しよう

### <a name="Rp-tools"></a>P.12: 適切にサポートツールを使おう

### <a name="Rp-lib"></a>P.13: 適切にサポートライブラリを使おう

### <a name="Ri-explicit"></a>I.1: インタフェースは明示的にしよう

### <a name="Ri-global"></a>I.2: `const` でないグローバル変数は避けよう

### <a name="Ri-singleton"></a>I.3: シングルトンは避けよう

##### 例外

最初にアクセスされた時に初期化をするために、最も単純な「シングルトン」（あまりに単純なので、普通はシングルトンであるとは考えられません）を使うことができます。

    X& myX()
    {
        static X my_x {3};
        return my_x;
    }

### <a name="Ri-typed"></a>I.4: インタフェースは、正確で、強い型付けとしよう

### <a name="Ri-pre"></a>I.5: 前提条件を述べよう (もしあれば)

### <a name="Ri-expects"></a>I.6: 前提条件を述べるには、`Expects()` を使おう

### <a name="Ri-post"></a>I.7: 事後の条件を述べよう

### <a name="Ri-ensures"></a>I.8: 事後の条件を述べるには、`Ensures()` を使おう

### <a name="Ri-concepts"></a>I.9: インタフェースがテンプレートであるなら、そのパラメタをコンセプトを使って文書化しよう

### <a name="Ri-except"></a>I.10: 要求される仕事を実行できないことを伝えるには、例外を使おう

### <a name="Ri-raw"></a>I.11: 決して、生のポインタ(`T*`)や参照(`T&`)で、所有権を移動しないこと

### <a name="Ri-nullptr"></a>I.12: ヌルであってはいけないポインタは、`not_null` と宣言しよう

### <a name="Ri-array"></a>I.13: 配列を一つのポインタで渡さないこと

### <a name="Ri-global-init"></a>I.22: グローバルなオブジェクトの複雑な初期化を避けよう

### <a name="Ri-nargs"></a>I.23: 関数引数の数は少なく抑えよう

### <a name="Ri-unrelated"></a>I.24: 同じ型で関連しないパラメタが隣り合うのを避けよう

##### 理由

同じ型の隣り合った引数は、間違えて逆にしやすいです。

##### 例、良くない

これを考えましょう:

    void copy_n(T* p, T* q, int n);  // copy from [p:p + n) to [q:q + n)

これは、K&R C スタイルインタフェースのやっかいな変種です。"to" と "from" 引数を逆にするのは容易です。

"from" 引数に、`const` を使おう:

    void copy_n(const T* p, T* q, int n);  // copy from [p:p + n) to [q:q + n)

##### 例外

パラメタの順序が重要でないなら、問題はありません。

    int max(int a, int b);

##### 代案

パラメタ型に、 `struct` を定義して、それらのパラメタのフィールドに適切な名前をつけよう。

    struct SystemParams {
        string config_file;
        string output_path;
        seconds timeout;
    };
    void initialize(SystemParams p);

こうすることで、この呼び出しを、将来これを読む人に明確にする傾向があります。引数はコール元で、しばしば、名前を使って入れられるためです。

### <a name="Ri-abstract"></a>I.25: インタフェースには、クラス階層でなく、抽象クラスを選ぼう

### <a name="Ri-abi"></a>I.26: クロスコンパイラの ABI がほしいなら、 C-スタイルのサブセットを使おう

### <a name="Ri-pimpl"></a>I.27: 安定したライブラリの ABI のためには Pimpl イディオムを考慮しよう

### <a name="Ri-encapsulate"></a>I.30: 規則を破るところはカプセル化しよう

##### 例

何らかの入力（例えば、`main` への引数）によって、ファイル、コマンドライン、あるいは標準入力からの入力を読み込む必要のあるプログラムを考えましょう。
例えば、こんなふうに書けます。

    bool owned;
    owner<istream*> inp;
    switch (source) {
    case std_in:        owned = false; inp = &cin;                       break;
    case command_line:  owned = true;  inp = new istringstream{argv[2]}; break;
    case file:          owned = true;  inp = new ifstream{argv[2]};      break;
    }
    istream& in = *inp;

これは、 [初期化されていない変数を使わない](#Res-always) 規則、
[所有権を無視する](#Ri-raw) 規則、
[マジック定数を使わない](#Res-magic)規則に違反します。
特に、誰かがどこかで、こう書くことを覚えていなければいけません。

    if (owned) delete inp;

この特定の例は、`cin` に対しては何もしない特別の deleter を持つ `unique_ptr` を使って解決することができます。
しかしそれは、（この問題に必ずぶつかる）初心者には複雑です。
そしてこの例は、静的と考えたい属性（今の場合、所有権）が、たまに、実行時に解決されなくてはいけないことがあるという、より一般的な問題の例です。
一般的で、最もひんぱんで、最も安全な例は、静的に解決することができます。なので、これにコストと複雑性を加えたくはありません。
しかし、一般的でなく、あまり安全でなく、必然的により高価なケースにも対応しなくてはいけません。
そのような例は、[[Str15]](http://www.stroustrup.com/resource-model.pdf) で議論されます。

そのためにクラスを書きます。

    class Istream { [[gsl::suppress(lifetime)]]
    public:
        enum Opt { from_line = 1 };
        Istream() { }
        Istream(zstring p) :owned{true}, inp{new ifstream{p}} {}            // read from file
        Istream(zstring p, Opt) :owned{true}, inp{new istringstream{p}} {}  // read from command line
        ~Istream() { if (owned) delete inp; }
        operator istream& () { return *inp; }
    private:
        bool owned = false;
        istream* inp = &cin;
    };

これで、`istream` の所有権の動的な性質はカプセル化されました。
現実のコードでは、潜在的なエラーへのチェックを少し、追加するのが良いでしょう。

訳註。引数があれば、ファイル、なければ、標準入力、というのは、よくあるのに、C++ で書きにくいのは有名らしく、私もはまった結果、引数を評価した後で、rdbuf を入れ直す、というトリックを教わりました。

### <a name="Rf-package"></a>F.1: 意味のある操作を注意深く名前を付けた関数に「パッケージ」しよう

### <a name="Rf-logical"></a>F.2: 一つの関数は一つの論理的な操作をするべきです

### <a name="Rf-single"></a>F.3: 関数は短く単純に保とう

### <a name="Rf-constexpr"></a>F.4: 関数がコンパイル時に評価されなければいけないならば、`constexpr` と宣言しよう

### <a name="Rf-inline"></a>F.5: 関数がとても小さく、実行時間が重要なら、`inline` と宣言しよう

### <a name="Rf-noexcept"></a>F.6: 関数が例外を投げないなら、 `noexcept` と宣言しよう

### <a name="Rf-smart"></a>F.7: 一般的な用途には、スマートポインタでなく、 `T*` あるいは `T&` 引数を取ろう

##### 理由

スマートポインタを渡すと、所有権を渡すあるいは共用します。そしてそれは所有権のセマンティクスが意図されるときにだけ
使われるべきです（[R.30](#Rr-smartptrparam)を参照）。
スマートポインタで渡すことは、その関数の使用を、スマートポインタを使う呼び出し元に限定します。
共用されたスマートポインタ（例えば、[R.30](#Rr-smartptrparam)）を渡すことは、実行時のコストを意味します。

### <a name="Rf-pure"></a>F.8: pure 関数を使おう

### <a name="Rf-unused"></a>F.9: 使わないパラメタは、無名とするべきです

##### 例

    X* find(map<Blob>& m, const string& s, Hint);   // once upon a time, a hint was used

### <a name="Rf-conventional"></a>F.15: 情報を伝えるには、単純で普通の方法を選ぼう

##### 理由

「普通でなく賢い」テクニックを使うことは、人を驚かせ、他のプログラマの理解を遅くし、バグを起こしやすくします。
もしあなたが本当に、一般的なテクニックを超えた最適化を必要と感じた時は、それが本当に改善であるかを確かめるために測定を行い、ドキュメント／コメントしなさい。なぜならばその改善は移植性がないかもしれないからです。

以下の表は 以下のガイドライン F.16-21 のアドバイスをまとめたものです。

普通の引数の渡し方：

![Normal parameter passing table](https://github.com/isocpp/CppCoreGuidelines/blob/master/param-passing-normal.png "Normal parameter passing")

上級者向けの引数の渡し型：

![Advanced parameter passing table](https://github.com/isocpp/CppCoreGuidelines/blob/master/param-passing-advanced.png "Advanced parameter passing")

上級者向けのテクニックは、その必要性をきちんと示し、その必要性をコメントにドキュメントした後で使おう。

### <a name="Rf-in"></a>F.16: 「入力」パラメタでは、安価にコピーできる型は値渡しで、そうでないものは `const` への参照で渡そう

### <a name="Rf-inout"></a>F.17: 「入出力」パラメタは、`const` でない参照で渡そう

### <a name="Rf-consume"></a>F.18: 「move-from する予定」のパラメタは、 `X&&` で渡して、そのパラメタを std::move しよう

### <a name="Rf-forward"></a>F.19: 「forward」パラメタは、 `TP&&` で渡して、そのパラメタには std::forward だけをしよう

### <a name="Rf-out"></a>F.20: 「出力」の出力値は、出力パラメタより、戻り値を選ぼう

##### 例外

* 継承階層中の型のような、値型でないものは、オブジェクトを `unique_ptr` あるいは `shared_ptr` で返そう。
* もし型がムーブが高価（例えば、`array<BigPOD>`）な時は、それをフリーストア上に確保しハンドル（例えば、`unique_ptr`）を返すか、（出力パラメタとして使われる）`const` でない転送先オブジェクトへの参照に渡すことを考えよう。
* 内側のループにある関数への複数の呼び出しにまたがって、キャパシティを持つオブジェクト(例えば、`std::string`, `std::vector`) を再使用する場合。

##### 例

    struct Package {      // exceptional case: expensive-to-move object
        char header[16];
        char load[2024 - 16];
    };

    Package fill();       // Bad: large return value
    void fill(Package&);  // OK

    int val();            // OK
    void val(int&);       // Bad: Is val reading its argument

### <a name="Rf-out-multi"></a>F.21: 複数の「出力」値を戻すには、 tuple あるいは struct を選ぼう

C++17 では、「構造化バインディング」を使って、複数の変数を宣言して初期化することができるようになるはずです：

    if (auto [ iter, success ] = my_set.insert("Hello"); success) do_something_with(iter);

### <a name="Rf-ptr"></a>F.22: 一つのオブジェクトを指定するには、 `T*` あるいは `owner<T*>` を選ぼう

### <a name="Rf-nullptr"></a>F.23: "null" が有効な値でないことを示すには、`not_null<T>` を使おう

### <a name="Rf-range"></a>F.24: 半開シーケンスを指定するには、`span<T>` あるいは `span_p<T>` を使おう

### <a name="Rf-zstring"></a>F.25: C-スタイル文字列を指定するには、`zstring` あるいは `not_null<zstring>` を使おう

### <a name="Rf-unique_ptr"></a>F.26: ポインタが必要である時、所有権を移動するには、`unique_ptr<T>` を使おう

### <a name="Rf-shared_ptr"></a>F.27: 所有権を共有するには、`shared_ptr<T>` を使おう

### <a name="Rf-ptr-ref"></a>F.60: 「引数なし」が有効な選択肢であるときは、`T&` でなく `T*` を使おう

### <a name="Rf-return-ptr"></a>F.42: 位置を指定するには、`T*` を返そう（その時に限り）

### <a name="Rf-dangle"></a>F.43: ローカルオブジェクトへのポインタあるいは参照は決して（直接、間接を問わす）返さないこと

##### 例、良くない

関数から戻った後は、そのローカルオブジェクトはもう存在しません：

    int* f()
    {
        int fx = 9;
        return &fx;  // BAD
    }

    void g(int* p)   // looks innocent enough
    {
        int gx;
        cout << "*p == " << *p << '\n';
        *p = 999;
        cout << "gx == " << gx << '\n';
    }

    void h()
    {
        int* p = f();
        int z = *p;  // read from abandoned stack frame (bad)
        g(p);        // pass pointer to abandoned stack frame to function (bad)
    }

##### 注意

これは参照にも当てはまります：

    int& f()
    {
        int x = 7;
        // ...
        return x;  // Bad: returns reference to object that is about to be destroyed
    }

### <a name="Rf-return-ref"></a>F.44: コピーが不適切で「オブジェクトを何も返さない」ことを必要としないなら、`T&` を返そう

### <a name="Rf-return-ref-ref"></a>F.45: `T&&` を返さないこと

### <a name="Rf-main"></a>F.46: `main()` の戻り値は、 `int` です

### <a name="Rf-assignment-op"></a>F.47: 代入演算子からは `T&` を返そう

##### 理由

`operator=(const T&)` の演算子多重定義（特に、値型では）の慣例は、代入をして、（`const` でない）`*this` を返すことです。
これは、標準ライブラリ型との一貫性を保証しますし、「整数がするようにしろ」という原則にも従います。

##### 注意

かつて、代入演算子が、 `const T&` を返すようにするという推奨がありました。
これは主に、`(a = b) = c` のような形のコードを避けるためでした。-- そのようなコードは、標準の型との一貫性に違反する価値のあるほど一般的ではありません。

### <a name="Rf-capture-vs-overload"></a>F.50: 関数ではうまく仕事ができないとき（ローカル変数を補足する、ローカル関数を書く）は、ラムダを使おう

### <a name="Rf-default-args"></a>F.51: 選択が可能なら、多重定義よりデフォルト引数を選ぼう

### <a name="Rf-reference-capture"></a>F.52: ローカルに使われるラムダでは、アルゴリズムに渡される変数も含めて、参照で変数を捕捉するようにしよう

### <a name="Rf-value-capture"></a>F.53: ノンローカルで使われる可能性のあるラムダでは、参照で変数を捕捉するのは避けよう；これには、戻り値、ヒープ上に格納されたもの、あるいは他のスレッドに渡されたものを含みます

### <a name="Rf-this-capture"></a>F.54: `this` を捕捉するなら、明示的に全ての変数を捕捉しよう（デフォルト補足はなし）

### <a name="F-varargs"></a>F.55: `va_arg` 引数を使わないこと

### <a name="Rc-org"></a>C.1: 関連するデータは構造にまとめよう (構造体あるいはクラス)

### <a name="Rc-struct"></a>C.2: クラスが不変条件を持っているなら、クラスを使おう；データメンバが独立に変化することがあるなら、構造体を使おう

### <a name="Rc-interface"></a>C.3: インタフェースと実装の間の区別を、クラスを使って表そう

### <a name="Rc-member"></a>C.4: クラスの表現へ直接のアクセスを必要とする時に限って、関数をメンバにしよう

##### 理由

メンバ関数と比べて、カップリングが少ない。オブジェクト状態を変更して、問題を起こす可能性のある関数を少なくできる。表現を変えた後、修正が必要な関数を少なくできる。

##### 例

    class Date {
        // ... relatively small interface ...
    };

    // helper functions:
    Date next_weekday(Date);
    bool operator==(Date, Date);

「ヘルパー関数」は、`Date` の表現に直接アクセスする必要はありません。

##### 例外

言語は、 `virtual` 関数がメンバであることを要求します。そして、全ての `virtual` 関数が直接データをアクセスするわけではありません。
特に、抽象クラスのメンバはほぼそうしません。
参照： [multi-methods](https://parasol.tamu.edu/~yuriys/papers/OMM10.pdf).

##### 例外

言語は、 `=`, `()`, `[]`, と `->` がメンバであることを要求します。

### <a name="Rc-helper"></a>C.5: ヘルパー関数は、それがサポートするクラスと同じ名前空間に置こう

##### 理由

ヘルパー関数とは、クラスの表現への直接のアクセスを必要としない一方、そのクラスへの便利なインタフェースの一部と考えられる関数（普通は、そのクラスを書く人が提供する）です。
それをそのクラスと同じ名前空間に置くと、それとクラスの関係が明らかになり、引数依存の検索で見つけることが可能となります。

##### 例

    namespace Chrono { // here we keep time-related services

        class Time { /* ... */ };
        class Date { /* ... */ };

        // helper functions:
        bool operator==(Date, Date);
        Date next_weekday(Date);
        // ...
    }

##### 注意

これは、[多重定義された演算子](#Ro-namespace) で特に重要です。

### <a name="Rc-standalone"></a>C.7: クラスあるいは列挙型の定義と、その型の変数の宣言を同じ文でするのはやめよう

### <a name="Rc-class"></a>C.8: public でないメンバが一つでもあるなら、構造体でなくクラスを使おう

### <a name="Rc-private"></a>C.9: メンバをさらすのは最小限にしよう

### <a name="Rc-concrete"></a>C.10: クラス階層よりは、具象型を選ぼう

### <a name="Rc-regular"></a>C.11: 具象型は、規則的としよう

### <a name="Rc-zero"></a>C.20: デフォルト操作を避けることができるなら、そうしよう

##### 例

    struct Named_map {
    public:
        // ... no default operations declared ...
    private:
        string name;
        map<int, int> rep;
    };

    Named_map nm;        // default construct
    Named_map nm2 {nm};  // copy construct

`std::map` と `string` は全ての特別な関数を持っていますから、これ以上の作業は要りません。

##### 注意

これは、 "the rule of zero" として知られています。

### <a name="Rc-five"></a>C.21: デフォルト操作のどれか一つでも、定義あるいは `=delete` するなら、全てを定義あるいは `=delete` しよう

##### 理由

*特別なメンバ関数* とは、デフォルトコンストラクタ、コピーコンストラクタ、
コピー代入演算子、ムーブコンストラクタ、ムーブ代入演算子、そしてデストラクタです。

これら特別な関数のセマンティクスは緊密に関係しています。なので、一つが宣言される必要があるならば、
他のものも考慮が必要なことが多いでしょう。

デフォルトコンストラクタ以外の特別なメンバ関数を一つでも宣言すると、それが `=default` あるいは `=delete` 
であっても、ムーブコンストラクタとムーブ代入演算子の暗黙的な生成が抑止されます。

ムーブコンストラクタあるいはムーブ代入演算子を宣言すると、それが `=default` あるいは `=delete` 
であっても、暗黙的に生成されたコピーコンストラクタあるいは暗黙的に生成されたコピー代入演算子
を delete されたものとして定義することになります。

なので、これら特別な関数の一つでも宣言したら、他も全て宣言するべきです。そうしないと、
全ての潜在的なムーブをより高価なコピーに変えるとか、クラスをムーブオンリィにするなどの
期待されない効果を生むことになります。

##### 例。良くない

    struct M2 {   // bad: incomplete set of default operations
    public:
        // ...
        // ... no copy or move operations ...
        ~M2() { delete[] rep; }
    private:
        pair<int, int>* rep;  // zero-terminated set of pairs
    };

    void use()
    {
        M2 x;
        M2 y;
        // ...
        x = y;   // the default assignment
        // ...
    }

デストラクタで「特別の注意」が必要（ここでは、解放）が必要であったことを考えると、コピーとムーブ代入（どちらも暗黙的にオブジェクトを破壊します）が正しい可能性は小さいです（ここでは、二重削除になります）。

##### 注意

これは、"the rule of five" あるいは "the rule of six" として知られています。デフォルトコンストラクタを数えるかどうかによります。

##### 注意

あるデフォルト操作のデフォルト実装がほしい（他のを定義すると同時に）時は、`=default` と書けば、その関数に対してそういう意味になります。
デフォルト操作がいらない時は、`=delete` でそれを抑止しましょう。

##### 例。よろしい

`virtual` にするためにだけ、デストラクタを宣言する必要がある時は、それは、デフォルトを取る
ものとして定義することができます。暗黙的なムーブ操作が抑止されるのを避けるためには、それらも
宣言する必要があります。すると次に、クラスがムーブオンリィ（そしてコピー不可能）になるのを避けるために、
コピー操作を宣言しなくていけません。

    class AbstractBase {
    public:
      virtual ~AbstractBase() = default;
      AbstractBase(const AbstractBase&) = default;
      AbstractBase& operator=(const AbstractBase&) = default;
      AbstractBase(AbstractBase&&) = default;
      AbstractBase& operator=(AbstractBase&&) = default;
    };

あるいは、[C.67](#Rc-copy-virtual) に示すように、スライシングを避けるために、コピーとムーブ操作は全部削除することができます。

    class ClonableBase {
    public:
      virtual unique_ptr<ClonableBase> clone() const;
      virtual ~ClonableBase() = default;
      ClonableBase(const ClonableBase&) = delete;
      ClonableBase& operator=(const ClonableBase&) = delete;
      ClonableBase(ClonableBase&&) = delete;
      ClonableBase& operator=(ClonableBase&&) = delete;
    };

ここでは、ムーブ操作だけあるいはコピー操作だけを定義しても、同じ効果が得られます。しかし、
それぞれの特別なメンバに明示的に意図を述べることは、読み手にとってよりそれを明らかにします。

##### 注意

デストラクタを持つクラスで、暗黙的に生成されたコピー操作に依存するのは、非推奨です。
訳註。デストラクタを書いても、コピーコンストラクタとコピー代入演算子を暗黙的に生成するコンパイラが現在ありますが、
それは標準に準拠していないふるまいなので、安心しないように。

### <a name="Rc-matched"></a>C.22: デフォルト操作に一貫性を持たせよう

### <a name="Rc-dtor"></a>C.30: クラスが、オブジェクト解体で明示的なアクションが必要なら、デストラクタを定義しよう

### <a name="Rc-dtor-release"></a>C.31: クラスが確保した全ての資源は、そのクラスのデストラクタで解放されなくてはいけません

### <a name="Rc-dtor-ptr"></a>C.32: もしクラスが、生のポインタ (`T*`) あるいは参照 (`T&`) を持つなら、それは所有を意味するのか考えよう

### <a name="Rc-dtor-ptr2"></a>C.33: もしクラスが、所有者であるポインタメンバを持つなら、デストラクタを定義しよう

### <a name="Rc-dtor-virtual"></a>C.35: 基底クラスのデストラクタは、 public かつ virtual であるか、protected かつ virtual でないかのいずれかであるべきです

### <a name="Rc-dtor-fail"></a>C.36: デストラクタは失敗しないこと

##### 例

    class X {
    public:
        ~X() noexcept;
        // ...
    };

    X::~X() noexcept
    {
        // ...
        if (cannot_release_a_resource) terminate();
        // ...
    }

##### 注意

多くの人が、デストラクタでの失敗に対処する安全なしかけを発明しようと試みてきました。
誰も、一般的なしかけを得ることに成功しませんでした。
これは、本当に現実的な問題となることがあります。例えば、クローズしようとしないソケットはどうしましょう？
デストラクタを書く人は、なぜデストラクタが呼ばれたか知らないので、例外を投げて「実行を拒否する」ことはできません。
[discussion](#Sd-dtor) を参照ください。
問題をさらに悪くすることに、多くの、「クローズ／解放」操作はリトライ不可能です。
もしなんとか可能なら、クローズ／解放の失敗を基本的な設計の誤りと考えて、終了しましょう。

##### 注意

デストラクタは `noexcept` と宣言しよう。それは、デストラクタが正常に終わるか、プログラムを終了させることを保証します。

### <a name="Rc-dtor-noexcept"></a>C.37: デストラクタは `noexcept` にしよう

### <a name="Rc-ctor"></a>C.40: クラスが不変条件を持つなら、コンストラクタを定義しよう

### <a name="Rc-complete"></a>C.41: コンストラクタは、完全に初期化されたオブジェクトを作るべきです

##### 理由

コンストラクタは、クラスの不変条件を確立します。クラスの使用者は、構築されたオブジェクトが使用可能であることを前提とできるべきです。

##### 例、良くない

    class X1 {
        FILE* f;   // call init() before any other function
        // ...
    public:
        X1() {}
        void init();   // initialize f
        void read();   // read from f
        // ...
    };

    void f()
    {
        X1 file;
        file.read();   // crash or bad read!
        // ...
        file.init();   // too late
        // ...
    }

コンパイラはコメントを読みません。

##### 例外

コンストラクタで有効なオブジェクトを作成するのが難しい時は、 [ファクトリ関数を使おう](#Rc-factory)。

### <a name="Rc-throw"></a>C.42: コンストラクタで有効なオブジェクトを作ることができないなら、例外を投げよう

### <a name="Rc-default0"></a>C.43: コピー可能な (値型の) クラスはデフォルトコンストラクタを持つことを保証しよう

##### 理由

言語とライブラリの機能の多くは、要素を初期化するのにデフォルトコンストラクタに依存します。例えば、`T a[10]` と `std::vector<T> v(10)` 。
デフォルトコンストラクタはまた、コピー可能な型で、適切な「moved from」された状態を定義する作業を、しばしば、単純化します。

##### 例

    class Date { // BAD: no default constructor
    public:
        Date(int dd, int mm, int yyyy);
        // ...
    };

    vector<Date> vd1(1000);   // default Date needed here
    vector<Date> vd2(1000, Date{Month::October, 7, 1885});   // alternative

デフォルトコンストラクタは、ユーザ宣言されたコンストラクタが無い時にだけ、自動で生成されます。なので、上の例で、ベクトル `vd1` を初期化することは不可能です。
デフォルト値が無いことは、使用者を驚かせ、その使用を複雑にします。なので、合理的にそれを定義することができるなら、するべきです。

##### 注意

全てのメンバがデフォルトコンストラクタを持つクラスは、暗黙的にデフォルトコンストラクタを得ます。

    struct X {
        string s;
        vector<int> v;
    };

    X x; // means X{{}, {}}; that is the empty string and the empty vector

組み込み型は、適切にデフォルトで構築されないことに注意ください。

    struct X {
        string s;
        int i;
    };

    void f()
    {
        X x;    // x.s is initialized to the empty string; x.i is uninitialized

        cout << x.s << ' ' << x.i << '\n';
        ++x.i;
    }

Static に確保された組み込み型のオブジェクトは、デフォルトで、`0` に初期化されます。しかし、ローカルな組み込み型変数はそうではありません。
あなたのコンパイラは、ローカルな組み込み型変数をデフォルトで初期化することがあるかもしれませんが、最適化ビルドではそうしないかもしれないことに注意ください。
なので、上の例のようなコードは動くように見えるかもしれませんが、それは未定義の振る舞いに依存しています。
あなたが初期化を必要とするならば、明示的なデフォルト初期化が役に立ちます：

    struct X {
        string s;
        int i {};   // default initialize (to 0)
    };

### <a name="Rc-default00"></a>C.44: デフォルトコンストラクタは、単純で例外を投げないことしよう

### <a name="Rc-default"></a>C.45: データメンバを初期化するだけのデフォルトコンストラクタを定義しないこと；クラス内メンバ初期化子をその代わりに使おう

##### 理由

クラス内メンバ初期化子を使うと、コンパイラはあなたの代わりに関数を生成します。コンパイラが生成した関数はより効率的なことがあります。

##### 例、良くない

    class X1 { // BAD: doesn't use member initializers
        string s;
        int i;
    public:
        X1() :s{"default"}, i{1} { }
        // ...
    };

##### 例

    class X2 {
        string s = "default";
        int i = 1;
    public:
        // use compiler-generated default constructor
        // ...
    };

### <a name="Rc-explicit"></a>C.46: デフォルトで、一つの引数を取るコンストラクタは explicit と宣言しよう

### <a name="Rc-order"></a>C.47: メンバ変数は、メンバ宣言の順に、定義し初期化しよう

### <a name="Rc-in-class-initializer"></a>C.48: 定数を初期化するには、コンストラクタでのメンバ初期化子より、クラス内初期化子を選ぼう

##### 理由

全てのコンストラクタで、同じ値を使うことが期待されることを明示的にします。繰り返しを避けます。メンテナンスの問題を避けます。最も短く、最も効率的なコードになります。

##### 例、良くない

    class X {   // BAD
        int i;
        string s;
        int j;
    public:
        X() :i{666}, s{"qqq"} { }   // j is uninitialized
        X(int ii) :i{ii} {}         // s is "" and j is uninitialized
        // ...
    };

メンテナは、`j` が意図的に初期化されていない（いずれにしても、多分、良くない考えです）のか、どうやってわかるでしょう？
ある場合に、`s` にデフォルト値 `""` を与えて、他のときには `qqq` を与えたのは意図されたことでしょうか（ほぼ間違いなくバグ）？
`j` の問題（メンバを初期化するのを忘れる）は、既存のクラスに新しいメンバを加える時にしばしば起こります。

##### 例

    class X2 {
        int i {666};
        string s {"qqq"};
        int j {0};
    public:
        X2() = default;        // all members are initialized to their defaults
        X2(int ii) :i{ii} {}   // s and j initialized to their defaults
        // ...
    };

**代替策**: コンストラクタへのデフォルト引数で、部分的な効果は得られます。そしてそれは、古いコードではよく見かけました。
しかし、それはあまり明示的ではなく、より多くの引数を渡す必要があり、一つ以上のコンストラクタがある時は繰り返しが必要です。

    class X3 {   // BAD: inexplicit, argument passing overhead
        int i;
        string s;
        int j;
    public:
        X3(int ii = 666, const string& ss = "qqq", int jj = 0)
            :i{ii}, s{ss}, j{jj} { }   // all members are initialized to their defaults
        // ...
    };

### <a name="Rc-initialize"></a>C.49: コンストラクタでは、代入より初期化を選ぼう

##### Example, good

    class A {   // Good
        string s1;
    public:
        A() : s1{"Hello, "} { }    // GOOD: directly construct
        // ...
    };

##### Example, bad

    class B {   // BAD
        string s1;
    public:
        B() { s1 = "Hello, "; }   // BAD: default constructor followed by assignment
        // ...
    };

    class C {   // UGLY, aka very bad
        int* p;
    public:
        C() { cout << *p; p = new int{10}; }   // accidental use before initialized
        // ...
    };

### <a name="Rc-factory"></a>C.50: 初期化の間に、「virtual」なふるまいが必要なら、ファクトリ関数を使おう

##### Reason

もし基底クラスオブジェクトの状態が、そのオブジェクトの派生部分の状態に依存しなくてはいけない時は、仮想関数（あるいは同等のもの）を使う必要があります。
同時に、不完全に構築されたオブジェクトを誤って使う機会のウィンドウを最小にしなくてはいけません。

##### Example

    class B {
    protected:
        B() { /* ... */ }              // create an imperfectly initialized object

        virtual void PostInitialize()  // to be called right after construction
        {
            // ...
            f();    // GOOD: virtual dispatch is safe
            // ...
        }

    public:
        virtual void f() = 0;

        template<class T>
        static shared_ptr<T> Create()  // interface for creating shared objects
        {
            auto p = make_shared<T>();
            p->PostInitialize();
            return p;
        }
    };

    class D : public B { /* ... */ };  // some derived class

    shared_ptr<D> p = D::Create<D>();  // creating a D object

コンストラクタを `protected` にすることで、不完全に構築されたオブジェクトが荒野に逃げ出すのを防ぎます。
`Create()` ファクトリ関数を提供することで、（フリーストア上の）コンストラクションを便利にします。

### <a name="Rc-delegating"></a>C.51: クラスの全てのコンストラクタに共通するアクションを表すには、委譲コンストラクタを使おう

### <a name="Rc-inheriting"></a>C.52: 派生クラスでそれ以上の明示的な初期化が必要ない時は、継承したコンストラクタを使ってコンストラクタをインポートしよう

### <a name="Rc-copy-assignment"></a>C.60: コピー代入は non-`virtual` とし、引数は `const&` で取り、戻り値は non-`const&` としよう

### <a name="Rc-copy-semantic"></a>C.61: コピー操作はコピーをするべきです

### <a name="Rc-copy-self"></a>C.62: コピー代入は自己代入に対して安全にしよう

### <a name="Rc-move-assignment"></a>C.63: ムーブ代入は non-`virtual` とし、引数は `&&` で取り、戻り値は non-`const &` としよう

### <a name="Rc-move-semantic"></a>C.64: ムーブ操作はムーブをするべきで、そのムーブ元は有効な状態のままとするべきです

### <a name="Rc-move-self"></a>C.65: ムーブ代入は自己代入に対して安全にしよう

### <a name="Rc-move-noexcept"></a>C.66: ムーブ操作は `noexcept` にしよう

### <a name="Rc-copy-virtual"></a>C.67: 基底クラスはコピーを禁止するべきで、「コピー操作」が望ましいならその代わりに仮想 `clone` を提供するべきです

### <a name="Rc-eqdefault"></a>C.80: デフォルトセマンティクスを使うことを明示的にする必要があるなら、 `=default` を使おう

### <a name="Rc-delete"></a>C.81: デフォルトのふるまいを無効にしたい（代替策が不要で）なら `=delete` を使おう

### <a name="Rc-ctor-virtual"></a>C.82: コンストラクタとデストラクタで仮想関数を呼ばないこと

##### Reason

呼ばれる関数は、派生クラスがオーバライドしたかもしれない関数でなく、これまでに構築されたオブジェクトのものとなるでしょう。
これはとても混乱させます。
さらに悪いことに、未実装の純粋仮想関数を、コンストラクタあるいはデストラクタから直接あるいは間接的に呼ぶことは、未定義の振る舞いとなります。

##### Example, bad

    class Base {
    public:
        virtual void f() = 0;   // not implemented
        virtual void g();       // implemented with Base version
        virtual void h();       // implemented with Base version
    };

    class Derived : public Base {
    public:
        void g() override;   // provide Derived implementation
        void h() final;      // provide Derived implementation

        Derived()
        {
            // BAD: attempt to call an unimplemented virtual function
            f();

            // BAD: will call Derived::g, not dispatch further virtually
            g();

            // GOOD: explicitly state intent to call only the visible version
            Derived::g();

            // ok, no qualification needed, h is final
            h();
        }
    };

明示的に修飾された特定の関数を呼ぶことは、その関数が `virtual` であっても、仮想呼び出しではないことに注意ください。

### <a name="Rc-swap"></a>C.83: 値型のような型では、 `noexcept` swap 関数を提供することを考慮しよう

### <a name="Rc-swap-fail"></a>C.84: `swap` 関数は失敗しないこと

### <a name="Rc-swap-noexcept"></a>C.85: `swap` は `noexcept` にしよう

### <a name="Rc-eq"></a>C.86: `==` は、オペランド型に対して対称的とし、 `noexcept` にしよう

### <a name="Rc-eq-base"></a>C.87: 基底クラスでの `==` に注意

### <a name="Rc-hash"></a>C.89: `hash` は `noexcept` にしよう

### <a name="Rh-domain"></a>C.120: クラス階層は、本質的に階層的な構造を持つ概念を表現するために使おう（その時に限り）

### <a name="Rh-abstract"></a>C.121: 基底クラスがインタフェースとして使われるなら、それを純粋抽象クラスにしよう

### <a name="Rh-separation"></a>C.122: インタフェースと実装の完全な分離が必要な時は、抽象クラスをインタフェースとして使おう

### <a name="Rh-abstract-ctor"></a>C.126: 抽象クラスは典型的にはコンストラクタがいりません

### <a name="Rh-dtor"></a>C.127: 仮想関数を持つクラスは、virtual あるいは protected デストラクタを持つべきです

##### Example, bad

    struct B {
        virtual int f() = 0;
        // ... no user-written destructor, defaults to public nonvirtual ...
    };

    // bad: derived from a class without a virtual destructor
    struct D : B {
        string s {"default"};
    };

    void use()
    {
        unique_ptr<B> p = make_unique<D>();
        // ...
    } // undefined behavior. May call B::~B only and leak the string

### <a name="Rh-override"></a>C.128: 仮想関数は、`virtual`, `override`, あるいは `final` の１つだけを必ず指定するべきです

### <a name="Rh-kind"></a>C.129: クラス階層を設計する時、実装の継承とインタフェースの継承を区別しよう

### <a name="Rh-copy"></a>C.130: 基底クラスではコピーを再定義するか、禁止しよう；その代わりに仮想 `clone` 関数を選ぼう

### <a name="Rh-get"></a>C.131: 自明な getter と setter を避けよう

##### Example

    class Point {   // Bad: verbose
        int x;
        int y;
    public:
        Point(int xx, int yy) : x{xx}, y{yy} { }
        int get_x() const { return x; }
        void set_x(int xx) { x = xx; }
        int get_y() const { return y; }
        void set_y(int yy) { y = yy; }
        // no behavioral member functions
    };

このようなクラスは、 `struct` にすることを考えましょう。-- つまり、振る舞いを持たない、変数の集まりで、全てが public データでメンバ関数がなし、です。

    struct Point {
        int x {0};
        int y {0};
    };

##### Note

この規則の鍵は、getter/setter セマンティクスが自明かどうかです。以下は「自明」の完全な定義ではありませんが、getter/setter の代わりに public データメンバであったら、シンタックス以外で何か違いがあるかを考えましょう。自明でないセマンティクスの例は：クラス不変条件を維持する、あるいは、内部的な型と、インタフェース型を変換するなど。

### <a name="Rh-virtual"></a>C.132: 関数を意味なく仮想とするのはやめよう

##### Reason

冗長な `virtual` は、実行時間とオブジェクトコードの大きさを増します。
仮想関数はオーバライドされる可能性があり、このため、派生クラスでの誤りにさらされます。
仮想関数はテンプレート階層中で、必ずコードの複製を起こします。

##### Example, bad

    template<class T>
    class Vector {
    public:
        // ...
        virtual int size() const { return sz; }   // bad: what good could a derived class do?
    private:
        T* elem;   // the elements
        int sz;    // number of elements
    };

この種の "vector" はそもそも、基底クラスとして使われることは意図されていません。

### <a name="Rh-protected"></a>C.133: `protected` データを避けよう

### <a name="Rh-public"></a>C.134: 全ての non-`const` データメンバが同じアクセスレベルを持つことを保証しよう

### <a name="Rh-mi-interface"></a>C.135: 複数の異なるインタフェースを表すために、多重継承を使おう

### <a name="Rh-mi-implementation"></a>C.136: 実装上の属性のユニオンを表すために、多重継承を使おう

### <a name="Rh-vbase"></a>C.137: 一般的すぎる基底クラスを避けるために、 `virtual` 基底を使おう

### <a name="Rh-using"></a>C.138: `using` で、派生クラスとその基底に対して多重定義のセットを作ろう

### <a name="Rh-final"></a>C.139: `final` はほどほどに使おう

### <a name="Rh-poly"></a>C.145: 多相的なオブジェクトは、ポインタと参照を使ってアクセスしよう

##### Example

    struct B { int a; virtual int f(); };
    struct D : B { int b; int f() override; };

    void use(B b)
    {
        D d;
        B b2 = d;   // slice
        B b3 = b;
    }

    void use2()
    {
        D d;
        use(d);   // slice
    }

`d` はどちらもスライスされます。

### <a name="Rh-dynamic_cast"></a>C.146: クラス階層を横断することが避けられない時は `dynamic_cast` を使おう

### <a name="Rh-ref-cast"></a>C.147: 目的のクラスが見つからない時がエラーとみなされる時は、参照型への `dynamic_cast` を使おう

### <a name="Rh-ptr-cast"></a>C.148: 目的のクラスが見つからない時が有効な選択肢とみなされる時は、ポインタ型への `dynamic_cast` を使おう

### <a name="Rh-smart"></a>C.149: `new` を使って作成したオブジェクトを `delete` するのを忘れるのを避けるために `unique_ptr` あるいは `shared_ptr` を使おう

### <a name="Rh-make_unique"></a>C.150: `unique_ptr` が所有するオブジェクトを作成するために `make_unique()` を使おう

### <a name="Rh-make_shared"></a>C.151: `shared_ptr` が所有するオブジェクトを作成するために `make_shared()` を使おう

##### 理由

`make_shared` を使うと、構築がより簡潔な文になります。
それはまた、`shared_ptr` の参照カウンタをそのオブジェクトの隣に置くことによって、参照カウンタが別に確保されることを
避ける利点もあります。

##### 例

    void test() {
        // OK: but repetitive; and separate allocations for the Bar and shared_ptr's use count
        shared_ptr<Bar> p {new<Bar>{7}};

        auto q = make_shared<Bar>(7);   // Better: no repetition of Bar; one object
    }

### <a name="Rh-array"></a>C.152: 決して、派生クラスのオブジェクトの配列へのポインタを、その基底へのポインタに代入しないこと

##### Example

    struct B { int x; };
    struct D : B { int y; };

    void use(B*);

    D a[] = {{1, 2}, {3, 4}, {5, 6}};
    B* p = a;     // bad: a decays to &a[0] which is converted to a B*
    p[1].x = 7;   // overwrite D[0].y

    use(a);       // bad: a decays to &a[0] which is converted to a B*

### <a name="Rh-use-virtual"></a>C.153: キャストより仮想関数を選ぼう

### <a name="Ro-conventional"></a>C.160: 演算子は、主に、一般的な使い方をまねるために定義しよう

### <a name="Ro-symmetric"></a>C.161: 対称的な操作のため、メンバでない関数を使おう

##### 理由

メンバ関数を使うと、２つのことが必要です。
例えば、 `==` の場合、 `a == b` と `b == a` は、微妙に違います。

##### 例

    bool operator==(Point a, Point b) { return a.x == b.x && a.y == b.y; }

### <a name="Ro-equivalent"></a>C.162: ほぼ等しい操作は多重定義しよう

### <a name="Ro-equivalent-2"></a>C.163: ほぼ等しい操作だけを多重定義しよう

### <a name="Ro-conversion"></a>C.164: 変換操作を避けよう

### <a name="Ro-custom"></a>C.165: カスタマイズするところで、 `using` を使おう

### <a name="Ro-address-of"></a>C.166: 単行演算子 `&` を多重定義するのは、スマートポインタと参照のシステムの一部である時にだけとしよう

### <a name="Ro-overload"></a>C.167: 慣用的な意味を持つ操作には、その演算子を使おう

### <a name="Ro-namespace"></a>C.168: 多重定義する演算子は、そのオペランドの名前空間で定義しよう

### <a name="Ro-lambda"></a>C.170: ラムダを多重定義したいときは、ジェネリックラムダを使おう

### <a name="Ru-union"></a>C.180: メモリを節約するために `union` を使おう

### <a name="Ru-naked"></a>C.181: 「裸の」 `union` を避けよう

### <a name="Ru-anonymous"></a>C.182: タグ付きの `union` を実装するために、無名 `union` を使おう

### <a name="Ru-pun"></a>C.183: `union` を使って型変換をしないこと

### <a name="Renum-macro"></a>Enum.1: マクロより列挙子を選ぼう

### <a name="Renum-set"></a>Enum.2: 関連する、名前がついた定数のセットを表すために列挙子を使おう

### <a name="Renum-class"></a>Enum.3: 「ただの」 enum より、class enum を選ぼう

### <a name="Renum-oper"></a>Enum.4: 列挙子に操作を定義して、安全で使いやすいしよう

### <a name="Renum-caps"></a>Enum.5: 列挙子を `ALL_CAPS` 、全部大文字、にしないこと

### <a name="Renum-unnamed"></a>Enum.6: 無名の列挙子を避けよう

### <a name="Renum-underlying"></a>Enum.7: 列挙子の元となる型を指定するのはその必要があるときだけにしよう

### <a name="Renum-value"></a>Enum.8: 列挙子の値を指定するのはその必要があるときだけにしよう

##### Example

    enum class Col1 { red, yellow, blue };
    enum class Col2 { red = 1, yellow = 2, blue = 2 }; // typo
    enum class Month { jan = 1, feb, mar, apr, may, jun,
                       jul, august, sep, oct, nov, dec }; // starting with 1 is conventional
    enum class Base_flag { dec = 1, oct = dec << 1, hex = dec << 2 }; // set of bits

慣用的な値（例えば、`Month`）に合わせる時と、連続した値ではいけない場合（例えば、`Base_flag` での別々のビット）は、値を指定する必要があります。

### <a name="Rr-raii"></a>R.1: 資源ハンドルとRAII (Resource Acquisition Is Initialization、資源獲得時初期化)を使って資源を自動的に管理しよう

### <a name="Rr-use-ptr"></a>R.2: インタフェースでは、個々のオブジェクトを指定するために生のポインタを使おう（その時に限り）

### <a name="Rr-ptr"></a>R.3: 生のポインタ (`T*`) は所有を示しません

### <a name="Rr-ref"></a>R.4: 生の参照 (`T&`) は所有を示しません

### <a name="Rr-scoped"></a>R.5: スコープのあるオブジェクトを選ぼう；不必要なヒープからの確保はやめよう

##### Example

以下の例は非効率（不要な確保と解放があるため）で、`...` の部分で例外が投げられたあるいは return された場合に脆弱（リークになります）で、冗長です。

    void f(int n)
    {
        auto p = new Gadget{n};
        // ...
        delete p;
    }

その代わり、ローカル変数を使おう：

    void f(int n)
    {
        Gadget g{n};
        // ...
    }

### <a name="Rr-global"></a>R.6: `const` でないグローバル変数を避けよう

### <a name="Rr-mallocfree"></a>R.10: `malloc()` と `free()` を避けよう

### <a name="Rr-newdelete"></a>R.11: 明示的に `new` と `delete` を呼ぶのを避けよう

### <a name="Rr-immediate-alloc"></a>R.12: 明示的な資源確保の結果は、直ちに管理オブジェクトに渡そう

### <a name="Rr-single-alloc"></a>R.13: 一つの式の中では、最大一つの明示的な資源確保をしよう

### <a name="Rr-ap"></a>R.14: ??? 配列対ポインタ引数

### <a name="Rr-pair"></a>R.15: 対になる確保と解放は必ず両方、多重定義しよう

### <a name="Rr-owner"></a>R.20: 所有を示すため、 `unique_ptr` あるいは `shared_ptr` を使おう

### <a name="Rr-unique"></a>R.21: 所有権を共有する必要がなければ、`shared_ptr` より `unique_ptr` を使おう

##### 理由

`unique_ptr` は概念的により単純で、かつ、より予測可能で（破壊がいつ起きるかわかります）、
かつ、より高速（使用カウンタを暗黙的に維持しません）です。

##### 例。良くない

これは不必要に参照カウンタを加え、維持します。

    void f()
    {
        shared_ptr<Base> base = make_shared<Derived>();
        // use base locally, without copying it -- refcount never exceeds 1
    } // destroy base

##### 例

これはより効率的です:

    void f()
    {
        unique_ptr<Base> base = make_unique<Derived>();
        // use base locally
    } // destroy base

### <a name="Rr-make_shared"></a>R.22: `shared_ptr` は `make_shared()` で作ろう

### <a name="Rr-make_unique"></a>R.23: `unique_ptr` は `make_unique()` で作ろう

### <a name="Rr-weak_ptr"></a>R.24: `shared_ptr` の循環を断ち切るために、`std::weak_ptr` を使おう

### <a name="Rr-smartptrparam"></a>R.30: 引数にスマートポインタを取るのは明示的に存在期間セマンティクスを表す必要のある時だけにしよう

### <a name="Rr-smart"></a>R.31: 標準にないスマートポインタを使う時は、 `std` の基本的なパターンに従おう

### <a name="Rr-uniqueptrparam"></a>R.32: `unique_ptr<widget>` 引数を取って、関数が `widget` の所有権を前提とすることを表そう

### <a name="Rr-reseat"></a>R.33: `unique_ptr<widget>&` 引数を取って、関数が `widget` を reseat することを表そう

### <a name="Rr-sharedptrparam-owner"></a>R.34: `shared_ptr<widget>` 引数を取って、関数が widget の所有者の一部であることを表そう

### <a name="Rr-sharedptrparam"></a>R.35: `shared_ptr<widget>&` 引数を取って、関数がその共用ポインタを reseat する可能性のあることを表そう

### <a name="Rr-sharedptrparam-const"></a>R.36: `const shared_ptr<widget>&` 引数を取って、それがそのオブジェクトへの参照カウントを保持し続ける可能性があることを表そう

### <a name="Rr-smartptrget"></a>R.37: エイリアスしたスマートポインタから得たポインタあるいは参照を渡さないこと

##### Example

このコードを考えましょう:

    // global (static or heap), or aliased local ...
    shared_ptr<widget> g_p = ...;

    void f(widget& w)
    {
        g();
        use(w);  // A
    }

    void g()
    {
        g_p = ...; // oops, if this was the last shared_ptr to that widget, destroys the widget
    }

以下はコードレビューを通るべきではありません:

    void my_code()
    {
        // BAD: passing pointer or reference obtained from a nonlocal smart pointer
        //      that could be inadvertently reset somewhere inside f or it callees
        f(*g_p);

        // BAD: same reason, just passing it as a "this" pointer
         g_p->func();
    }

### <a name="Res-lib"></a>ES.1: 他のライブラリや「手作りコード」より標準ライブラリを選ぼう

### <a name="Res-abstr"></a>ES.2: 言語機能を直接使うより、適切な抽象化を選ぼう

### <a name="Res-scope"></a>ES.5: スコープを小さく保とう

### <a name="Res-cond"></a>ES.6: for 文の初期化子と条件で名前を宣言し、スコープを制限しよう

### <a name="Res-name-length"></a>ES.7: 一般的でローカルな名前は短く、一般的でなくローカルでない名前は長くしよう

### <a name="Res-name-similar"></a>ES.8: 似て見える名前を避けよう

### <a name="Res-not-CAPS"></a>ES.9: `ALL_CAPS` 、全部大文字の名前を避けよう

### <a name="Res-name-one"></a>ES.10: 一つの宣言では一つ（だけ）名前を宣言しよう

### <a name="Res-auto"></a>ES.11: 型名の冗長な繰り返しを避けるため `auto` を使おう

##### Example

これを見て:

    auto p = v.begin();   // vector<int>::iterator
    auto h = t.future();
    auto q = make_unique<int[]>(s);
    auto f = [](int x){ return x + 10; };

どの場合も、長くて、覚えるのが大変で、コンパイラは既に知っているのにプログラマが間違える可能性のある型を書かなくて済みます。

##### Example

    template<class T>
    auto Container<T>::first() -> Iterator;   // Container<T>::Iterator

##### Exception

初期化リストで、あなたが正確に自分がほしい型を知っていて、初期化子が変換を必要とすることがある場合には、`auto` を避けよう。

##### Example

    auto lst = { 1, 2, 3 };   // lst is an initializer list
    auto x{1};   // x is an int (after correction of the C++14 standard; initializer_list in C++11)

### <a name="Res-reuse"></a>ES.12: ネストしたスコープ内で名前を再使用しないこと

### <a name="Res-always"></a>ES.20: オブジェクトは常に初期化しよう

##### 例

    void use(int arg)
    {
        int i;   // bad: uninitialized variable
        // ...
        i = 7;   // initialize i
    }

違います。`i = 7` は `i` を初期化しません。それに代入しているのです。さらに、`i` は、`...` の部分で読むことができます。正しくは：

    void use(int arg)   // OK
    {
        int i = 7;   // OK: initialized
        string s;    // OK: default initialized
        // ...
    }

##### 注意

*常に初期化しよう* 規則は、 *オブジェクトは使う前に設定されなくてはいけません* 言語規則より、意図的に強いです。
後者はよりゆるい規則で、技術的なバグを捉えます。しかし：

* それは読みにくいコードにつながります
* それは人々に名前を必要以上に大きいスコープで宣言することを許します
* それは複雑なコードを許し、論理的なバグを生みます
* それはリファクタリングを妨げます

*常に初期化しよう* 規則は、メンテナンス可能性を高めることを目的としたスタイルの規則であるとともに、設定する前に使う誤りを防ぐための規則です。

##### 例外

すぐに入力から初期化される予定のオブジェクトを宣言する時は、それを初期化するのは、二重の初期化になります。
しかし、これは、入力を超えた部分に、初期化されていないデータを残すことがあるのに注意ください。-- そしてそれは多くのエラーとセキュリティ侵害の源となってきました。

    constexpr int max = 8 * 1024;
    int buf[max];         // OK, but suspicious: uninitialized
    f.read(buf, max);

状況によっては、この配列を初期化するコストは大きいかもしれません。
しかし、そのような例は実際に、初期化されていないデータをアクセス可能として残す傾向があるので、疑いを持って扱うべきです。

    constexpr int max = 8 * 1024;
    int buf[max] = {};   // zero all elements; better in some situations
    f.read(buf, max);

### <a name="Res-introduce"></a>ES.21: 使う必要が起きる前に変数（あるいは定数）を導入しないこと

### <a name="Res-init"></a>ES.22: 変数を初期化する値を得る前に変数を宣言しないこと

##### 理由

読みやすさ。変数を使うことができるスコープを制限する。設定される前に使う危険をおかさないこと。初期化は、しばしば、代入よりずっと効率的です。

##### 例、良くない

    string s;
    // ... no use of s here ...
    s = "what a waste";

##### 例、良くない

    SomeLargeType var;   // ugly CaMeLcAsEvArIaBlE

    if (cond)   // some non-trivial condition
        Set(&var);
    else if (cond2 || !cond3) {
        var = Set2(3.14);
    }
    else {
        var = 0;
        for (auto& e : something)
            var += e;
    }

    // use var; that this isn't done too early can be enforced statically with only control flow

`SomeLargeType` がそれほど高価でないデフォルト初期化を持つなら、これは問題ではありません。
そうでない時は、迷路のような条件を通る全ての可能なパスがカバーされたかどうかを、プログラマは心配に思うでしょう。
カバーされない時は、「設定される前に使う」バグになります。これはメンテナンスのわなです。

訳註。デフォルトコンストラクタが高価であってもなくてもこういうコードは現実には避けられないし、カバレッジの問題は別ですよね。

`const` 変数を含むほどほどの複雑さの初期化のためには、初期化を表すために、ラムダを使うことを考えよう。[ES.28](#Res-lambda-init) を参照。

### <a name="Res-list"></a>ES.23: `{}` 初期化子シンタックスを選ぼう

##### 例

    int x {f(99)};
    vector<int> v = {1, 2, 3, 4, 5, 6};

##### 例外

コンテナでは、 `{...}` を要素のリストに、 `(...)` をサイズに使う伝統があります。

    vector<int> v1(10);    // vector of 10 elements with the default value 0
    vector<int> v2 {10};   // vector of 1 element with the value 10

### <a name="Res-unique"></a>ES.24: ポインタを持つには `unique_ptr<T>` を使おう

### <a name="Res-const"></a>ES.25: 後で値を変更したいと思わないなら、オブジェクトは `const` あるいは `constexpr` と宣言しよう

### <a name="Res-recycle"></a>ES.26: ２つの無関係な目的のために一つの変数を使わないこと

### <a name="Res-stack"></a>ES.27: スタック上の配列は、`std::array` あるいは `stack_array` を使おう

### <a name="Res-lambda-init"></a>ES.28: 複雑な初期化、特に `const` 変数、のためにはラムダを使おう

### <a name="Res-macros"></a>ES.30: プログラムテキストを操作するためにマクロを使わないこと

##### Example, bad

    #define Case break; case   /* BAD */

### <a name="Res-macros2"></a>ES.31: 定数や「関数」のためにマクロを使わないこと

### <a name="Res-ALL_CAPS"></a>ES.32: マクロ名には `ALL_CAPS` 、全て大文字、を使おう

### <a name="Res-MACROS"></a>ES.33: マクロを使わなくてはいけない時は、一意の名前をつけよう

### <a name="Res-ellipses"></a> ES.34: (C-スタイルの) 可変引数関数を定義しないこと

### <a name="Res-complicated"></a>ES.40: 複雑な式を避けよう

### <a name="Res-parens"></a>ES.41: 演算子の優先順位に疑問がある時は、かっこをつけよう

### <a name="Res-ptr"></a>ES.42: ポインタの使用は単純で単刀直入としよう

### <a name="Res-order"></a>ES.43: 評価の順序が未定義となる式を避けよう

### <a name="Res-order-fct"></a>ES.44: 関数引数の評価の順序に依存しないこと

### <a name="Res-magic"></a>ES.45: 「マジック定数」を避けよう；シンボリック定数を使おう

### <a name="Res-narrowing"></a>ES.46: 損失のある (narrowing, truncating) 算術変換を避けよう

### <a name="Res-nullptr"></a>ES.47: `0` あるいは `NULL` でなく `nullptr` を使おう

### <a name="Res-casts"></a>ES.48: キャストを避けよう

### <a name="Res-casts-named"></a>ES.49: キャストをしなくてはいけない時は、名前のあるキャストを使おう

### <a name="Res-casts-const"></a>ES.50: `const` をキャストして取り除かないこと

### <a name="Res-range-checking"></a>ES.55: 範囲チェックの必要性を避けよう

### <a name="Res-move"></a>ES.56: `std::move()` は、オブジェクトを明示的に他のスコープに移動する必要のある時だけ使おう

##### Example, bad

    vector<int> make_vector() {
        vector<int> result;
        // ... load result with data
        return std::move(result);       // bad; just write "return result;"
    }

決して、 `return move(local_variable);` と書かないこと。なぜならば言語は既にその変数がムーブ候補であることを知っているからです。
このコードで `move` を書いても役に立ちません。そして実際に、有害です。
コンパイラによっては、それは、ローカル変数への余分な参照エイリアスを作ることによって、RVO (the return value optimization) と干渉するからです。

##### Example, bad

    vector<int> v = std::move(make_vector());   // bad; the std::move is entirely redundant

`f` が値を戻す時、決して、`x = move(f());` のように、戻される値に対して `move` を書かないこと。
言語は既に、戻される値が一時オブジェクトであり、moved from することができることを知っています。

### <a name="Res-new"></a>ES.60: 資源管理関数の外での `new` と `delete` を避けよう

### <a name="Res-del"></a>ES.61: 配列は `delete[]` で削除し、配列でないものは `delete` で削除しよう

### <a name="Res-arr2"></a>ES.62: 異なる配列の間で、ポインタの比較をしないこと

### <a name="Res-slice"></a>ES.63: スライスしないこと

### <a name="Res-construct"></a>ES.64: コンストラクタは `T{e}` ノーテーションを使おう

### <a name="Res-deref"></a>ES.65: 不正なポインタを参照外ししないこと

### <a name="Res-switch-if"></a>ES.70: 選択の余地があるなら、 `if` 文より `switch` 文を選ぼう

### <a name="Res-for-range"></a>ES.71: 選択の余地があるなら、`for` 文より範囲 `for` 文を選ぼう

### <a name="Res-for-while"></a>ES.72: 明らかなループ変数がある時は、`while` 文より `for` 文を選ぼう

### <a name="Res-while-for"></a>ES.73: 明らかなループ変数がない時は、`for` 文より `while` 文を選ぼう

### <a name="Res-for-init"></a>ES.74: `for` 文の初期化部分でループ変数を宣言するようにしよう

##### Example

    for (int i = 0; i < 100; ++i) {   // GOOD: i var is visible only inside the loop
        // ...
    }

##### Example, don't

    int j;                            // BAD: j is visible outside the loop
    for (j = 0; j < 100; ++j) {
        // ...
    }
    // j is still visible here and isn't needed

### <a name="Res-do"></a>ES.75: `do` 文を避けよう

##### Note

はい。`do` 文が、解決策を明確に表すことを示すちゃんとした例はあります。しかし、多くのバグの元でもあります。

### <a name="Res-goto"></a>ES.76: `goto` を避けよう

##### 例外

ネストしたループから抜け出る時。その場合、常に、前方にジャンプすること。

    for (int i = 0; i < imax; ++i)
        for (int j = 0; j < jmax; ++j) {
            if (a[i][j] > elem_max) goto finished;
            // ...
        }
    finished:
    // ...

### <a name="Res-continue"></a>ES.77: ループでの `break` と `continue` の使用は最小としよう

### <a name="Res-break"></a>ES.78: 空でない `case` は常に `break` で終わらせよう

### <a name="Res-default"></a>ES.79: 一般的な場合を扱うために（その時に限り） `default` を使おう

### <a name="Res-noname"></a>ES.84: 名前のないローカル変数を宣言し（ようと試み）ないこと

### <a name="Res-empty"></a>ES.85: 空の文は目立つようにしよう

##### Example

    for (i = 0; i < max; ++i);   // BAD: the empty statement is easily overlooked
    v[i] = f(v[i]);

    for (auto x : v) {           // better
        // nothing
    }
    v[i] = f(v[i]);

### <a name="Res-loop-counter"></a>ES.86: 生の for ループの本体内で、ループ制御変数を変更するのは避けよう

##### Example

    for (int i = 0; i < 10; ++i) {
        // no updates to i -- ok
    }

    for (int i = 0; i < 10; ++i) {
        //
        if (/* something */) ++i; // BAD
        //
    }

    bool skip = false;
    for (int i = 0; i < 10; ++i) {
        if (skip) { skip = false; continue; }
        //
        if (/* something */) skip = true;  // Better: using two variable for two concepts.
        //
    }

### <a name="Res-if"></a>ES.87: 条件に冗長な `==` あるいは `!=` をつけないこと

##### Example

定義により、 `if` 文, `while` 文, あるいは `for`- 文にある条件は、 `true` と `false` のいずれかを選びます。
数型は `0` と比較され、ポインタ型は `nullptr` と比較されます。

    // These all mean "if `p` is not `nullptr`"
    if (p) { ... }            // good
    if (p != 0) { ... }       // redundant `!=0`; bad: don't use 0 for pointers
    if (p != nullptr) { ... } // redundant `!=nullptr`, not recommended

### <a name="Res-mix"></a>ES.100: 符号ありと符号なしの算術を混ぜないこと

### <a name="Res-unsigned"></a>ES.101: ビット操作には符号なしの型を使おう

### <a name="Res-signed"></a>ES.102: 算術には符号ありの型を使おう

### <a name="Res-overflow"></a>ES.103: オーバーフローしないこと

### <a name="Res-underflow"></a>ES.104: アンダーフローしないこと

### <a name="Res-zero"></a>ES.105: ゼロで割り算をしないこと

### <a name="Res-nonnegative"></a>ES.106: 符号なしを使うことで、負数を避けようとしないこと

### <a name="Res-subscripts"></a>ES.107: 添字に符号なしを使わないこと；`gsl::index` を選ぼう 

### <a name="Rper-reason"></a>Per.1: 理由なしに最適化しないこと

### <a name="Rper-Knuth"></a>Per.2: 早すぎる最適化はしないこと

### <a name="Rper-critical"></a>Per.3: 性能にクリティカルでないものを最適化しないこと

### <a name="Rper-simple"></a>Per.4: 複雑なコードは単純なコードに比べて必然的に速いと思わないこと

### <a name="Rper-low"></a>Per.5: 低レベルのコードは高レベルのコードに比べて必然的に速いと思わないこと

### <a name="Rper-measure"></a>Per.6: 測定しないで性能を論じないこと

### <a name="Rper-efficiency"></a>Per.7: 最適化を可能とするように設計しよう

### <a name="Rper-type"></a>Per.10: 静的な型システムに依存しよう

### <a name="Rper-Comp"></a>Per.11: 計算を、実行時からコンパイル時に移動しよう

### <a name="Rper-alias"></a>Per.12: 冗長な aliase を除こう

### <a name="Rper-indirect"></a>Per.13: 冗長な間接化を除こう

### <a name="Rper-alloc"></a>Per.14: 確保と解放の数を最小にしよう

### <a name="Rper-alloc0"></a>Per.15: クリティカルな箇所では確保しないこと

### <a name="Rper-compact"></a>Per.16: コンパクトなデータ構造を使おう

### <a name="Rper-struct"></a>Per.17: 時間にクリティカルな構造体では最も使われるメンバを先頭に宣言しよう

### <a name="Rper-space"></a>Per.18: 領域は時間です

##### 理由

性能は、典型的には、メモリアクセス時間が支配的だから。

### <a name="Rper-access"></a>Per.19: 予測可能なようにメモリアクセスをしよう

##### Reason

性能はキャッシュ性能にとても敏感で、キャッシュアルゴリズムは連続したデータへの単純（通常は線形）なアクセスを好みます。

##### Example

    int matrix[rows][cols];

    // bad
    for (int c = 0; c < cols; ++c)
        for (int r = 0; r < rows; ++r)
            sum += matrix[r][c];

    // good
    for (int r = 0; r < rows; ++r)
        for (int c = 0; c < cols; ++c)
            sum += matrix[r][c];

### <a name="Rper-context"></a>Per.30: クリティカルなパスではコンテキストスイッチを避けよう

### <a name="Rconc-multi"></a>CP.1: コードがマルチスレッドプログラムの一部として実行するかもしれないことを前提としよう

### <a name="Rconc-races"></a>CP.2: データ競合を避けよう

### <a name="Rconc-data"></a>CP.3: 書き込み可能なデータの明示的な共用は最小にしよう

### <a name="Rconc-task"></a>CP.4: スレッドでなく、タスクの言葉で考えよう

### <a name="Rconc-volatile"></a>CP.8: 同期のために `volatile` を使わないこと

### <a name="Rconc-tools"></a>CP.9: 可能な時は必ず、ツールを使ってあなたの並列コードを検証しよう

##### 注意

スレッド安全性は難しいです。経験あるプログラマもしばしば誤ります。ツールを使うのは、これらの危険を緩和するための重要な戦略です。
「世の中には」商用とオープンソースの両方、研究用と本番用の両方、の多くのツールがあります。
不幸なことに、人々の要求と制約はあまりにも多岐にわたるため、特定の推奨をすることはできません。しかし、これくらいのコメントはできます：

* 静的強制ツール:  [clang](http://clang.llvm.org/docs/ThreadSafetyAnalysis.html)
と、 [GCC](https://gcc.gnu.org/wiki/ThreadSafetyAnnotation) のある古いバージョンは、
スレッド安全性に関する、いくらかの静的な注釈をサポートします。
その注釈は一般的にはローカル（特定のメンバ変数が特定の mutex で守られるように印をつける）で、通常は学ぶのが簡単です。
しかし、多くの静的ツールにあるように、それは、誤ったネガティブ、補足されるべきだが許されるケース、をしばしば起こします。

* 動的強制ツール: Clang の [Thread Sanitizer](http://clang.llvm.org/docs/ThreadSanitizer.html) (TSAN とも呼ばれます)
は、パワフルな動的ツールの例です。それはあなたのプログラムのビルドと実行を変えて、メモリアクセスの記録を追加します。
そして、あなたのバイナリの、ある実行時でのデータ競合を完全に見つけます。
このためのコストはメモリ（ほとんどの場合、５から１０倍）と、CPU 速度低下（２から２０倍）の両方です。
このような動的なツールは統合テスト、canary push、あるいは複数のスレッドで動くユニットテストに適用するのが最も適切です。
ワークロードが重要です：TSAN が問題を見つける時は、それはほぼ常に、実際のデータ競合です。
しかし、それは与えられた実行で起きた競合しか見つけることはできません。

### <a name="Rconc-raii"></a>CP.20: 単純な `lock()/unlock()` は決して使わず、 RAII を使おう

### <a name="Rconc-lock"></a>CP.21: 複数の `mutex` を取る時は、`std::lock()` あるいは `std::scoped_lock` を使おう

### <a name="Rconc-unknown"></a>CP.22: ロックを持っている時は、未知のコード（例えば、コールバック）を決して呼ばないこと

### <a name="Rconc-join"></a>CP.23: join するスレッドは、スコープ内のコンテナとみなそう

### <a name="Rconc-detach"></a>CP.24: スレッドは、グローバルなコンテナとみなそう

### <a name="Rconc-joining_thread"></a>CP.25: `std::thread` より、`gsl::joining_thread` を選ぼう

### <a name="Rconc-detached_thread"></a>CP.26: スレッドを `detach()` しないこと

### <a name="Rconc-data-by-value"></a>CP.31: スレッドに渡す少量のデータは、参照あるいはポインタでなく、値で渡そう

### <a name="Rconc-shared"></a>CP.32: 無関係なスレッド間で所有権を共有するには、 `shared_ptr` を使おう

### <a name="Rconc-switch"></a>CP.40: コンテキストスイッチを最小にしよう

### <a name="Rconc-create"></a>CP.41: スレッド作成と破壊を最小にしよう

### <a name="Rconc-wait"></a>CP.42: 条件無しで `wait` しないこと

### <a name="Rconc-time"></a>CP.43: クリティカルセクション内で使う時間は最小にしよう

### <a name="Rconc-name"></a>CP.44: `lock_guard` と `unique_lock` には名前をつけるのを忘れないこと

### <a name="Rconc-mutex"></a>CP.50: `mutex` はそれが守るデータと一緒に定義しよう。可能なら、 `synchronized_value<T>` を使おう

### <a name="Rconc-future"></a>CP.60: 並列タスクから値を返すには、 `future` を使おう

### <a name="Rconc-async"></a>CP.61: 並列タスクを起動するには、 `async()` を使おう

### <a name="Rconc-lockfree"></a>CP.100: 絶対に必要でない限り、ロックフリープログラミングを使わないこと

### <a name="Rconc-distrust"></a>CP.101: あなたのハードウェアとコンパイラの組み合わせを疑おう

### <a name="Rconc-literature"></a>CP.102: 注意深く論文を勉強しよう

##### 参考文献

* Anthony Williams: C++ concurrency in action. Manning Publications.
* Boehm, Adve, You Don't Know Jack About Shared Variables or Memory Models , Communications of the ACM, Feb 2012.
* Boehm, "Threads Basics", HPL TR 2009-259.
* Adve, Boehm, "Memory Models: A Case for Rethinking Parallel Languages and Hardware", Communications of the ACM, August 2010.
* Boehm, Adve, "Foundations of the C++ Concurrency Memory Model", PLDI 08.
* Mark Batty, Scott Owens, Susmit Sarkar, Peter Sewell, and Tjark Weber, "Mathematizing C++ Concurrency", POPL 2011.
* Damian Dechev, Peter Pirkelbauer, and Bjarne Stroustrup: Understanding and Effectively Preventing the ABA Problem in Descriptor-based Lock-free Designs. 13th IEEE Computer Society ISORC 2010 Symposium. May 2010.
* Damian Dechev and Bjarne Stroustrup: Scalable Non-blocking Concurrent Objects for Mission Critical Code. ACM OOPSLA'09. October 2009
* Damian Dechev, Peter Pirkelbauer, Nicolas Rouquette, and Bjarne Stroustrup: Semantically Enhanced Containers for Concurrent Real-Time Systems. Proc. 16th Annual IEEE International Conference and Workshop on the Engineering of Computer Based Systems (IEEE ECBS). April 2009.

### <a name="Rconc-double"></a>CP.110: 初期化のために、ダブルチェックするロックを自分で書かないこと

### <a name="Rconc-double-pattern"></a>CP.111: 本当にダブルチェックするロックが必要な時は、慣用的なパターンを使おう

### <a name="Rconc-volatile2"></a>CP.200: `volatile` を使うのは、C++ でないメモリと話す時だけにしよう

### <a name="Rconc-signal"></a>CP.201: ??? シグナル

### <a name="Re-design"></a>E.1: 設計の初期に、エラー処理戦略を決めよう

### <a name="Re-throw"></a>E.2: 関数が与えられた仕事を実行できないことを示すためには例外を投げよう

### <a name="Re-errors"></a>E.3: 例外はエラー処理にだけ使おう

##### Reason

エラー処理を、「普通のコード」と分離するため。
C++ 実装は、例外がまれであるという前提で最適化されている傾向があります。

##### Example, don't

    // don't: exception not used for error handling
    int find_index(vector<string>& vec, const string& x)
    {
        try {
            for (gsl::index i = 0; i < vec.size(); ++i)
                if (vec[i] == x) throw i;  // found x
        } catch (int i) {
            return i;
        }
        return -1;   // not found
    }

これは、明らかな代替策と比べてより複雑で、ほぼ確実に、ずっと遅く走るでしょう。
`vector` で値を探すことに関して、例外的なことは何もありません。

### <a name="Re-design-invariants"></a>E.4: 不変条件に関して、あなたのエラー処理戦略を設計しよう

### <a name="Re-invariant"></a>E.5: コンストラクタに不変条件を確立させよう。それができない時は例外を投げさせよう

### <a name="Re-raii"></a>E.6: リークを防ぐために RAII を使おう

### <a name="Re-precondition"></a>E.7: 事前条件を述べよう

### <a name="Re-postcondition"></a>E.8: 事後条件を述べよう

### <a name="Re-noexcept"></a>E.12: 例外を投げることがありえないあるいは許容できない時は `noexcept` を使おう
訳注。原文の exiting function わからない。

### <a name="Re-never-throw"></a>E.13: オブジェクトの直接の所有者である時は決して例外を投げないこと

### <a name="Re-exception-types"></a>E.14: 例外の型は、目的のために設計されたユーザ定義型（ビルトイン型でなく）を使おう

##### Example, don't

    void my_code()     // Don't
    {
        // ...
        throw 7;       // 7 means "moon in the 4th quarter"
        // ...
    }

    void your_code()   // Don't
    {
        try {
            // ...
            my_code();
            // ...
        }
        catch(int i) {  // i == 7 means "input buffer too small"
            // ...
        }
    }

### <a name="Re-exception-ref"></a>E.15: 階層からの例外は参照で捕捉しよう

##### Example

    void f()
    {
        try {
            // ...
        }
        catch (exception e) {   // don't: may slice
            // ...
        }
    }

その代わりに、参照を使おう:

    catch (exception& e) { /* ... */ }

あるいは、典型的には `const` 参照のほうがいい:

    catch (const exception& e) { /* ... */ }

### <a name="Re-never-fail"></a>E.16: デストラクタ、解放、 `swap` は決して失敗しないこと

### <a name="Re-not-always"></a>E.17: 全ての関数で全ての例外を捕捉しようと試みないこと

##### Reason

意味のある回復アクションができない関数で例外を捕捉することは、複雑さとムダにつながります。
例外は、それを処理できる関数に届くまで、伝搬させましょう。
巻き戻るパスでの後始末アクションは、[RAII](#Re-raii) にさせましょう。

##### Example, don't

    void f()   // bad
    {
        try {
            // ...
        }
        catch (...) {
            // no action
            throw;   // propagate exception
        }
    }

### <a name="Re-catch"></a>E.18: 明示的な `try/catch` の使用は最小にしよう

### <a name="Re-finally"></a>E.19: 適切な資源ハンドルが得られない時は、 `final_action` オブジェクトを使って、後始末を表そう

### <a name="Re-no-throw-raii"></a>E.25: 例外を投げられない時は、資源管理のための RAII をシミュレートしよう

### <a name="Re-no-throw-crash"></a>E.26: 例外を投げられない時は、速やかに失敗することを考慮しよう

### <a name="Re-no-throw-codes"></a>E.27: 例外を投げられない時は、エラーコードをシステマチックに使おう

### <a name="Re-no-throw"></a>E.28: グローバル状態（例えば `errno`）を基本とするエラー処理を避けよう

### <a name="Re-specifications"></a>E.30: exception specification は使わないこと

### <a name="Re_catch"></a>E.31: `catch` 節は正しい順序にしよう

##### Example

    void f()
    {
        // ...
        try {
                // ...
        }
        catch (Base& b) { /* ... */ }
        catch (Derived& d) { /* ... */ }
        catch (...) { /* ... */ }
        catch (std::exception& e){ /* ... */ }
    }

`Derived`が `Base` から派生しているなら、 `Derived` ハンドラは決して呼ばれません。
"全てをキャッチする" ハンドラは、 `std::exception` ハンドラが決して呼ばれないことを保証します。

### <a name="Rconst-immutable"></a>Con.1: デフォルトで、オブジェクトは変更不可能としよう

### <a name="Rconst-fct"></a>Con.2: デフォルトで、メンバ関数は `const` としよう

### <a name="Rconst-ref"></a>Con.3: デフォルトで、 `const` へのポインタやメンバを渡そう

### <a name="Rconst-const"></a>Con.4: 生成された後は値が変わらないオブジェクトを定義するために `const` を使おう

### <a name="Rconst-constexpr"></a>Con.5: コンパイル時に計算できる値のために `constexpr` を使おう

### <a name="Rt-raise"></a>T.1: テンプレートを使って、コードの抽象化のレベルを上げよう

### <a name="Rt-algo"></a>T.2: テンプレートを使って、多くの引数型に適用できるアルゴリズムを表そう

### <a name="Rt-cont"></a>T.3: テンプレートを使って、コンテナと範囲を表そう

### <a name="Rt-expr"></a>T.4: テンプレートを使って、シンタックスツリー操作を表そう

### <a name="Rt-generic-oo"></a>T.5: ジェネリックとオブジェクト指向テクニックを組み合わせて、それらの長所を増加させよう。コストでなく。

### <a name="Rt-concepts"></a>T.10: テンプレート引数の全てに、コンセプトを指定しよう

### <a name="Rt-std-concepts"></a>T.11: 可能なときにはいつでも、標準のコンセプトを使おう

### <a name="Rt-auto"></a>T.12: ローカル変数には、 `auto` でなくコンセプト名を選ぼう

### <a name="Rt-shorthand"></a>T.13: 単純で一つの型の引数のコンセプトには、短縮形ノーテーションを選ぼう

### <a name="Rt-low"></a>T.20: 意味のあるセマンティクスのない「コンセプト」を避けよう

### <a name="Rt-complete"></a>T.21: コンセプトには、操作の完全なセットを要求しよう

### <a name="Rt-axiom"></a>T.22: コンセプトに公理を指定しよう

### <a name="Rt-refine"></a>T.23: 詳細化したコンセプトをそのより一般的な場合と区別するために、新しい使用パターンを加えよう

### <a name="Rt-tag"></a>T.24: セマンティクスだけが違うコンセプトを区別するために tag classe あるいは trait を使おう

### <a name="Rt-not"></a>T.25: 補完する制約条件を避けよう

### <a name="Rt-use"></a>T.26: コンセプトを定義する時は、単純なシンタックスでなく使用パターンを使うことを選択しよう

### <a name="Rt-fo"></a>T.40: アルゴリズムに操作を渡すには、関数オブジェクトを使おう

### <a name="Rt-essential"></a>T.41: テンプレートのコンセプトには、必須の属性だけを要求しよう

### <a name="Rt-alias"></a>T.42: ノーテーションを単純にして、実装の詳細を隠すために、テンプレートのエイリアスを使おう

### <a name="Rt-using"></a>T.43: エイリアスを定義する時は、`typedef` より `using` を選ぼう

### <a name="Rt-deduce"></a>T.44: クラステンプレートの引数型を推論するために、関数テンプレートを使おう（可能ならば）

### <a name="Rt-regular"></a>T.46: テンプレートの引数は少なくても、 `Regular` あるいは Semi`Regular` であることを要求しよう

### <a name="Rt-visible"></a>T.47: 一般的な名前を持った、高度に visible で制約されないテンプレートを避けよう

### <a name="Rt-concept-def"></a>T.48: あなたのコンパイラがコンセプトをサポートしない場合、 `enable_if` でそのふりをしよう

### <a name="Rt-erasure"></a>T.49: 可能なら、type-erasure を避けよう

### <a name="Rt-depend"></a>T.60: テンプレートのコンテキスト依存を最小にしよう

### <a name="Rt-scary"></a>T.61: メンバをパラメタ化しすぎないこと(ひどい)

### <a name="Rt-nondependent"></a>T.62: 依存しないクラステンプレートメンバをテンプレート化されていない基底クラスに置こう

### <a name="Rt-specialization"></a>T.64: クラステンプレートの異なる実装を提供するために特殊化を使おう

### <a name="Rt-tag-dispatch"></a>T.65: 関数の異なる実装を提供するために tag dispatch を使おう

### <a name="Rt-specialization2"></a>T.67: 不規則な型に対する異なる実装を提供するために特殊化を使おう

### <a name="Rt-cast"></a>T.68: テンプレート内では、 `()` でなく `{}` を使って、あいまいさを避けよう

### <a name="Rt-customization"></a>T.69: テンプレート内では、それを customization point とする意図がない限り、修飾されない非メンバ関数呼び出しをしないこと

### <a name="Rt-hier"></a>T.80: クラス階層をナイーブにテンプレートとしないこと

### <a name="Rt-array"></a>T.81: 階層と配列を混ぜないこと

### <a name="Rt-linear"></a>T.82: 仮想関数が不適切な場合、階層を linearize しよう

### <a name="Rt-virtual"></a>T.83: メンバ関数テンプレートを virtual と宣言しないこと

### <a name="Rt-abi"></a>T.84: ABI が安定したインタフェースを提供するために、テンプレート化されないコア実装を使おう

### <a name="Rt-variadic"></a>T.100: いろいろな型の可変個の引数を取る関数が必要な時は、可変引数テンプレートを使おう

### <a name="Rt-variadic-pass"></a>T.101: ??? 可変引数テンプレートにどのように引数を渡すか ???

### <a name="Rt-variadic-process"></a>T.102: 可変引数テンプレートへの引数をどのように処理するか

### <a name="Rt-variadic-not"></a>T.103: 均質な引数リストには、可変引数テンプレートを使わないこと

### <a name="Rt-metameta"></a>T.120: 本当に必要な時に限り、テンプレートメタプログラミングを使おう

### <a name="Rt-emulate"></a>T.121: テンプレートメタプログラミングは主に、コンセプトをエミュレートするために使おう

### <a name="Rt-tmp"></a>T.122: コンパイル時に型を計算するためにテンプレート（通常はテンプレートエイリアス）を使おう

### <a name="Rt-fct"></a>T.123: コンパイル時に値を計算するために `constexpr` 関数を使おう

### <a name="Rt-std-tmp"></a>T.124: 標準ライブラリの TMP 機構を選ぼう

### <a name="Rt-lib"></a>T.125: 標準ライブラリの TMP 機構の先に行く必要があるならば、既存のライブラリを使おう

### <a name="Rt-name"></a>T.140: 再使用される可能性のある全ての操作には名前をつけよう

### <a name="Rt-lambda"></a>T.141: 一箇所でだけ、単純な関数オブジェクトが必要な時は、無名ラムダを使おう

### <a name="Rt-var"></a>T.142?: ノーテーションを単純にするためにテンプレート変数を使おう

### <a name="Rt-nongeneric"></a>T.143: 意図しないで、汎用的でないコードを書かないこと

### <a name="Rt-specialize-function"></a>T.144: 関数テンプレートを特殊化しないこと

### <a name="Rt-check-class"></a>T.150: `static_assert` を使って、クラスがコンセプトにあっているか確認しよう

### <a name="Rcpl-C"></a>CPL.1: C より C++ を選ぼう

### <a name="Rcpl-subset"></a>CPL.2: C を使わなくてはいけない時は、 C と C++ の共通サブセットを使い、 C コードを C++ としてコンパイルしよう

### <a name="Rcpl-interface"></a>CPL.3: インタフェースに C を使わなくてはいけない時は、それを呼び出すコードで C++ を使おう

### <a name="Rs-file-suffix"></a>SF.1: あなたのプロジェクトが既に他の慣例に従っていないなら、コードファイルには `.cpp` サフィックスを、インタフェースファイルに `.h` を使おう

### <a name="Rs-inline"></a>SF.2: `.h` ファイルはオブジェクトの定義やインラインでない関数定義を含まないこと

### <a name="Rs-declaration-header"></a>SF.3: 複数のソースファイルで使われる全ての宣言のために `.h` ファイルを使おう

### <a name="Rs-include-order"></a>SF.4: ファイル内で他の宣言の前に `.h` ファイルをインクルードしよう

### <a name="Rs-consistency"></a>SF.5: `.cpp` ファイルは、そのインタフェースを定義する `.h` ファイルをインクルードしなくてはいけません

### <a name="Rs-using"></a>SF.6: `using namespace` 指令は、移行のため、基本的なライブラリ (`std` のような)のため、あるいは、ローカルスコープ内（その時に限り）で使おう

### <a name="Rs-using-directive"></a>SF.7: ヘッダファイル内のグローバルスコープで、 `using namespace` を書かないこと

##### 理由

そうすると、`#include` する人は、効果的にあいまいさを解決し代わりのものを使うことができなくなります。またそうすると、`#include` されるヘッダが順序に依存するようになります。なぜならば、それらは異なる順序でインクルードされた時、異なる意味をもつことがあるからです。
##### 例

    // bad.h
    #include <iostream>
    using namespace std; // bad

    // user.cpp
    #include "bad.h"

    bool copy(/*... some parameters ...*/);    // some function that happens to be named copy

    int main() {
        copy(/*...*/);    // now overloads local ::copy and std::copy, could be ambiguous
    }

### <a name="Rs-guards"></a>SF.8: 全ての  `.h` ファイルで、`#include` ガードを使おう

### <a name="Rs-cycles"></a>SF.9: ソースファイル間の循環依存を避けよう

### <a name="Rs-implicit"></a>SF.10: 暗黙的に `#include` された名前への依存を避けよう

### <a name="Rs-contained"></a>SF.11: ヘッダフィルは自己完結しているべきです

### <a name="Rs-namespace"></a>SF.20: 論理的構造を表すために名前空間を使おう

### <a name="Rs-unnamed"></a>SF.21: ヘッダでは名前無し (anonymous) 名前空間を使わないこと

### <a name="Rs-unnamed2"></a>SF.22: 全ての内部的／エクスポートされない要素のために、名前無し (anonymous) 名前空間を使おう

### <a name="Rsl-lib"></a>SL.1:  可能な時はいつでも、ライブラリを使おう

### <a name="Rsl-sl"></a>SL.2: 他のライブラリよりは、標準ライブラリを選ぼう

### <a name="sl-std"></a>SL.3: 標準でない要素を、 `std` 名前空間に入れないこと

### <a name="sl-safe"></a>SL.4: 標準ライブラリは、型安全なように使おう

### <a name="Rsl-arrays"></a>SL.con.1: C 配列より、 STL `array` あるいは `vector` を使おう

### <a name="Rsl-vector"></a>SL.con.2: 他のコンテナを使う理由が無い限り、デフォルトで STL `vector` を使おう

### <a name="Rsl-bounds"></a>SL.con.3: 境界エラーを避けよう

### <a name="Rstr-string"></a>SL.str.1: 文字シーケンスを所有するには、`std::string` を使おう

### <a name="Rstr-view"></a>SL.str.2: 文字シーケンスを参照するには、`std::string_view` あるいは `gsl::string_span` を使おう

### <a name="Rstr-zstring"></a>SL.str.3: C スタイルのゼロ終了する文字シーケンスを参照するには、 `zstring` あるいは c`zstring` を使おう

### <a name="Rstr-char*"></a>SL.str.4: 単一の文字を参照するには、 `char*` を使おう

### <a name="Rstr-byte"></a>SL.str.5: 必ずしも文字を表さないバイト値を参照するには、`std::byte` を使おう

### <a name="Rstr-locale"></a>SL.str.10: ロケールに敏感な文字列操作をする必要がある時は `std::string` を使おう

### <a name="Rstr-span"></a>SL.str.11: 文字列を変更する必要がある時は、`std::string_view` でなく、`gsl::string_span` を使おう

### <a name="Rstr-s"></a>SL.str.12: 標準ライブラリの文字列を意味する文字列リテラルには `s` サフィックスを使おう

### <a name="Rio-low"></a>SL.io.1: 文字レベルの入力は、必要がある時だけ、使おう

### <a name="Rio-validate"></a>SL.io.2: 読む時は、常に誤った形式の入力を考慮しよう

### <a name="Rio-streams"></a>SL.io.3: I/O には、 `iostream` を選ぼう

### <a name="Rio-sync"></a>SL.io.10: `printf`-ファミリー関数を使わないなら、`ios_base::sync_with_stdio(false)` を呼ぼう

### <a name="Rio-endl"></a>SL.io.50: `endl` は使わないこと

##### 理由

`endl` 操作子は、ほぼ、`'\n'` と `"\n"` に同じです。
それはとても一般的に使われるため、冗長な `flush()` をすることで出力をおおいに遅くします。
この性能低下は、`printf` スタイルの出力と比べてとても大きいことがあります。

##### 例

    cout << "Hello, World!" << endl;    // two output operations and a flush
    cout << "Hello, World!\n";          // one output operation and no flush

### <a name="Rclib-jmp"></a>SL.C.1: setjmp/longjmp は使わないこと

### <a name="Ra-stable"></a>A.1: コードの安定した部分をあまりそうでない部分と分離しよう

### <a name="Ra-lib"></a>A.2: 潜在的に再利用可能な部分はライブラリとして表そう

### <a name="Ra-dag"></a>A.4: ライブラリ間に循環は無いべきです

### <a name="Rnr-top"></a>NR.1: ダメ：全ての宣言は関数の先頭にあるべきです

### <a name="Rnr-single-return"></a>NR.2: ダメ：関数には一つだけの `return` 文があるべきです

### <a name="Rnr-no-exceptions"></a>NR.3: ダメ：例外を使わないこと

##### （この規則に従わない）理由

この禁止則には３つの主な理由があるようです。

* 例外は非効率的です
* 例外はリークと誤りにつながります
* 例外の性能は予測不可能です

全ての人を満足させるようにこの問題の結論を出す方法はありません。
略

### <a name="Rnr-lots-of-files"></a>NR.4: ダメ：クラスの宣言はそれぞれ独自のソースファイルに置こう

### <a name="Rnr-two-phase-init"></a>NR.5: ダメ：コンストラクタでたくさんの作業をしないこと；その代わり、２相の初期化を使おう

### <a name="Rnr-goto-exit"></a>NR.6: ダメ：関数の終わりに全ての後始末アクションを置いて、goto で抜けよう

### <a name="Rnr-protected-data"></a>NR.7: ダメ： 全てのデータメンバを `protected` にしよう

### <a name="Rl-comments"></a>NL.1: コードで明確に書けることをコメントで言わないこと

### <a name="Rl-comments-intent"></a>NL.2: コメントでは意図を書こう

### <a name="Rl-comments-crisp"></a>NL.3: コメントは簡潔にしよう

### <a name="Rl-indent"></a>NL.4: 一貫したインデントスタイルを保とう

### <a name="Rl-name-type"></a>NL.5: 名前に型情報をエンコードしないこと

### <a name="Rl-name-length"></a>NL.7: 名前の長さは、ほぼ、そのスコープの長さと比例させよう

### <a name="Rl-name"></a>NL.8: 一貫した名前付けスタイルを使おう

### <a name="Rl-all-caps"></a>NL.9: `ALL_CAPS`、全部大文字、はマクロ名にだけ使おう

### <a name="Rl-camel"></a>NL.10: `underscore_style` の名前を選ぼう

### <a name="Rl-space"></a>NL.15: 空白はほどほどに使おう

### <a name="Rl-literals"></a>NL.11: リテラルは読みやすくしよう

### <a name="Rl-order"></a>NL.16: 慣用的なクラスメンバ宣言順を使おう

##### 理由

慣用的なメンバの順序は、読みやすさを増します。
クラスを宣言する時は、以下の順序を使おう。

* 型: クラス, enum, そしてエイリアス (`using`)
* コンストラクタ, 代入, デストラクタ
* 関数
* データ

`public` その次に `protected` その次に `private` の順を使おう。

##### 例

    class X {
    public:
        // interface
    protected:
        // unchecked function for use by derived class implementations
    private:
        // implementation details
    };

### <a name="Rl-knr"></a>NL.17: K&R に由来するレイアウトを使おう

### <a name="Rl-ptr"></a>NL.18: C++ スタイルの宣言レイアウトを使おう

### <a name="Rl-misread"></a>NL.19: 読み間違いをしやすい名前を避けよう

##### Example

    int oO01lL = 6; // bad

    int splunk = 7;
    int splonk = 8; // bad: splunk and splonk are easily confused

### <a name="Rl-stmt"></a>NL.20: 同じ行に２つの文を置かないこと

### <a name="Rl-dcl"></a>NL.21: 一つの宣言には、一つの名前（だけ）を宣言しよう

### <a name="Rl-void"></a>NL.25: `void` は引数型に使わないこと

##### Example

    void f(void);   // bad

    void g();       // better

### <a name="Rl-const"></a>NL.26: 慣用的な `const` ノーテーションを使おう

##### Example

    const int x = 7;    // OK
    int const y = 9;    // bad

    const int *const p = nullptr;   // OK, constant pointer to constant int
    int const *const p = nullptr;   // bad, constant pointer to constant int

終わり
