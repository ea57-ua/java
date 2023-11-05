# Covarianza en Java
##### Autor: Erik Avagyan

## Contenido
- [Que es la covarianza ?](#que-es-la-covarianza-)
- [Ejemplo](#ejemplo)

## Que es la covarianza ?

La covarianza es un concepto importante en Java que se refiere la capacidad de tratar un objeto de un tipo derivado (subtipo) como si fuera del tipo base(clase padre). La covarianza permite una gran flexibilidad en la creación de estructuras de datos que deben ser capaces de manejar diferentes tipos de datos. En Java se aplica principalmente en las listas.

## Ejemplo

Suponemos que tenemos una clase padre llamada `Animal` que tiene el método `makeSound()` y tres clases hijas `Dog`,`Cat` y `Cow` que heredan de la clase padre `Animal` y sobrescriben el método `makeSound()`.

```java
public class Animal {
    public void makeSound() {
        System.out.println("Animal sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof");
    }
}

public class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}

public class Cow extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Moo");
    }
}
```

Usando la covarianza podemos crear una lista de objetos de tipo `Animal` y agregar objetos de tipo `Dog`,`Cat` y `Cow` a la lista.

```java
List<Animal> animals = new ArrayList<>();
animals.add(new Dog());
animals.add(new Cat());
animals.add(new Cow());
```

Ahora podemos iterar sobre la lista y llamar al método `makeSound()` de cada objeto.

```java
for (Animal animal : animals) {
    animal.makeSound();
}
```

