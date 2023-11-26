# Genericidad 
##### Autor: Erik Avagyan

## Contenido
- [Que son los genericos?](#que-son-los-genericos)
- [Clase genérica](#clase-genérica)
    - [Ejemplo de clase genérica con un tipo de parámetro](#ejemplo-de-clase-genérica-con-un-tipo-de-parámetro)
    - [Ejemplo de clase genérica con múltiples tipos de parámetros](#ejemplo-de-clase-genérica-con-múltiples-tipos-de-parámetros)
- [Interfaces genéricas](#interfaces-genéricas)
- [Métodos genéricos](#métodos-genéricos)
- [Restricciones de tipo genérico](#restricciones-de-tipo-genérico)


## Que son los genericos?

Los tipos genéricos en Java son una forma de parametrizar clases, interfaces y métodos. 
Permiten que el código sea reutilizable y más flexible. El uso de genéricos permite 
escribir código que puede funcionar con diferentes tipos de objetos. 

## Clase genérica

Podemos crear una clase genérica que pueda trabajar con diferentes tipos de objetos. 
Veamos diferentes ejemplos para entender mejor cómo funcionan los genéricos.

### Ejemplo de clase genérica con un tipo de parámetro

```java
public class Box<T> {
    private T content;

    public Box(T t) {
        this.content = t;
    }

    public T getContent() {
        return content;
    }

    public static void main(String[] args) {
        Box<Integer> integerBox = new Box<>(10);
        Box<String> stringBox = new Box<>("Hello World");

        System.out.printf("Integer Value: %d\n", integerBox.getContent());
        System.out.printf("String Value: %s\n", stringBox.getContent());
    }
}
```

La salida del programa anterior será:

```bash
Integer Value: 10
String Value: Hello World
```

En el ejemplo anterior hemos creado una clase genérica llamada `Box` que puede
almacenar cualquier tipo de objeto. La clase `Box` tiene un tipo de parámetro `T`
que se utiliza para almacenar el tipo de objeto que se va a almacenar en la caja.

El constructor de la clase `Box` toma un parámetro de tipo `T` que se utiliza para
inicializar el campo `content`. El método `getContent` devuelve el contenido de la
caja que es de tipo `T`.

En el método `main` hemos creado dos instancias de la clase `Box`. La primera instancia
de la clase `Box` almacena un objeto de tipo `Integer` y la segunda instancia de la
clase `Box` almacena un objeto de tipo `String`.

### Ejemplo de clase genérica con múltiples tipos de parámetros

```java
public class Pair<T, U> {
    private T first;
    private U second;

    public Pair(T first, U second) {
        this.first = first;
        this.second = second;
    }

    public T getFirst() {
        return first;
    }

    public U getSecond() {
        return second;
    }

    public static void main(String[] args) {
        Pair<Integer, String> pair = new Pair<>(1, "One");
        System.out.printf("First: %d, Second: %s\n", pair.getFirst(), pair.getSecond());

        Pair<String, String> otherPair = new Pair<>("One", "Two");
        System.out.printf("First: %s, Second: %s\n", otherPair.getFirst(), otherPair.getSecond());
    }
}
```

La salida del programa anterior será:

```bash
First: 1, Second: One
First: One, Second: Two
```

En el ejemplo anterior hemos creado una clase genérica llamada `Pair` que
tiene dos tipos de parámetros `T` y `U`. La clase `Pair` tiene dos campos
`first` y `second` que son de tipo `T` y `U` respectivamente. El constructor
de la clase `Pair` toma dos parámetros de tipo `T` y `U` que se utilizan para
inicializar los campos `first` y `second`.

## Interfaces genéricas
Podemos crear interfaces genéricas que puedan ser implementadas por diferentes tipos de objetos.

```java
public interface Box<T> {
    T getContent();
}

public class BoxImpl<T> implements Box<T> {
    private T content;

    public BoxImpl(T t) {
        this.content = t;
    }

    @Override
    public T getContent() {
        return content;
    }

    public static void main(String[] args) {
        Box<Integer> integerBox = new BoxImpl<>(10);
        Box<String> stringBox = new BoxImpl<>("Hello World");

        System.out.printf("Integer Value: %d\n", integerBox.getContent());
        System.out.printf("String Value: %s\n", stringBox.getContent());
    }
}
```

En el ejemplo anterior hemos creado una interfaz genérica llamada `Box` que
tiene un tipo de parámetro `T`. La interfaz `Box` tiene un método `getContent`
que devuelve el contenido de la caja que es de tipo `T`.

La clase `BoxImpl` implementa la interfaz `Box` y proporciona una implementación
del método `getContent`. La clase `BoxImpl` tiene un tipo de parámetro `T` que
se utiliza para inicializar el campo `content`. El método `getContent` devuelve
el contenido de la caja que es de tipo `T`.

## Métodos genéricos

Podemos crear métodos genéricos que puedan ser invocados con parametros de diferentes tipos.

```java
class Test {
    public static <T> void genericDisplay(T element) {
        System.out.println(element.getClass().getName() + " = " + element);
    }

    public static void main(String[] args) {
        genericDisplay(11);
        genericDisplay("Hello World");
        genericDisplay(1.0);
    }
}
```

La salida del programa anterior será:

```bash
java.lang.Integer = 11
java.lang.String = Hello World
java.lang.Double = 1.0
```

En el ejemplo anterior hemos creado un método genérico llamado `genericDisplay`
que puede ser invocado con parámetros de diferentes tipos. El método imprime la
clase y el valor del parámetro que se le pasa.

## Restricciones de tipo genérico

### Extends

Podemos restringir el tipo de parámetro genérico a un cierto tipo o subtipo o
interfaz utilizando la palabra clave `extends`.

```java
public class Box<T extends Number> {
    // ...
} 
```

En el ejemplo anterior hemos restringido el tipo de parámetro genérico `T` a
un tipo `Number` o subtipo de `Number`. 

### Super

Esta restricción es opuesta a la restricción `extends`. Podemos restringir el
tipo de parámetro genérico a un cierto tipo o super tipo de ese tipo.

```java
public class Box<T super Integer> {
    // ...
} 
```
En la clase anterior hemos restringido el tipo de parámetro genérico `T` a un
tipo `Integer` o super tipo de `Integer`, es decir, `Number` o `Object`.

### Multiple bounds

Podemos restringir el tipo de parámetro genérico a múltiples tipos o interfaces
utilizando la palabra clave `&`.

```java
public class Box<T extends Number & Comparable> {
    // ...
} 
```
En el ejemplo anterior `T` debe ser un tipo `Number` o subtipo de `Number` y
también debe implementar la interfaz `Comparable`.

### Wildcards o comodines

Los comodines se representan con el signo de interrogación `?`. Sirven para
representar con tipos genéricos desconocidos pero que son subtipos de un tipo
concreto. Existen dos tipos: `? extends`(covariante) y `? super`(contravariante).

```java
public void printList(List<? extends Number> list) {
    // ...
}
```
El método anterior puede ser invocado con una lista de cualquier tipo de número
o subtipo de número.

```java
public void printList(List<? super Integer> list) {
    // ...
}
```

El método anterior puede ser invocado con una lista de cualquier tipo que sea
super tipo de `Integer`, es decir, `Number` o `Object`.