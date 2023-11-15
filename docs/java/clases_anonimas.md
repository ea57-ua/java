# Clases anónimas
##### Autor: Erik Avagyan

## Contenido

## Que son las clases anónimas ?
Las clases anónimas en Java son clases que no tienen nombre. Se utilizan cuando necesitamos crear una clase que se extienda de una clase o implemente una interfaz, pero que no necesitamos usar en ningún otro lugar. Las clases anónimas se implementan en el lugar donde se necesitan.

Se puede crear una clase anónima que extienda una clase o implemente una interfaz, en los dos casos la clase anónima debe implementar los métodos de la interfaz o de la clase abstracta.

## Ejemplo

### Ejemplo con clase abstracta
```java
abstract class Person {
    abstract void eat();
}

class Test {
    public static void main(String args[]) {
        Person p = new Person() {
            @Override
            void eat() {
                System.out.println("nice fruits");
            }
        };

        p.eat();
    }
}
```

### Ejemplo con interfaz
```java
interface Eatable {
    void eat();
}

class Test {
    public static void main(String args[]) {
        Eatable e = new Eatable() {
            @Override
            public void eat() {
                System.out.println("nice fruits");
            }
        };

        e.eat();
    }
}
```

## Reglas 
- Se usan para crear un único objeto.
- Se usan para implementar una interfaz o extender una clase abstracta.
- Una clase anónima solo puede implementar una interfaz.
- Una clase anónima solo puede extender una clase abstracta o implementar una interfaz, pero no ambas.
- Una clase anónima no puede tener constructores.
- Una clase anónima tiene acceso a los miembros de su clase externa.
- Una clase anónima no puede acceder a ninguna variable local en su método que no sea final.
