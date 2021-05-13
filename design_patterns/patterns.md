# Creational design patterns

クラスやオブジェクトの作成パターン

<details><summary>Abstract Factory</summary>

## Abstract Factory

オブジェクトを作成する一連の抽象クラスを作成する。

```puml
@startuml
abstract AbstractFactory {
    +{abstract}getProduct1(): AbstractProduct1
    +{abstract}getProduct2(): AbstractProduct2
}

abstract AbstractProduct1 {}

abstract AbstractProduct2 {}

class ConcreteFactory {
    +getProduct1(): ConcreteProduct1
    +getProduct2(): ConcreteProduct2
}

class ConcreteProduct1 {}

class ConcreteProduct2 {}

ConcreteFactory --|> AbstractFactory
ConcreteProduct1 --|> AbstractProduct1
ConcreteProduct2 --|> AbstractProduct2
AbstractFactory --> AbstractProduct1 : create >
AbstractFactory --> AbstractProduct2 : create >
ConcreteFactory --> ConcreteProduct1 : create >
ConcreteFactory --> ConcreteProduct2 : create >
@enduml
```

</details>

<details><summary>Builder</summary>

## Builder

表現形式のインタフェースとそれを使用した

作成過程を管理するクラスを用意するパターン。

```puml
@startuml
class Director {
    -builder: Builder
    +build()
}

interface Builder {
    +{abstract}buildPart()
    +{abstract}getResult()
}

class ConcreteBuilder {
    +buildPart()
    +getResult()
}

Director o-- Builder
ConcreteBuilder ..|> Builder

@enduml
```

</details>

<details><summary>Factory Method</summary>

## Factory Method

スーパークラスにインスタンスを生成するメソッドと

そのインスタンスのインタフェースを用意することで、

インスタンスの生成をオーバーライドできるパターン

```puml
@startuml
abstract Factory {
    +{abstract}factoryMethod(): Product
}

interface Product {
}

class ConcreteFactory {
    +factoryMethod(): Product
}

class ConcreteProduct {
}

ConcreteFactory --|> Factory
ConcreteProduct ..|> Product
Factory --> Product : create >
ConcreteFactory --> ConcreteProduct : create >
note left of ConcreteFactory : factoryMethod() returns ConcreteProduct()
@enduml
```

</details>

<details><summary>Object Pool</summary>

## Object

</details>

<details><summary>Prototype</summary>

## Prototype

自身のインスタンスをコピーして新しいインスタンスを作成する

メソッドもったインタフェースを用意するパターン

```uml
@startuml
interface ProtoType {
    +{abstract}createClone(): ProtoType
}

class ConcreteProtoType {
    +createClone(): ProtoType
}

ConcreteProtoType ..|> ProtoType
User --> ProtoType : uses >
@enduml
```

</details>

<details><summary>Singleton</summary>

## Singleton

一度、インスタンスを生成したクラスが

その後、同じインスタンスしか返さないことで

インスタンスが常に一つであることを保障するパターン。

```puml
@startuml
class Singleton {
    -instance: Singleton
    -Singleton()
    +getInstance(): Singleton
}
@enduml
```

</details>

# Structural design patterns

クラスやオブジェクトの構成パターン

<details><summary>Adapter</summary>

## Adapter

クラスのインターフェースをクライアントが期待する別のインターフェースに

変換することで、互換性がない他のクラスを連携する。

```puml
@startuml
class Adapter {
    +targetMethod()
}

interface Target {
    +{abstract}targetMethod()
}

class Adaptee {
    +method()
}

Adapter ..|> Target
Adapter --|> Adaptee
Client --> Target: Use >
note left of Adapter: method() in targetMethod()
@enduml
```

もしくは

```puml
@startuml
class Adapter {
    -adaptee: Adaptee
    +targetMethod()
}

interface Target {
    +{abstract}targetMethod()
}

class Adaptee {
    +method()
}

Adapter --|> Target
Adapter::adaptee o-- Adaptee
Client --> Target: Use >
note left of Adapter : "adaptee.method() in taregetMethod()"
@enduml
```

</details>

<details><summary>Bridge</summary>

## Bridge

実装と機能を独立させるパターンで、

機能クラスのフィールドに実装クラスを集約することで、

機能クラスのサブクラスが実装クラスのサブクラスを

選択できるパターン。

```puml
@startuml
class Abstraction {
    -implementer: Implementer
    +operation()
}

abstract Implementer {
    +{abstract}operationImple()
}

class RefineAbstraction {
    +operation()
}

class ConcreteImplementorA {
    +operationImple()
}

class ConcreteImplementorB {
    +operationImple()
}

RefineAbstraction --|> Abstraction
ConcreteImplementorA --|> Implementer
ConcreteImplementorB --|> Implementer
Abstraction::implementer o-- Implementer
note left of Abstraction : implementor.operationImple() in operation()
@enduml
```

</details>

<details><summary>Composite</summary>

## Composite

</details>

<details><summary>Decorator</summary>

## Decorator

</details>

<details><summary>Facade</summary>

## Facade

</details>

<details><summary>Flyweight</summary>

## Flyweight

</details>

<details><summary>Private Class Data</summary>

## Private Class Data

</details>

<details><summary>Proxy</summary>

## Proxy

</details>

# Behavioral design patterns

クラスやオブジェクト間のコミュニーケーションパターン

<details><summary>Chain of responsibility</summary>

## Chain of responsibility

</details>

<details><summary>Command</summary>

## Command

</details>

<details><summary>Interpreter</summary>

## Interpreter

</details>

<details><summary>Iterator</summary>

## Iterator

集約クラスに順番にアクセスする方法を提供する。

```puml
@startuml
interface Iterable {
    +{abstract}iterator(): Iterator;
}

interface Iterator {
    +{abstract}hasNext();
    +{abstract}next();
}

class ConcreteIterable {
    +Iterator iterator();
}

class ConcreteIterator {
    -concreteIterable: ConcreteIterable
    +hasNext();
    +next();
}

ConcreteIterable ..|> Iterable
ConcreteIterator ..|> Iterator
ConcreteIterator --o ConcreteIterable
@enduml
```

### 例

<details><summary>iterator in java</summary>

```java
class IntegerBox {
    private List<Integer> list = new ArrayList<>();

    public class Iterator {
        private IntegerBox box;
        private java.util.Iterator iterator;
        private int value;

        public Iterator(IntegerBox integerBox) {
            box = integerBox;
        }

        public void first() {
            iterator = box.list.iterator();
            next();
        }

        public void next() {
            try {
                value = (Integer)iterator.next();
            } catch (NoSuchElementException ex) {
                value =  -1;
            }
        }

        public boolean isDone() {
            return value == -1;
        }

        public int currentValue() {
            return value;
        }
    }

    public void add(int in) {
        list.add(in);
    }

    public Iterator getIterator() {
        return new Iterator(this);
    }
}

public class IteratorDemo {
    public static void main(String[] args) {
        IntegerBox integerBox = new IntegerBox();
        for (int i = 9; i > 0; --i) {
            integerBox.add(i);
        }
        // getData() has been removed.
        // Client has to use Iterator.
        IntegerBox.Iterator firstItr = integerBox.getIterator();
        IntegerBox.Iterator secondItr = integerBox.getIterator();
        for (firstItr.first(); !firstItr.isDone(); firstItr.next()) {
            System.out.print(firstItr.currentValue() + "  ");
        }
        System.out.println();
        // Two simultaneous iterations
        for (firstItr.first(), secondItr.first(); !firstItr.isDone(); firstItr.next(), secondItr.next()) {
            System.out.print(firstItr.currentValue() + " " + secondItr.currentValue() + "  ");
        }
    }
}
```

</details>

</details>

<details><summary>Mediator</summary>

## Mediator

</details>

<details><summary>Memento</summary>

## Memento

</details>

<details><summary>Null Object</summary>

## Null Object

</details>

<details><summary>Observer</summary>

## Observer

</details>

<details><summary>State</summary>

## State

</details>

<details><summary>Strategy</summary>

## Strategy

</details>

<details><summary>Template method</summary>

## Template method

メソッドを組み合わせて使用するメソッドを

抽象クラスのみに定義し、サブクラスは部分的な

メソッドのみをオーバーライドするようなパターン

```uml
@startuml
abstract AbstractClass {
    +{abstract}method1()
    +{abstract}method2()
    +templateMethod()
}
class ConcreteClass {
    +method1()
    +method2()
}

ConcreteClass --|> AbstractClass
@enduml
```

</details>

<details><summary>Visitor</summary>

## visitor

</details>
