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

</details>

<details><summary>Ordering</summary>

### Ordering

</details>

<details><summary>Formatting</summary>

### Formatting

</details>

## Document

コメントのルール。

<details><summary>Comments</summary>

### Comments

</details>

<details><summary>Doc comments</summary>

### Doc comments

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