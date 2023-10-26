# Herencia 
##### Autor: Erik Avagyan

## Contenido
- [**Que es la herencia ?**](#que-es-la-herencia)
    - [**Por que usar herencia ?**](#por-que-usar-herencia)
- [**Tipos de herencia**](#tipos-de-herencia)
    - [**Herencia simple o single inheritance**](#herencia-simple-o-single-inheritance)
    - [**Herencia multinivel o multilevel inheritance**](#herencia-multinivel-o-multilevel-inheritance)
    - [**Herencia jerárquica o hierarchical inheritance**](#herencia-jerárquica-o-hierarchical-inheritance)
    - [**Herencia múltiple o multiple inheritance**](#herencia-múltiple-o-multiple-inheritance)
- [**Herencia en Java**](#herencia-en-java)
    - [**Reglas de herencia en Java**](#reglas-de-herencia-en-java)
- [**Casting de objetos**](#casting-de-objetos)

## Que es la herencia ?
La **herencia** es un concepto fundamental en la **programación orientada a objetos** que 
nos permite crear nuevas clases basadas en clases existentes. En Java, la herencia 
es una característica poderosa que facilita la reutilización de código y la organización 
de nuestros programas.

La herencia en Java es un mecanismo que permite que una clase adquiera propiedades y 
comportamientos (campos y métodos) de otra clase. La **clase padre**(superclase) es la clase cuyas
propiedades y comportamientos se heredan, y la **clase hija**(subclase) es la clase que hereda. 

### Por que usar herencia ?
- La herencia permite **reutilizar código**. El código de la superclase es común a las subclases, por lo que no es necesario volver a escribirlo en cada subclase.
Las clases hijas usan el código de la clase padre heredando sus métodos y atributos.
- La herencia permite **extender el código**. Podemos agregar nuevos métodos y atributos a la clase hija sin afectar a la clase padre.
- Podemos **sobreescribir los métodos** de la clase padre en la clase hija para cambiar su comportamiento.

## Tipos de herencia

### Herencia simple o single inheritance
![Herencia simple](https://miro.medium.com/v2/resize:fit:558/format:webp/1*tiWlegYWK335l_yDJLwjgw.png)
La `clase B` es una subclase de la `clase A` si la `clase B` extiende la `clase A`.  Una clase hija puede heredar de una sola clase padre. Es la herencia más común.

```java
class Padre {
    // Atributos y métodos de la clase padre
}

class Hijo extends Padre {
    // Atributos y métodos de la clase hija
}
```
### Herencia multinivel o multilevel inheritance
![Herencia multinivel](https://miro.medium.com/v2/resize:fit:468/format:webp/1*oyUS1L9ShlkWZmENfVQJmg.png)

Una clase puede heredar de una clase que a su vez hereda de otra clase. Es decir, una clase hija puede ser la clase padre de otra clase. 

```java
class A {
    // Atributos y métodos de la clase A
}
class B extends A {
    // Atributos y métodos de la clase B
}
class C extends B {
    // Atributos y métodos de la clase C
}
```
La `clase C` hereda de la `clase B` que a su vez hereda de la `clase A`. La `clase C` hereda todos los atributos y métodos de la `clase B` y la `clase A`.

### Herencia jerárquica o hierarchical inheritance
![Herencia jerárquica](https://miro.medium.com/v2/resize:fit:640/format:webp/1*mFxgt1R-THhRdyKt4ZMH6A.png)

Una clase puede tener más de una subclase. Es decir, una clase padre puede tener más de una clase hija. 

```java
class A {
    // Atributos y métodos de la clase A
}
class B extends A {
    // Atributos y métodos de la clase B
}
class C extends A {
    // Atributos y métodos de la clase C
}
```
La `clase A` es la clase padre de la `clase B` y la `clase C`. La `clase B` y la `clase C` heredan todos los atributos y métodos de la `clase A`.

### Herencia múltiple o multiple inheritance
![Herencia múltiple](https://miro.medium.com/v2/resize:fit:640/format:webp/1*4JFfAofGp7s6DtYRCr-0_g.png)

Una clase puede heredar de más de una clase. Es decir, una clase hija puede tener más de una clase padre. **En Java NO se permite la herencia multiple**. Se puede simular usando interfaces. 

```java
interface A {
}

interface B {
}

class C implements A, B {
}
``` 
Se puede usar la herencia multiple en lenguajes como C++, pero no en Java.

## Herencia en Java
En Java, la herencia se implementa usando la palabra clave `extends`. La sintaxis es la siguiente:

```java
class Animal {
    // Atributos y métodos de la clase Animal
}

class Perro extends Animal {
    // Atributos y métodos de la clase Perro
}
``` 

La `clase Perro` hereda de la `clase Animal`. La `clase Animal` es la clase padre de la `clase Perro`. La `clase Perro` es la clase hija de la `clase Animal`. Un objeto `Perro` es también un objeto `Animal`.

### Reglas de herencia en Java
- La herencia multiple no está permitida en Java. Una clase puede heredar de una sola clase.
- La herencia ciclica no está permitida en Java. Una clase no puede heredar de si misma.
- Los **atributos y métodos privados no se heredan**. 
- Los **constructores no se heredan**. Sin embargo, el constructor de la clase padre se invoca desde el constructor de la clase hija usando la palabra clave `super()`.

```java
// Clase padre
class Figura {
    public double calcularArea() {
        return 0.0;
    }
}

// Clase hija
class Circulo extends Figura {
    private double radio;

    public Circulo(double radio) {
        this.radio = radio;
    }

    public double getRadio() {
        return radio;
    }

    @Override
    public double calcularArea() {
        return Math.PI * radio * radio;
    }
}

public class Main {
    public static void main(String[] args) {
        Circulo miCirculo = new Circulo(5.0);
        
        // Podemos llamar al método heredado calcularArea() desde la subclase
        double areaDelCirculo = miCirculo.calcularArea();
        
        // También podemos acceder a los métodos específicos de la subclase
        double radioDelCirculo = miCirculo.obtenerRadio();
        
        System.out.println("Área del círculo: " + areaDelCirculo);
        System.out.println("Radio del círculo: " + radioDelCirculo);
    }
}
```

## Casting de objetos
![Casting de objetos](https://media.geeksforgeeks.org/wp-content/uploads/20210119153952/Downcasting.jpg)

El casting de objetos es la conversión de un tipo de objeto a otro. En Java, el casting de objetos se puede dividir en dos tipos:
- **Upcasting**: convertir un objeto de una subclase a un objeto de la superclase.
- **Downcasting**: convertir un objeto de una superclase a un objeto de la subclase. Provoca una excepción `ClassCastException` si no se usa `instanceof`.

```java
class Parent {
    public void show() {
        System.out.println("Parent show method is called");
    }
} 

class Child extends Parent {
    @Override
    public void show() {
        System.out.println("Child show method is called");
    }
}

class Main {
    public static void main(String[] args) {
        // Upcasting
        Parent parent = new Child();
        parent.show(); // Child show method is called
        
        // Downcasting
        Child child = (Child) parent;
        child.show(); // Child show method is called
    }
}
```

