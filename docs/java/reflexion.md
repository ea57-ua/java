# Reflexión 
##### Autor: Erik Avagyan

## Contenido
- [Que es la reflexión ?](#que-es-la-reflexión-)
- [Para que sirve la reflexión ?](#para-que-sirve-la-reflexión-)
- [Métodos básicos de la API de reflexión](#métodos-básicos-de-la-api-de-reflexión)
    - [Obtener una clase](#obtener-una-clase)
    - [Obtener los constructores de una clase](#obtener-los-constructores-de-una-clase)
    - [Obtener los métodos de una clase](#obtener-los-métodos-de-una-clase)
    - [Obtener información sobre los métodos de una clase](#obtener-información-sobre-los-métodos-de-una-clase)
    - [Obtener los campos de una clase](#obtener-los-campos-de-una-clase)
    - [Obtener la superclase de una clase](#obtener-la-superclase-de-una-clase)
    - [Obtener interfaces implementadas por una clase](#obtener-interfaces-implementadas-por-una-clase)
    - [Obtener los modificadores de acceso de una clase](#obtener-los-modificadores-de-acceso-de-una-clase)
    - [Obtener las anotaciones de una clase](#obtener-las-anotaciones-de-una-clase)
    - [Invocar un método](#invocar-un-método)
- [Enlaces de interés](#enlaces-de-interés)

## Que es la reflexión ?

La **reflexión** (en inglés **reflection**) en Java es una API que permite a los programas obtener información sobre el tipo y la estructura de los objetos en tiempo de ejecución. La reflexión permite que los programas puedan utilizar esta información y acceder a los objetos sobre los que se está ejecutando la aplicación. Permite leer 
los metadatos de las clases, interfaces, campos y métodos de clases cargadas en memoria. También permite instanciar clases, invocar métodos, obtener y cambiar el valor de los campos de una clase.

## Para que sirve la reflexión ?

La API de reflexión se utiliza en frameworks de inyección de dependencias, frameworks de persistencia, frameworks de testing, frameworks de mapeo objeto-relacional, frameworks de serialización, etc.

## Métodos básicos de la API de reflexión

### Obtener una clase
En reflexión, las clases se guardan en objetos de tipo Class. Hay varias formas de obtener la clase:

```java
Class<?> c1 = Class.forName("com.example.MyClass");
Class<MyClass> c2 = MyClass.class; // Podemos especificar que tipo de clase esperamos obtener
Class<?> c3 = obj.getClass();
```

### Obtener los constructores de una clase
```java
Class<?> extractClass = Class.forName("models.Employee");
Constructor<?>[] constructors = extractClass.getConstructors();

for (Constructor<?> constructor : constructors) {
    System.out.println(constructor.getName());
}
```

### Obtener los métodos de una clase
El método `getMethods()` devuelve todos los métodos públicos de la clase y de sus superclases. Para obtener todos los métodos de la clase, incluyendo los privados, se utiliza el método `getDeclaredMethods()`.

```java
Class<Persona> extractClass = Persona.class;
Method[] methods = extractClass.getDeclaredMethods();
System.out.println("Métodos de la clase Persona: " + Arrays.toString(methods));
```

### Obtener información sobre los métodos de una clase
```java
Class<Persona> extractClass = Persona.class;
Method[] methods = extractClass.getDeclaredMethods();
for (Method method : methods) {
    System.out.println("Nombre del método: " + method.getName());
    System.out.println("Tipo de retorno: " + method.getReturnType());
    System.out.println("Parámetros: " + Arrays.toString(method.getParameterTypes()));
    System.out.println("Excepciones: " + Arrays.toString(method.getExceptionTypes()));
    System.out.println("Modificadores: " + Modifier.toString(method.getModifiers()));
}
```

### Obtener los campos de una clase
El método `getFields()` devuelve todos los campos públicos de la clase y de sus superclases. Para obtener todos los campos de la clase, incluyendo los privados, se utiliza el método `getDeclaredFields()`.

```java
Class<Persona> extractClass = Persona.class;
Field[] classFields = extractClass.getDeclaredFields();
Field[] allFields = extractClass.getFields(); // Incluye los campos de las superclases
```

### Obtener la superclase de una clase
```java
Class<Persona> myClass = Persona.class;
Class<? super Persona> superClass = myClass.getSuperclass();
```

### Obtener interfaces implementadas por una clase
```java
Class<Persona> myClass = Persona.class;
Class<?>[] interfaces = myClass.getInterfaces();
```

### Obtener los modificadores de acceso de una clase
```java
int modifiers = Persona.class.getModifiers();
System.out.println("Modificadores de acceso de la clase Persona: " + Modifier.toString(modifiers));
```

### Obtener las anotaciones de una clase
```java
Class<Persona> myClass = Persona.class;
Annotation[] annotations = myClass.getAnnotations();
System.out.println("Anotaciones de la clase Persona: " + Arrays.toString(annotations));
```

### Invocar un método
```java
Persona persona = new Persona("Erik", "Avagyan");
Class<Persona> myClass = Persona.class;
Method setAge = myClass.getDeclaredMethod("setAge", int.class);
setAge.setAccessible(true); // si el método es privado
setAge.invoke(persona, 25);
setAge.setAccessible(false);
```

## Enlaces de interés
- [Documentación oficial de la API de reflexión](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Class.html)
- [Tutorial completo de reflexión en Java](https://aeontanvir.medium.com/exploring-java-reflection-api-a-comprehensive-guide-d871f73333ca)