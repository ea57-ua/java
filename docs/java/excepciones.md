# Excepciones
##### Autor: Erik Avagyan

## Contenido
- [Que es una excepcion?](#que-es-una-excepcion)
- [Jerarquía de excepciones](#jerarquía-de-excepciones)
- [Tipos de excepciones](#tipos-de-excepciones)
    - [Excepciones comprobadas o checked exceptions](#excepciones-comprobadas-o-checked-exceptions)
    - [Excepciones no comprobadas o unchecked exceptions o `Runtime exceptions`](#excepciones-no-comprobadas-o-unchecked-exceptions-o-runtime-exceptions)
- [Manejo de excepciones](#manejo-de-excepciones)
    - [Bloque try-catch](#bloque-try-catch)
    - [Lanazamiento de excepciones](#lanazamiento-de-excepciones)
- [Excepciones definidas por el usuario](#excepciones-definidas-por-el-usuario)

## Que es una excepcion?

Una excepción en Java es un evento inesperado que puede interrumpir el flujo de la ejecución. Se usan las excepciones para manejar errores y otros eventos que pueden ocurrir durante la ejecución de un programa.

## Jerarquía de excepciones

![Jerarquía de excepciones](https://lh5.googleusercontent.com/WqqNoyFEkZXfmZBBQjgIutY72_BUV6_By_BAe7Ih9u36HfelS3nTWQEYtdRUkQS32Tuhg9P9CUXo-jgvOpkO84vLm2viI4Od0BNustwONdMm7DKZnKC6kyVHyRJbsESLIPV4uBU) 

La clase base de todas las excepciones es la clase **Throwable**. Esta clase tiene dos subclases directas: **Error** y **Exception**. La clase **Error** representa errores que no se pueden recuperar, como por ejemplo un error de memoria. La clase **Exception** representa errores que se pueden recuperar, como por ejemplo un error de división por cero. La clase **Exception** tiene varias subclases, que representan diferentes tipos de excepciones. Por ejemplo, la clase ArithmeticException representa una excepción de división por cero.

## Tipos de excepciones

Las excepciones se dividen en dos tipos:

### Excepciones comprobadas o checked exceptions
Excepción que ocurre en **tiempo de compilación**. El compilador obliga a que se capture o se lance la excepción. 

Ejemplos: 
- FileNotFoundException
- IOException
- SQLException

### Excepciones no comprobadas o unchecked exceptions o `Runtime exceptions`
Excepción que ocurre en **tiempo de ejecución**. El compilador no obliga a que se capture o se lance la excepción.

Ejemplos:
- NullPointerException
- ArrayIndexOutOfBoundsException
- ArithmeticException

![Tipos de excepciones](https://miro.medium.com/v2/resize:fit:729/1*jd1wo9joMCehuDqAdZ5m6A.png)

## Manejo de excepciones

### Bloque try-catch
La estructura `try-catch` se usa para manejar excepciones. En `try` se coloca el código que puede lanzar una excepción. En `catch` se coloca el código que se ejecuta cuando se lanza una excepción.

```java
    try {
        // Código que puede generar una excepción
    } catch (ExcepcionTipo1 e) {
        // Manejar la excepción de tipo 1
    } catch (ExcepcionTipo2 e) {
        // Manejar la excepción de tipo 2
    }
```

En el código de catch podemos hacer diferentes cosas:
-  Imprimir un mensaje de error
-  Relanzar la excepción
-  Lanzar una nueva excepción
-  Hacer alguna acción, depende del contexto

En Java también existe el bloque `try-catch-finally`. El bloque `finally` se ejecuta siempre, independientemente de si se lanza una excepción o no.

```java
    try {
        // Código que puede generar una excepción
    } catch (ExcepcionTipo1 e) {
        // Manejar la excepción de tipo 1
    } catch (ExcepcionTipo2 e) {
        // Manejar la excepción de tipo 2
    } finally {
        // Código que se ejecuta siempre
    }
```

### Lanazamiento de excepciones

Para lanzar una excepción se usa la palabra clave `throw`. Se puede lanzar una excepción de cualquier tipo, pero es recomendable lanzar una excepción de un tipo existente.

```java
    throw new ExcepcionTipo1();
```

Podemos hacer que el método actual lance una excepción usando la palabra clave `throws`. En este caso, el método actual no maneja la excepción, sino que la lanza al método que lo llamó.

```java
    public void metodo1() throws ExcepcionTipo1 {
        // Código que puede generar una excepción
    }
```

## Excepciones definidas por el usuario

Se pueden definir excepciones personalizadas. Para esto, se debe crear una clase que herede de la clase `Exception` o de la clase `RuntimeException`. La clase `Exception` se usa para crear excepciones comprobadas, mientras que la clase `RuntimeException` se usa para crear excepciones no comprobadas.

```java
    public class MiExcepcion extends Exception {
        // Código de la clase
    }
```

```java
    public class MiExcepcion extends RuntimeException {
        // Código de la clase
    }
```

Crear nuestras excepciones ayuda a clasificar mejor los errores de la aplicación. Se añaden mensajes significativos que ayudan durante el proceso de desarrollo. Cuanto más especifica una excepción el control de los errores es más granular. 

Contructores de excepciones personalizadas:
```java
public class MiExcepcionPersonalizada extends Exception {
    public MiExcepcionPersonalizada() {
        super("Ocurrió un error personalizado.");
    }

    public MiExcepcionPersonalizada(String mensaje) {
        super(mensaje);
    }
}
```

Otro ejemplo:
```java
public class MiExcepcionConAtributo extends Exception {
    // Atributo personalizado
    private int codigoError;

    // Constructor que acepta un código de error
    public MiExcepcionConAtributo(int codigoError) {
        this.codigoError = codigoError;
    }

    // Sobrescribe el método getMessage() para incluir el código de error en el mensaje
    @Override
    public String getMessage() {
        return "MiExcepcionConAtributo: Código de error " + codigoError;
    }
}
``` 

Como se usa:
```java
public class Ejemplo {
    public static void main(String[] args) {
        try {
            throw new MiExcepcionConAtributo(404);
        } catch (MiExcepcionConAtributo e) {
            System.out.println(e.getMessage()); 
            // Imprime: "MiExcepcionConAtributo: Código de error 404"
        }
    }
}
``` 