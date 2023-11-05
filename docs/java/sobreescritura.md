# Sobreescritura de métodos
##### Autor: Erik Avagyan

## Contenido
- [Sobreescritura de métodos](#sobreescritura-de-métodos)
- [Ejemplo](#ejemplo)
- [Reglas para la sobrescritura de métodos](#reglas-para-la-sobrescritura-de-métodos)
- [Sobrescritura VS Sobrecarga](#sobrescritura-vs-sobrecarga)


## Sobreescritura de métodos

La **sobreescritura de métodos** o **override** es una característica de la programación orientada a objetos que permite a una subclase proporcionar una implementación específica de un método que ya está proporcionado por una de sus superclases o clases de interfaces. El método que sobrescribe debe tener el mismo nombre, mismos parámetros y el mismo tipo de retorno que el método que sobrescribe. 

Gracias a la sobrescritura de métodos es posible usar el polimorfismo que explicaremos más adelante.

## Ejemplo

```java
class Parent {
    void show() { System.out.println("Parent's show()"); }
}
 
class Child extends Parent {
    // Sobrescribe el método show() de la clase padre
    @Override void show()
    {
        System.out.println("Child's show()");
    }
}
``` 
Si ejecutamos el siguiente código:
```java
    Parent obj1 = new Parent();
    obj1.show();

    Parent obj2 = new Child();
    obj2.show();
``` 

Obtendremos la siguiente salida:
```bash
Parent's show()
Child's show()
```

## Reglas para la sobrescritura de métodos
- Un método sobrescrito puede tener diferente nivel de acceso pero no un nivel de acceso más restrictivo que el método que sobrescribe. Por ejemplo, si el método de la superclase es declarado protected, el método sobrescrito en la subclase puede ser public, pero no private.

- Los métodos declarados como final o static no pueden ser sobrescritos.

- Los métodos privados no se pueden sobrescribir, ya que no son visibles fuera de la clase.

- El tipo devuelto de un método sobrescrito puede ser un subtipo del tipo devuelto por el método de la superclase.

- Para invocar el método de la superclase, se utiliza la palabra clave super. Por ejemplo, `super.show()` invocará el método show() de la superclase.

## Sobrescritura VS Sobrecarga
La **sobrecarga** de métodos es una característica de la programación orientada a objetos que permite a una clase tener más de un método con el mismo nombre, siempre que la lista de argumentos sea diferente. Esto se conoce como sobrecarga de métodos. Un uso de la sobrecarga de métodos es tener varios constructores que aceptan diferentes conjuntos de argumentos.

```java
public class Suma {
    public int suma(int x, int y) {
        return x + y;
    }
 
    public int suma(int x, int y, int z) {
        return x + y + z;
    }
 
    public double suma(double x, double y) {
        return x + y;
    }
}
```

La **sobrescritura** de métodos es una característica de la programación orientada a objetos que permite a una subclase proporcionar una implementación específica de un método que ya está proporcionado por una de sus superclases o clases de interfaces. El método que sobrescribe debe tener el mismo nombre, mismos parámetros y el mismo tipo de retorno que el método que sobrescribe.