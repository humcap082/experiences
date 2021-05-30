# Effective Dart

## Style

コードのレイアウトと整理のルール。

<details><summary>Identifiers</summary>

### Identifiers

dartには三つのフレーバーがあり、その使い分けについてです。

|flavor|説明|
|:---|:---|
|UpperCamelCase|単語の頭文字が大文字|
|lowerCamelCase|最初の単語は小文字で、後に続く単語の頭文字は大文字|
|lowercase_with_underscores|単語は小文字で単語をアンダースコアで区切ります。|

<details><summary>DO name types using UpperCase</summary>

#### DO name types using UpperCase

クラスや列挙型、型定義や型はUpperCamelCaseを使用します。

##### 例

<details><summary>good</summary>

###### good

```dart
class SliderMenu {}

class HttpRequest {}

typedef Predicate<T> = bool Function(T value)
```

</details>

</details>

<details><summary>DO name extensions using UpperCamelCase</summary>

#### DO name extensions using UpperCamelCase

型と同様に拡張ももUpperCamelCaseを使用します。

##### 例

<details><summary>good</summary>

```dart
extension MyFancyList<T> on List<T> {}

extension SmartIterable<T> on Iterable<T> {}
```

</details>

</details>

<details><summary>DO name libraries, packages, directories, and source files using lowercase_with_underscores</summary>

#### DO name libraries, packages, directories, and source files using lowercase_with_underscores

一部ファイルシステムでは大文字と小文字が区別されないため、多くのプロジェクトでは

ファイル名をlowercase_with_underscoresを使用します。

##### 例

<details><summary>good</summary>

###### good

```dart
library peg_parser.source_scanner

import 'file_system.dart';
import 'slider_menu.dart';

```

</details>

</details>

<details><summary>DO name import prefixes using lowercase_with_underscores</summary>

#### DO name import prefixes using lowercase_with_underscores

インポートはlowercase_with_underscoresを使用します。

##### 例

<details><summary>good</summary>

```dart
import 'dart:math' as math;
import 'package:angular_components/angular_components' as angular_components;
import 'package:js/js.dart' as js;
```

</details>

</details>

<details><summary>DO name other identifers using lowerCamelCase</summary>

#### DO name other identifers using lowerCamelCase

クラスメンバ、最上位の定義、変数、パラメータ、および名前付きパラメータは、

lowerCamelCaseを使用します。

##### 例

<details><summary>good</summary>

```dart
var count = 3;
HttpRequest httpRequest;
void align(bool clearItems);
```

</details>

</details>

<details><summary>PREFER using lowerCamelCase for constant names</summary>

#### PREFER using lowerCamelCase for constant names

新しいコードでは列挙値を含む定数変数にlowerCamelCaseを使用します。

##### 例

<details><summary>good</summary>

```dart
const pi = 3.14;
const defaultTimeout = 1000;
final urlScheme = RegExp('^([a-z]+):');

class Dice {
    static final numberGenerator = Random();
}
```

</details>

</details>

<details><summary>DO capitalize acronyms and abbreviations longer than two letters like words</summary>

#### DO capitalize acronyms and abbreviations longer than two letters like words

UpperCamelCaseを用いる場合、2文字より多い略語は頭文字だけを大文字にしますが、

2文字の場合は、完全に大文字にします。例外として`ID`は`Id`になり、

もともと`Mr`のように大文字と小文字で略されているものは

そのまま使用できます。

##### 例

<details><summary>good</summary>

```dart
class HttpConnection {}

class DBIOPort {}

class TVVcr {}

class MrRogers {}

var httpRequest;
var uiHandler;
Id id;
```

</details>

</details>

<details><summary>PREFER using \_, \_\_, etc. for unused callback parameters.</summary>

#### PREFER using \_, \_\_, etc. for unused callback parameters.

引数を求められる関数定義がありますが、もしその引数が関数内で

使用されないとき、その引数をアンダースコアに置き換えることが

好まれます。そのような引数が複数ある場合は、複数のアンダースコアを

つなげます。

##### 例

<details><summary>good</summary>

###### good

```dart
futureOfVoid.then((_) {
    print('Operation complete);
})
```

</details>

</details>

<details><summary>DON'T use a leading underscore for identifiers that aren't private</summary>

#### DON'T use a leading underscore for identifiers that aren't private

アンダースコアをトップレベルの宣言や、メンバーにつけることで、それらを

プライベートとして判断します。なので、プライベートではないメンバには

アンダースコアをつけるべきではありません。そして、

ローカル変数、ローカルパラメータ、ローカル関数、ライブラリは

プライベートの必要がないので、アンダースコアをつけることはありません。

</details>

<details><summary>DON'T use prefix letters</summary>

#### DON'T use prefix letters

ハンガリアン記法やその他のスキームはコンパイラがコードを理解するのに

あまり役に立たなかった`BCPL`の時代に生まれました。

しかし、`Dart`では必要ありません。

##### 例

<details><summary>good/bad</summary>

```dart
defaultTimeout  // good
kDefaultTimeout // bad
```

</details>

</details>

</details>

<details><summary>Ordering</summary>

### Ordering

ファイルのプリアンブルを整理するために、ディレクティブが表示される順序を

規定しています。

<details><summary>DO place "dart:" imports before other imports</summary>

#### DO place "dart:" imports before other imports

##### 例

<details><summary>good</summary>

```dart
import 'dart:async';
import 'dart:html';

import 'package:bar/bar.dart';
import 'package:foo/foo.dart';
```

</details>

</details>

<details><summary>DO place "package:" imports before relative imports.</summary>

#### DO place "package:" imports before relative imports.

##### 例

<details><summary>good</summary>

```dart
import 'package:bar/bar.dart';
import 'package:foo/foo.dart';

import 'util.dart';
```

</details>

</details>

<details><summary>DO specify exports in a separate section after all imports</summary>

#### DO specify exports in a separate section after all imports

##### 例

<details><summary>good</summary>

```dart
import 'src/error.dart';
import 'src/foo_bar.dart';

export 'src/error.dart';
```

</details>

</details>

<details><summary>DO sort sections alphabetically</summary>

#### DO sort sections alphabetically

##### 例

<details><summary>good</summary>

```dart
import 'package:bar/bar.dart';
import 'package:foo/foo.dart';

import 'foo.dart';
import 'foo/foo.cart';
```

</details>

</details>

</details>

<details><summary>Formatting</summary>

### Formatting

他の言語と同じように`dart`は余分なスペースを無視します。

そのスペースを利用し、`dart`の適切にフォーマットします。

<details><summary>DO format your code using dart format</summary>

フォーマットは面倒な作業であり、リファクリング中に時間がかかります。

しかし、心配する必要はありません。`dart format`は自動フォーマットします。

残りのガイドラインは`dart format`では、補完できない部分です。

</details>

<details><summary>CONSIDER changing your code to make it more formatter-friendly</summary>

#### CONSIDER changing your code to make it more formatter-friendly

特に長い識別子、深くネストされた式、さまざまな演算子が混在している場合など、

フォーマットされた出力が読みにくい場合があります。その場合は、手動で

読みやすい形にしてください。

</details>

<details><summary>AVOID lines longer than 80 characters</summary>

#### AVOID lines longer than 80 characters

次の行に移動する時に、目の移動が遠くなるため、長いテキストは

読みにくくなります。80文字を超える行が本当に必要な場合は、

命名を短くすることを検討してください。

例外として、コメントやURIで80文字をこえても良いです。

また、複数行の文字列には80文字を超えても良いです。

</details>

<details><summary>DO use curly braces for all flow control statements</summary>

#### DO use curly braces for all flow control statements

すべての制御フローには中括弧を使用してください。

一行に収まる文は例外として許されます。

##### 例

<details><summary>good</summary>

###### good

```dart
if (isWeekDay) {
    print('Bic to work');
} else {
    print('Go dancing or read book!');
}
```

</details>

<details><summary>exception</summary>

###### exception

```dart
if (art == null) return defaultValue;
```

</details>

</details>

</details>

## Documentation

コメントのルール。

<details><summary>Comments</summary>

### Comments

通常のコメントのルール

<details><summary>DO format comments like sentences</summary>

#### DO format comments like sentences

最初は大文字で、最後はピリオドで終わります。

##### 例

<details><summary>good</summary>

```dart
// Not if there is nothing before it.
```

</details>

</details>

<details><summary>DON'T use block comments for documentation</summary>

#### DON'T use block comments for documentation

`/* ... */`はコードを一時的に避難させるためのものであり、

通常、コメントは`//`を使用します。

##### 例

<details><summary>bad</summary>

###### bad

```dart
greet(name) {
    /* Assume we have a valid name. */
    print('Hi, $name!');
}
```

</details>

</details>

</details>

<details><summary>Doc comments</summary>

### Doc comments

ドキュメントのコメントのルール

<details><summary>DO use /// doc comments to document members and types</summary>

#### DO use /// doc comments to document members and types

ドキュメント用のコメントは`///`を使用します。これにより`dartdoc`は

それを見つけてドキュメント生成します。

<details><summary>good</summary>

```dart
/// The number of characters in this chunk when unsplit.
int get length => ...
```

</details>

</details>

<details><summary>PREFER writing doc comments for public APIs</summary>

#### PREFER writing doc comments for public APIs

全てのライブラリは、できる限り、変数やメンバ、定義にドキュメントをつけるべきです。

</details>

<details><summary>CONSIDER writing a library-level doc comment</summary>

#### CONSIDER writing a library-level doc comment

ライブラリレベルにドキュメントを生成する必要があります。

ドキュメントには以下を含めてください。

- ライブラリの目的に関する1文のようやく
- ライブラリ全体で使用される用語の説明
- APIを使用してウォークスルーするいくつかの完全なコードサンプル
- 最も重要、一般的に使用されるクラス、及び関数へのリンク。
- ライブラリが関係するドメイン上の外部参照リンク。

ドキュメントは`library`ディレクティブのすぐうえに記述します。

</details>

<details><summary>CONSIDER writing doc comments for private APIs</summary>

##### CONSIDER writing doc comments for private APIs

パブリックなAPIにだけではなく、プラベートなAPIにもドキュメントを

つけたほうがいいでしょう。

</details>

<details><summary>DO start doc comments with a single-sentence summary</summary>

#### DO start doc comments with a single-sentence summary

コメントはユーザー中心に考えた要約からはじめるべきです。

##### 例

<details><summary>good</summary>

```dart
/// Deletes the file at [path] from the file system.
void delete(String path) {
    ...
}
```

</details>

</details>

<details><summary>DO separate the first sentence of a doc comment into its own paragraph</summary>

#### DO separate the first sentence of a doc comment into its own paragraph

空白行のコメントをあけることで、段落を区切ることができます。`dartdoc`は最初の空白行のコメント

で要約と説明文を識別します。

##### 例

<details><summary>good</summary>

```dart
/// Deletes the file at [path].
///
/// Throws an [IOError] if the file could not be found. Throws a
/// [PermissionError] if the file is present but could not be deleted.
void delete(String path) {
    ...
}
```

</details>

</details>

<details><summary>AVOID redundancy with the surrounding context<summary>

### AVOID redundancy with the surrounding context

周囲の情報と重複を避けるべきです。ソースコードを見て、すぐに理解できる部分は

コメントに書き込む必要はありません。

</details>

<details><summary>PREFER starting variable, getter, or setter comments with noun phrases<summary>

### PREFER starting variable, getter, or setter comments with noun phrases

プロパティやゲッターにそれを説明するコメントはなるべくつけるべきです。

ゲッターにつけている場合は、セッターにつける必要はありません。

#### 例

<details><summary>good<summary>

##### good

```dart
/// The current day of the week, where `0` is Sunday.
int weekday;

/// The number of checked buttons on the page.
int get checkedCount => ...
```

</details>

</details>

<details><summary>PREFER stating library or type comments with noun phrases<summary>

### PREFER stating library or type comments with noun phrases

ライブラリや型のコメントは名詞ではじめてください。

</details>

<details><summary>CONSIDER including code samples in doc comments.<summary>

### CONSIDER including code samples in doc comments.

人間は例から一般化するのが得意なので、一つでもコードサンプルがあると

学習が容易になります。

#### 例

<details><summary>good<summary>

```dart
/// Returns the lesser of two numbers.
///
/// ```dart
/// min(5, 3) == 3
/// ```
num min(num a, num b) => ...
```

</details>

</details>

<details><summary>DO use square brackets in doc comments to refer to in-scope identifiers<summary>

### DO use square brackets in doc comments to refer to in-scope identifiers

変数、メソッド、型などの名前は`[]`で囲むと`dart_doc`は名前を検索し、

関連するAPIドキュメントへのリンクを作成します。カッコはオプションですが、メソッドまたは

コンストラクタを参照しているときにわかりやすくなります。

#### 例

<details><summary>good<summary>

##### good

```dart
/// Throws a [StateError] if ...
/// similar to [anotherMethod()], but ...
/// Similar to [Duration.inDays], but handles fractional days.
/// To create a point from polar coordinates, use [Point.polar()].
```

</details>

</details>

<details><summary>DO use prose to explain parameters. return values, and exceptions<summary>

### DO use prose to explain parameters. return values, and exceptions

他の言語では、詳細なタグとセクションを使用して、メソッドの引数と戻り値を

説明します。`Dart`は`[]`を使用してそれを強調します。

#### 例

<details><summary>bad<summary>

```dart
/// Defines a flag with the given name and abbreviation.
///
/// @param name The name of the flag.
/// @param abbr The abbreviation for the flag.
/// @returns The new flag.
/// @throws ArgumentError If there is already an option with
///     the given name or abbreviation.
Flag addFlag(String name, String abbr) => ...
```

</details>

<details><summary>good<summary>

```dart
/// Defines a flag.
///
/// Throws an [ArgumentError] if there is already an option named [name] or
/// there is already an option using abbreviation [abbr]. Returns the new flag.
Flag addFlag(String name, String abbr) => ...
```

</details>

</details>

<details><summary>DO put doc comments before metadata annotations<summary>

### DO put doc comments before metadata annotations

コメントはアノテーションの前に配置指定ください。

#### 例

<details><summary>good<summary>

```dart
/// A button that can be flipped on and off.
@Component(selector: 'toggle')
class ToggleComponent {}
```

</details>

</details>

</details>

<details><summary>Markdown</summary>

### Markdown

</details>

<details><summary>Writing</summary>

### Writing

</details>

## Usage

動作を実装する言語の効果的な活用方法。

<details><summary>Libraries</summary>
</details>

<details><summary>Null</summary>
</details>

<details><summary>Strings</summary>
</details>

<details><summary>Collections</summary>
</details>

<details><summary>Functions</summary>
</details>

<details><summary>Variables</summary>
</details>

<details><summary>Members</summary>
</details>

<details><summary>Constructors</summary>
</details>

<details><summary>Error handling</summary>
</details>

<details><summary>Asynchrony</summary>
</details>

## Design

汎用的な設計ガイド。

<details><summary>Names</summary>
</details>

<details><summary>Libraries</summary>
</details>

<details><summary>Classes and mixins</summary>
</details>

<details><summary>Constructors</summary>
</details>

<details><summary>Members</summary>
</details>

<details><summary>Types</summary>
</details>

<details><summary>Parameters</summary>
</details>

<details><summary>Equality</summary>
</details>

## 備考

<details><summary>ガイドのセクション</summary>

### ガイドのセクション

|Section|説明|
|:---|:---|
|DO|常に従う必要があります。|
|DON'T|やっていはいけないことです。|
|PREFER|従う必要がありますが、例外も存在します。|
|AVOID|やってはいけないことですが、例外もあります。|
|CONSIDER|好みや状況によります。|

</details>

<details><summary>用語集</summary>

### 用語集

|用語|説明|
|:---|:---|
|library member|型以外のトップレベルフィールドのすべてのもの。|
|class member|クラス内のコンストラクタ、フィールド、ゲッター、セッター、メソッドなど。|
|member|ライブラリメンバとクラスメンバのいずれか|
|variable|トップレベルの変数パラメータ、ローカル変数|
|type|クラスや型|
|property|トップレベルの変数、ゲッター、セッターなどのほぼすべてのフィードのようなもの。|

</details>
