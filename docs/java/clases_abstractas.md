# Clases abstractas
##### Autor: Erik Avagyan

## Contenido
- [Que son las clases abstractas?](#que-son-las-clases-abstractas)
- [Herencia de clases abstractas](#herencia-de-clases-abstractas)
- [Observaciones importantes sobre las clases abstractas](#observaciones-importantes-sobre-las-clases-abstractas)

## Que son las clases abstractas?

En Java, una clase abstracta es una clase que **no se puede instanciar**. La clase abstracta puede contener **métodos abstractos** y métodos concretos (implementados). Los métodos abstractos son métodos que no tienen implementación. Los métodos concretos son métodos que tienen implementación. Las clases abstractas se definen con la palabra clave `abstract`.

```java
public abstract class Figura {
    public abstract double area();
    public abstract double perimetro();
}
```

Una clase abstracta puede tener atributos, métodos abstractos y métodos concretos. Los métodos abstractos se declaran con la palabra clave `abstract` y no tienen implementación. Deben ser implementados en las subclases que heredan de la clase abstracta. 

Las clases abstractas se utilizan como plantilla para implementar subclases concretas que deben implementar **todos** los métodos abstractos. 

![Herencia de clase abstracta](https://docs.oracle.com/javase/tutorial/figures/java/classes-graphicObject.gif)

## Herencia de clases abstractas

Una subclase que hereda de una clase abstracta debe implementar todos los métodos abstractos de la clase abstracta. 

```java
public abstract class Figura {
    public abstract double calcularArea();
}

public class Circulo extends Figura {
    private double radio;

    public Circulo(double radio) {
        this.radio = radio;
    }

    @Override
    public double calcularArea() {
        return Math.PI * radio * radio;
    }
}

``` 
Si la subclase no implementa todos los métodos abstractos, la subclase debe declararse como abstracta.

```java
public abstract class Figura {
    public abstract double calcularArea();
}

public abstract class Circulo extends Figura {
    private double radio;

    public Circulo(double radio) {
        this.radio = radio;
    }

    public abstract double calcularPerimetro();
}

public class CirculoConcreto extends Circulo {
    public CirculoConcreto(double radio) {
        super(radio);
    }

    @Override
    public double calcularArea() {
        return Math.PI * radio * radio;
    }

    @Override
    public double calcularPerimetro() {
        return 2 * Math.PI * radio;
    }
}
```

## Observaciones importantes sobre las clases abstractas

- Una clase abstracta no se puede instanciar.
- Una clase abstracta puede tener constructores.
- Una clase abstracta puede tener atributos.
- Una clase abstracta puede tener métodos estáticos.
- Si una subclase no implementa todos los métodos abstractos de la clase abstracta, la subclase debe declararse como abstracta.