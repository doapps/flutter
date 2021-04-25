# DOAPPS Flutter Style Guide

# Tabla de Contenido

1. [Variables](#variables)
2. [Clases](#clases)
3. [Métodos](#métodos)
5. [Importaciones](#importaciones)

## Variables

Las variables deben ser declaradas en ingles y 

* Utilice la notación `camelCase` al momento de nombrar una variable `variable`.

```dart
//mal
int PAGINA_INICIAL = 1; 

//bien
int initialPage = 1;
```

* Si la variable se creará dentro de un `Widget` esta debe anteponer un `_` al momento de crear la variable.

```dart
//mal
class _PrincipalState extends State<Principal> {
  int counter = 1;

  @override
  Widget build(BuildContext context) {
   ...
  }
}

//bien
class _PrincipalState extends State<Principal> {
  int _counter = 1;
  
  @override
  Widget build(BuildContext context) {
   ...
  }
}
```

* Cuando una variable sea creará dentro del metodo `build` de un `Widget` esta no debe llevar un `_`.


```dart
//mal
class _PrincipalState extends State<Principal> {
  @override
  Widget build(BuildContext context) {
    final _screenSize = MediaQuery.of(context).size;
   ...
  }
}

//bien
class _PrincipalState extends State<Principal> { 
  @override
  Widget build(BuildContext context) {
    final screenSize = MediaQuery.of(context).size;
   ...
  }
}
```

## Clases

* Se debe utilizar la nomenclatura `PascalCase` para la creación de clases.

```dart
//mal
class productProvider {
    ...
}

//bien
class ProductProvider {
    ...
}
```

* Si una clase no será exportada y solo sera usada en mismo archivo, esta debe ser privada, por lo cual deberá anteponer un `_` en su nombre.

```dart
//mal
class ProductList {
    ...
}

//bien
class _ProductoList {
    ...
}
```

## Métodos

* Para la declaración de metodos debe usar la nomenclatura `camelCase`

### Métodos que retornan un valor

* Debe indicar que tipo de dato retornará el método.

```dart
//mal
getName() {
    return ...;
}

//bien
String getName() {
    return ...;
}
```

* Dado el caso que el método sea asincrona debe retornar un `Future<type>`

```dart
//mal
getName() async {
    return ...;
}

//bien
Future<String> getName() async {
    return ...;
}
```
### Métodos que retornan un valor

* Si el método no retorna ningún valor dicho método debe ser de tipo `void`.

```dart
//mal
setValue() {
    ...
}

//bien
void setValue() {
    ...
}
```

* Dado el caso que el método sea asincrona debe retornar un `Future<void>`

```dart
//mal
setValue() {
    ...
}

//bien
Future<void> setValue() async {
    ...
}
```

### Métodos con envío de parametros

* Para los métodos con envío de parametros estos se deben indicar con su tipo al momento de declarar la función, el nombre de los parametros debe seguir la nomenclatura `camelCase` y los parametros deben tener un espacio entre ellos.

```dart
//mal
setUserInfo(firstName,lastName, age) {
    ...
}

//bien
Future<void> setNames(String firstName, String lastName, Int age) async {
    ...
}
```