# Interfaces 
##### Autor: Erik Avagyan

## Contenido
- [**Que es una interfaz ?**](#que-es-una-interfaz)
- [**Usos y reglas de las interfaces**](#usos-y-reglas-de-las-interfaces)
- [**Ejemplo**](#ejemplo)

## Que es una interfaz ?
Las interfaces en Java son un mecanismo para conseguir más nivel de abstracción. Una interfaz es una colección de métodos abstractosm no pueden tener implementaciones.  Define las firmas de los métodos, es 
decir, el nombre, los parámetros y el tipo de retorno, pero no su implementación. 

Para crear una interfaz, usamos la palabra clave `interface` en lugar de `class`. 

```java
interface InterfaceName {
    // Constantes
    final int CONSTANT = 100;
    // Métodos abstractos por defecto
    int method1();
    double methood2();
}
```

## Usos y reglas de las interfaces 

-  Las interfaces se usan para lograr la abstracción.
-  Las interfaces se usan para lograr la funcionalidad de múltiples herencias.
-  Una clase puede implementar más de una interfaz.
-  Una clase puede heredar de una clase e implementar una o más interfaces.
-  Las variables declaradas en una interfaz son por defecto `public`, `static` y `final`.
-  No se puede crear una instancia de una interfaz pero se puede crear una referencia de una interfaz.
-  Una interfaz puede extender otra interfaz.
-  Una clase que implementa una interfaz debe implementar todos sus métodos.
-  No hay constructores en una interfaz.
-  No hay método `main()` en una interfaz.
-  No se puede declarar métodos como  `private`, `static` o `final` en una interfaz.

![Relaciones entre clases e interfaces](https://media.geeksforgeeks.org/wp-content/uploads/20230419112343/Intefaces-in-Java-1.webp)


## Ejemplo

```java
public interface Vehicle {
    // Constantes
    final int MAX_SPEED = 100;
    // Métodos abstractos
    void changeGear(int a);
    void speedUp(int a);
    void applyBrakes(int a);
}

public class Car implements Vehicle {
    int speed;
    int gear;

    // Implementación de los métodos abstractos
    @Override
    public void changeGear(int newGear) {
        // ...
    }

    @Override
    public void speedUp(int increment) {
        // ...
    }

    @Override
    public void applyBrakes(int decrement) {
        // ...
    }
}

public class Motocycle implements Vehicle {
    @Override
    public void changeGear(int newGear) {
        // ...
    }

    @Override
    public void speedUp(int increment) {
        // ...
    }

    @Override
    public void applyBrakes(int decrement) {
        // ...
    }
}
```

Podemos crear una referencia de una interfaz y usarla para referir a un objeto de una clase que implementa la interfaz. Por ejemplo:

```java
public class Test {
    public static void main(String[] args) {
        Vehicle car = new Car();
        Vehicle motocycle = new Motocycle();

        car.changeGear(2);
        car.speedUp(3);
        motocycle.changeGear(1);
        motocycle.speedUp(4);
    }
}
```
