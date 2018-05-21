Here is a Japanese translation of (only) rule titles (for now) from [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) as of April 16, 2018 by kanda.motohiro@gmail.com. This translation is disributed under the [LICENSE](https://github.com/isocpp/CppCoreGuidelines/blob/master/LICENSE).
The LICENSE is very restrictive but according to this [issue discussion on translation](https://github.com/isocpp/CppCoreGuidelines/issues/1065), publishing a translation is permitted.

以下は、C++ Core Guidelines の規則のタイトルだけを訳したものです。ライセンスファイルによれば、訳をこのように公開することは不可能なのですが、引用したイシューでは、許可されているようです。

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

### <a name="Ri-abstract"></a>I.25: インタフェースには、クラス階層でなく、抽象クラスを選ぼう

### <a name="Ri-abi"></a>I.26: クロスコンパイラの ABI がほしいなら、 C-スタイルのサブセットを使おう

### <a name="Ri-pimpl"></a>I.27: 安定したライブラリの ABI のためには Pimpl イディオムを考慮しよう

### <a name="Ri-encapsulate"></a>I.30: 規則を破るところはカプセル化しよう

### <a name="Rf-package"></a>F.1: 意味のある操作を注意深く名前を付けた関数に「パッケージ」しよう

### <a name="Rf-logical"></a>F.2: 一つの関数は一つの論理的な操作をするべきです

### <a name="Rf-single"></a>F.3: 関数は短く単純に保とう

### <a name="Rf-constexpr"></a>F.4: 関数がコンパイル時に評価されなければいけないならば、`constexpr` と宣言しよう

### <a name="Rf-inline"></a>F.5: 関数がとても小さく、実行時間が重要なら、`inline` と宣言しよう

### <a name="Rf-noexcept"></a>F.6: 関数が例外を投げないなら、 `noexcept` と宣言しよう

### <a name="Rf-smart"></a>F.7: 一般的な用途には、スマートポインタでなく、 `T*` あるいは `T&` 引数を取ろう

### <a name="Rf-pure"></a>F.8: pure 関数を使おう

### <a name="Rf-unused"></a>F.9: 使わないパラメタは、無名とするべきです

### <a name="Rf-conventional"></a>F.15: 情報を伝えるには、単純で普通の方法を選ぼう

### <a name="Rf-in"></a>F.16: 「入力」パラメタでは、安価にコピーできる型は値渡しで、そうでないものは `const` への参照で渡そう

### <a name="Rf-inout"></a>F.17: 「入出力」パラメタは、`const` でない参照で渡そう

### <a name="Rf-consume"></a>F.18: 「move-from する予定」のパラメタは、 `X&&` で渡して、そのパラメタを std::move しよう

### <a name="Rf-forward"></a>F.19: 「forward」パラメタは、 `TP&&` で渡して、そのパラメタには std::forward だけをしよう

### <a name="Rf-out"></a>F.20: 「出力」の出力値は、出力パラメタより、戻り値を選ぼう

### <a name="Rf-out-multi"></a>F.21: 複数の「出力」値を戻すには、 tuple あるいは struct を選ぼう

### <a name="Rf-ptr"></a>F.22: 一つのオブジェクトを指定するには、 `T*` あるいは `owner<T*>` を選ぼう

### <a name="Rf-nullptr"></a>F.23: "null" が有効な値でないことを示すには、`not_null<T>` を使おう

### <a name="Rf-range"></a>F.24: 半開シーケンスを指定するには、`span<T>` あるいは `span_p<T>` を使おう

### <a name="Rf-zstring"></a>F.25: C-スタイル文字列を指定するには、`zstring` あるいは `not_null<zstring>` を使おう

### <a name="Rf-unique_ptr"></a>F.26: ポインタが必要である時、所有権を移動するには、`unique_ptr<T>` を使おう

### <a name="Rf-shared_ptr"></a>F.27: 所有権を共有するには、`shared_ptr<T>` を使おう

### <a name="Rf-ptr-ref"></a>F.60: 「引数なし」が有効な選択肢であるときは、`T&` でなく `T*` を使おう

### <a name="Rf-return-ptr"></a>F.42: 位置を指定するには、`T*` を返そう（その時に限り）

### <a name="Rf-dangle"></a>F.43: ローカルオブジェクトへのポインタあるいは参照は決して（直接、間接を問わす）返さないこと

### <a name="Rf-return-ref"></a>F.44: コピーが不適切で「オブジェクトを何も返さない」ことを必要としないなら、`T&` を返そう

### <a name="Rf-return-ref-ref"></a>F.45: `T&&` を返さないこと

### <a name="Rf-main"></a>F.46: `main()` の戻り値は、 `int` です

### <a name="Rf-assignment-op"></a>F.47: 代入演算子からは `T&` を返そう

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

### <a name="Rc-helper"></a>C.5: ヘルパー関数は、それがサポートするクラスと同じ名前空間に置こう

### <a name="Rc-standalone"></a>C.7: クラスあるいは列挙型の定義と、その型の変数の宣言を同じ文でするのはやめよう

### <a name="Rc-class"></a>C.8: public でないメンバが一つでもあるなら、構造体でなくクラスを使おう

### <a name="Rc-private"></a>C.9: メンバをさらすのは最小限にしよう

### <a name="Rc-concrete"></a>C.10: クラス階層よりは、具象型を選ぼう

### <a name="Rc-regular"></a>C.11: 具象型は、規則的としよう

### <a name="Rc-zero"></a>C.20: デフォルト操作を避けることができるなら、そうしよう

### <a name="Rc-five"></a>C.21: デフォルト操作のどれか一つでも、定義あるいは `=delete` するなら、全てを定義あるいは `=delete` しよう

### <a name="Rc-matched"></a>C.22: デフォルト操作に一貫性を持たせよう

### <a name="Rc-dtor"></a>C.30: クラスが、オブジェクト解体で明示的なアクションが必要なら、デストラクタを定義しよう

### <a name="Rc-dtor-release"></a>C.31: クラスが確保した全ての資源は、そのクラスのデストラクタで解放されなくてはいけません

### <a name="Rc-dtor-ptr"></a>C.32: もしクラスが、生のポインタ (`T*`) あるいは参照 (`T&`) を持つなら、それは所有を意味するのか考えよう

### <a name="Rc-dtor-ptr2"></a>C.33: もしクラスが、所有者であるポインタメンバを持つなら、デストラクタを定義しよう

### <a name="Rc-dtor-virtual"></a>C.35: 基底クラスのデストラクタは、 public かつ virtual であるか、protected かつ virtual でないかのいずれかであるべきです

### <a name="Rc-dtor-fail"></a>C.36: デストラクタは失敗しないこと

### <a name="Rc-dtor-noexcept"></a>C.37: デストラクタは `noexcept` にしよう

### <a name="Rc-ctor"></a>C.40: クラスが不変条件を持つなら、コンストラクタを定義しよう

### <a name="Rc-complete"></a>C.41: コンストラクタは、完全に初期化されたオブジェクトを作るべきです

### <a name="Rc-throw"></a>C.42: コンストラクタで有効なオブジェクトを作ることができないなら、例外を投げよう

### <a name="Rc-default0"></a>C.43: コピー可能な (値型の) クラスはデフォルトコンストラクタを持つことを保証しよう

### <a name="Rc-default00"></a>C.44: デフォルトコンストラクタは、単純で例外を投げないことしよう

### <a name="Rc-default"></a>C.45: データメンバを初期化するだけのデフォルトコンストラクタを定義しないこと；クラス内メンバ初期化子をその代わりに使おう

### <a name="Rc-explicit"></a>C.46: デフォルトで、一つの引数を取るコンストラクタは explicit と宣言しよう

### <a name="Rc-order"></a>C.47: メンバ変数は、メンバ宣言の順に、定義し初期化しよう

### <a name="Rc-in-class-initializer"></a>C.48: 定数を初期化するには、コンストラクタでのメンバ初期化子より、クラス内初期化子を選ぼう

### <a name="Rc-initialize"></a>C.49: コンストラクタでは、代入より初期化を選ぼう

### <a name="Rc-factory"></a>C.50: 初期化の間に、「virtual」なふるまいが必要なら、ファクトリ関数を使おう

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

### <a name="Rh-override"></a>C.128: 仮想関数は、`virtual`, `override`, あるいは `final` の１つだけを必ず指定するべきです

### <a name="Rh-kind"></a>C.129: クラス階層を設計する時、実装の継承とインタフェースの継承を区別しよう

### <a name="Rh-copy"></a>C.130: 基底クラスではコピーを再定義するか、禁止しよう；その代わりに仮想 `clone` 関数を選ぼう

### <a name="Rh-get"></a>C.131: 自明な getter と setter を避けよう

### <a name="Rh-virtual"></a>C.132: 関数を意味なく仮想とするのはやめよう

### <a name="Rh-protected"></a>C.133: `protected` データを避けよう

### <a name="Rh-public"></a>C.134: 全ての non-`const` データメンバが同じアクセスレベルを持つことを保証しよう

### <a name="Rh-mi-interface"></a>C.135: 複数の異なるインタフェースを表すために、多重継承を使おう

### <a name="Rh-mi-implementation"></a>C.136: 実装上の属性のユニオンを表すために、多重継承を使おう

### <a name="Rh-vbase"></a>C.137: 一般的すぎる基底クラスを避けるために、 `virtual` 基底を使おう

### <a name="Rh-using"></a>C.138: `using` で、派生クラスとその基底に対して多重定義のセットを作ろう

### <a name="Rh-final"></a>C.139: `final` はほどほどに使おう

### <a name="Rh-poly"></a>C.145: 多相的なオブジェクトは、ポインタと参照を使ってアクセスしよう

### <a name="Rh-dynamic_cast"></a>C.146: クラス階層を横断することが避けられない時は `dynamic_cast` を使おう

### <a name="Rh-ref-cast"></a>C.147: 目的のクラスが見つからない時がエラーとみなされる時は、参照型への `dynamic_cast` を使おう

### <a name="Rh-ptr-cast"></a>C.148: 目的のクラスが見つからない時が有効な選択肢とみなされる時は、ポインタ型への `dynamic_cast` を使おう

### <a name="Rh-smart"></a>C.149: `new` を使って作成したオブジェクトを `delete` するのを忘れるのを避けるために `unique_ptr` あるいは `shared_ptr` を使おう

### <a name="Rh-make_unique"></a>C.150: `unique_ptr` が所有するオブジェクトを作成するために `make_unique()` を使おう

### <a name="Rh-make_shared"></a>C.151: `shared_ptr` が所有するオブジェクトを作成するために `make_shared()` を使おう

### <a name="Rh-array"></a>C.152: 決して、派生クラスのオブジェクトの配列へのポインタを、その基底へのポインタに代入しないこと

### <a name="Rh-use-virtual"></a>C.153: キャストより仮想関数を選ぼう

### <a name="Ro-conventional"></a>C.160: 演算子は、主に、一般的な使い方をまねるために定義しよう

### <a name="Ro-symmetric"></a>C.161: 対称的な操作のため、メンバでない関数を使おう

### <a name="Ro-equivalent"></a>C.162: ほぼ等しい操作は多重定義しよう

### <a name="Ro-equivalent-2"></a>C.163: ほぼ等しい操作だけを多重定義しよう

### <a name="Ro-conversion"></a>C.164: 変換操作を避けよう

### <a name="Ro-custom"></a>C.165: カスタマイズするところで、 `using` を使おう

### <a name="Ro-address-of"></a>C.166: 単行演算子 `&` を多重定義するのは、スマートポインタと参照のシステムの一部である時にだけとしよう

### <a name="Ro-overload"></a>C.167: 慣用的な意味を持つ操作には、その演算子を使おう

### <a name="Ro-namespace"></a>C.168: 多重定義する演算子は、そのオペランドの名前空間で定義しよう

### <a name="Ro-lambda"></a>C.170: ラムダを多重定義したいときは、汎用的なラムダを使おう

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

### <a name="Rr-raii"></a>R.1: 資源ハンドルとRAII (Resource Acquisition Is Initialization、資源獲得時初期化)を使って資源を自動的に管理しよう

### <a name="Rr-use-ptr"></a>R.2: インタフェースでは、個々のオブジェクトを指定するために生のポインタを使おう（その時に限り）

### <a name="Rr-ptr"></a>R.3: 生のポインタ (`T*`) は所有を示しません

### <a name="Rr-ref"></a>R.4: 生の参照 (`T&`) は所有を示しません

### <a name="Rr-scoped"></a>R.5: スコープのあるオブジェクトを選ぼう；不必要なヒープからの確保はやめよう

### <a name="Rr-global"></a>R.6: `const` でないグローバル変数を避けよう

### <a name="Rr-mallocfree"></a>R.10: `malloc()` と `free()` を避けよう

### <a name="Rr-newdelete"></a>R.11: 明示的に `new` と `delete` を呼ぶのを避けよう

### <a name="Rr-immediate-alloc"></a>R.12: 明示的な資源確保の結果は、直ちに管理オブジェクトに渡そう

### <a name="Rr-single-alloc"></a>R.13: 一つの式の中では、最大一つの明示的な資源確保をしよう

### <a name="Rr-ap"></a>R.14: ??? 配列対ポインタ引数

### <a name="Rr-pair"></a>R.15: 対になる確保と解放は必ず両方、多重定義しよう

### <a name="Rr-owner"></a>R.20: 所有を示すため、 `unique_ptr` あるいは `shared_ptr` を使おう

### <a name="Rr-unique"></a>R.21: 所有権を共有する必要がなければ、`shared_ptr` より `unique_ptr` を使おう

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

### <a name="Rr-smartptrget"></a>R.37: エリアスしたスマートポインタから得たポインタあるいは参照を渡さないこと

### <a name="Res-lib"></a>ES.1: 他のライブラリや「手作りコード」より標準ライブラリを選ぼう

### <a name="Res-abstr"></a>ES.2: 言語機能を直接使うより、適切な抽象化を選ぼう

### <a name="Res-scope"></a>ES.5: スコープを小さく保とう

### <a name="Res-cond"></a>ES.6: for 文の初期化子と条件で名前を宣言し、スコープを制限しよう

### <a name="Res-name-length"></a>ES.7: 一般的でローカルな名前は短く、一般的でなくローカルでない名前は長くしよう

### <a name="Res-name-similar"></a>ES.8: 似て見える名前を避けよう

### <a name="Res-not-CAPS"></a>ES.9: `ALL_CAPS` 、全部大文字の名前を避けよう

### <a name="Res-name-one"></a>ES.10: 一つの宣言では一つ（だけ）名前を宣言しよう

### <a name="Res-auto"></a>ES.11: 型名の冗長な繰り返しを避けるため `auto` を使おう

### <a name="Res-reuse"></a>ES.12: ネストしたスコープ内で名前を再使用しないこと

### <a name="Res-always"></a>ES.20: オブジェクトは常に初期化しよう

### <a name="Res-introduce"></a>ES.21: 使う必要が起きる前に変数（あるいは定数）を導入しないこと

### <a name="Res-init"></a>ES.22: 変数を初期化する値を得る前に変数を宣言しないこと

### <a name="Res-list"></a>ES.23: `{}` 初期化子シンタックスを選ぼう

### <a name="Res-unique"></a>ES.24: ポインタを持つには `unique_ptr<T>` を使おう

### <a name="Res-const"></a>ES.25: 後で値を変更したいと思わないなら、オブジェクトは `const` あるいは `constexpr` と宣言しよう

### <a name="Res-recycle"></a>ES.26: ２つの無関係な目的のために一つの変数を使わないこと

### <a name="Res-stack"></a>ES.27: スタック上の配列は、`std::array` あるいは `stack_array` を使おう

### <a name="Res-lambda-init"></a>ES.28: 複雑な初期化、特に `const` 変数、のためにはラムダを使おう

### <a name="Res-macros"></a>ES.30: プログラムテキストを操作するためにマクロを使わないこと

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

### <a name="Res-do"></a>ES.75: `do` 文を避けよう

### <a name="Res-goto"></a>ES.76: `goto` を避けよう

### <a name="Res-continue"></a>ES.77: ループでの `break` と `continue` の使用は最小としよう

### <a name="Res-break"></a>ES.78: 空でない `case` は常に `break` で終わらせよう

### <a name="Res-default"></a>ES.79: 一般的な場合を扱うために（その時に限り） `default` を使おう

### <a name="Res-noname"></a>ES.84: 名前のないローカル変数を宣言し（ようと試み）ないこと

### <a name="Res-empty"></a>ES.85: 空の文は目立つようにしよう

### <a name="Res-loop-counter"></a>ES.86: 生の for ループの本体内で、ループ制御変数を変更するのは避けよう

### <a name="Res-if"></a>ES.87: 条件に冗長な `==` あるいは `!=` をつけないこと

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

### <a name="Rper-access"></a>Per.19: 予測可能なようにメモリアクセスをしよう

### <a name="Rper-context"></a>Per.30: クリティカルなパスではコンテキストスイッチを避けよう

### <a name="Rconc-multi"></a>CP.1: コードがマルチスレッドプログラムの一部として実行するかもしれないことを前提としよう

### <a name="Rconc-races"></a>CP.2: データ競合を避けよう

### <a name="Rconc-data"></a>CP.3: 書き込み可能なデータの明示的な共用は最小にしよう

### <a name="Rconc-task"></a>CP.4: スレッドでなく、タスクの言葉で考えよう

### <a name="Rconc-volatile"></a>CP.8: 同期のために `volatile` を使わないこと

### <a name="Rconc-tools"></a>CP.9: 可能な時は必ず、ツールを使ってあなたの並列コードを検証しよう

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

### <a name="Rconc-double"></a>CP.110: 初期化のために、ダブルチェックするロックを自分で書かないこと

### <a name="Rconc-double-pattern"></a>CP.111: 本当にダブルチェックするロックが必要な時は、慣用的なパターンを使おう

### <a name="Rconc-volatile2"></a>CP.200: `volatile` を使うのは、C++ でないメモリと話す時だけにしよう

### <a name="Rconc-signal"></a>CP.201: ??? シグナル

### <a name="Re-design"></a>E.1: 設計の初期に、エラー処理戦略を決めよう

### <a name="Re-throw"></a>E.2: 関数が与えられた仕事を実行できないことを示すためには例外を投げよう

### <a name="Re-errors"></a>E.3: 例外はエラー処理にだけ使おう

### <a name="Re-design-invariants"></a>E.4: 不変条件に関して、あなたのエラー処理戦略を設計しよう

### <a name="Re-invariant"></a>E.5: コンストラクタに不変条件を確立させよう。それができない時は例外を投げさせよう

### <a name="Re-raii"></a>E.6: リークを防ぐために RAII を使おう

### <a name="Re-precondition"></a>E.7: 事前条件を述べよう

### <a name="Re-postcondition"></a>E.8: 事後条件を述べよう

### <a name="Re-noexcept"></a>E.12: 例外を投げることがありえないあるいは許容できない時は `noexcept` を使おう
訳注。原文の exiting function わからない。

### <a name="Re-never-throw"></a>E.13: オブジェクトの直接の所有者である時は決して例外を投げないこと

### <a name="Re-exception-types"></a>E.14: 例外の型は、目的のために設計されたユーザ定義型（ビルトイン型でなく）を使おう

### <a name="Re-exception-ref"></a>E.15: 階層からの例外は参照で捕捉しよう

### <a name="Re-never-fail"></a>E.16: デストラクタ、解放、 `swap` は決して失敗しないこと

### <a name="Re-not-always"></a>E.17: 全ての関数で全ての例外を捕捉しようと試みないこと

### <a name="Re-catch"></a>E.18: 明示的な `try/catch` の使用は最小にしよう

### <a name="Re-finally"></a>E.19: 適切な資源ハンドルが得られない時は、 `final_action` オブジェクトを使って、後始末を表そう

### <a name="Re-no-throw-raii"></a>E.25: 例外を投げられない時は、資源管理のための RAII をシミュレートしよう

### <a name="Re-no-throw-crash"></a>E.26: 例外を投げられない時は、速やかに失敗することを考慮しよう

### <a name="Re-no-throw-codes"></a>E.27: 例外を投げられない時は、エラーコードをシステマチックに使おう

### <a name="Re-no-throw"></a>E.28: グローバル状態（例えば `errno`）を基本とするエラー処理を避けよう

### <a name="Re-specifications"></a>E.30: exception specification は使わないこと

### <a name="Re_catch"></a>E.31: `catch` 節は正しい順序にしよう

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

### <a name="Rt-alias"></a>T.42: ノーテーションを単純にして、実装の詳細を隠すために、テンプレートのエリアスを使おう

### <a name="Rt-using"></a>T.43: エリアスを定義する時は、`typedef` より `using` を選ぼう

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

### <a name="Rt-tmp"></a>T.122: コンパイル時に型を計算するためにテンプレート（通常はテンプレートエリアス）を使おう

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

### <a name="Rs-using-directive"></a>SF.7: ヘッダフィル内のグローバルスコープで、 `using namespace` を書かないこと

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

### <a name="Rclib-jmp"></a>SL.C.1: setjmp/longjmp は使わないこと

### <a name="Ra-stable"></a>A.1: コードの安定した部分をあまりそうでない部分と分離しよう

### <a name="Ra-lib"></a>A.2: 潜在的に再利用可能な部分はライブラリとして表そう

### <a name="Ra-dag"></a>A.4: ライブラリ間に循環は無いべきです

### <a name="Rnr-top"></a>NR.1: ダメ：全ての宣言は関数の先頭にあるべきです

### <a name="Rnr-single-return"></a>NR.2: ダメ：関数には一つだけの `return` 文があるべきです

### <a name="Rnr-no-exceptions"></a>NR.3: ダメ：例外を使わないこと

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

### <a name="Rl-knr"></a>NL.17: K&R に由来するレイアウトを使おう

### <a name="Rl-ptr"></a>NL.18: C++ スタイルの宣言レイアウトを使おう

### <a name="Rl-misread"></a>NL.19: 読み間違いをしやすい名前を避けよう

### <a name="Rl-stmt"></a>NL.20: 同じ行に２つの文を置かないこと

### <a name="Rl-dcl"></a>NL.21: 一つの宣言には、一つの名前（だけ）を宣言しよう

### <a name="Rl-void"></a>NL.25: `void` は引数型に使わないこと

### <a name="Rl-const"></a>NL.26: 慣用的な `const` ノーテーションを使おう

終わり
