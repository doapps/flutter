# DOAPPS Flutter Style Guide

# Table of Contents

1. [Variables](#variables)
2. [Classes](#classes)
3. [Methods](#methods)
4. [Files](#files)
5. [Reserved Words](#reserved_words)
5. [Imports](#imports)

## Variables

Variables should be declared in English: 

* Use the `camelCase` notation when naming a `variable`.

```dart
//bad
int PAGINA_INICIAL = 1; 

//good
int initialPage = 1;
```

* If the variable will be created inside a `Widget` it must be private.

```dart
//bad
class _PrincipalState extends State<Principal> {

  int counter = 1;

  @override
  Widget build(BuildContext context) {
   ...
  }
}

//good
class _PrincipalState extends State<Principal> {

  int _counter = 1;
  
  @override
  Widget build(BuildContext context) {
   ...
  }
}
```

* When a variable is created within the `build` method of a `Widget` it should not be private.


```dart
//bad
class _PrincipalState extends State<Principal> {
  @override
  Widget build(BuildContext context) {
    final _screenSize = MediaQuery.of(context).size;
   ...
  }
}

//good
class _PrincipalState extends State<Principal> { 
  @override
  Widget build(BuildContext context) {
    final screenSize = MediaQuery.of(context).size;
   ...
  }
}
```

## Classes

* Use the `PascalCase` notation when naming a `class`.

```dart
//bad
class productProvider {
    ...
}

//good
class ProductProvider {
    ...
}
```

* If a `class` will not be exported and will only be used in the same file, it must be private, so you must prepend a `_` in its name.

```dart
//bad
class ProductList {
    ...
}

//good
class _ProductList {
    ...
}
```

## Methods

* Use the `camelCase` notation when naming a `method`.


* If a `method` will not be exported and will only be used in the same file, it must be private, so you must prepend a `_` in its name.
### Methods that return a value

* It must indicate what type of data the method returns.

```dart
//bad
getName() {
    return ...;
}

//good
String getName() {
    return ...;
}
```

* If the case that the method is asynchronous it must return a `Future <type>`

```dart
//bad
getName() async {
    return ...;
}

//good
Future<String> getName() async {
    return ...;
}
```
### Methods that don't return a value

* If the method does not return any value, the method must be of type `void`.

```dart
//bad
setValue() {
    ...
}

//good
void setValue() {
    ...
}
```

* In the case that the method is asynchronous it must return a `Future <void>`

```dart
//bad
setValue() {
    ...
}

//good
Future<void> setValue() async {
    ...
}
```

### Methods with sending parameters

* Methods with sending parameters, these must be indicated with their type when declaring the method, the name of the parameters must follow the `camelCase` notation and the parameters must have a space between them.

```dart
//bad
setUserInfo(firstName,lastName, age)async {
    ...
}

//good
Future<void> setUserInfo(String firstName, String lastName, Int age) async {
    ...
}
```
## Archivos y Carpetas

### Nombramiento de archivos o clases

Para una mejor practica intente nombrar los archivos separando palabras con `Subguion _`, siempre la primera palabra debe indicar la pertenencia a la funcion a realizar tanto para clases o widgets.

* Siempre vea la forma que el archivo especifique la funcion del archivo de modo que usted lo entienda y otros programadores tambien.
* No use mayusculas al nombrar los archivos.
* Utilize palabras en ingles unicamente.
```

//bad

Glosario.dart

SubMenuData.dart

ProductProvider.dart

//good
glosary_home_page.dart

glosary_sub_menu.dart

product_provider.dart
```

### Nombramiento de carpetas

* Nunca use mas de tres palabras para nombrar una carpeta.
* Intente no usar carpetas para cada archivo, debe de ver la forma de agrupar archivos segun su conteniendo, que tengan coherencia.
* No rebundar en palabras al nombrar las carpetas o subcarpetas.

```
//bad
modeloglobalnetworking
    - networkingdata
    - dbmodel

//good

model
    -network
    -entitydb
```

* En el ejemplo primero no se entiende muy bien la clase y en los sub carpetas hace rebundancia a la clase modelglobalnetworkin.
* En el buen ejemplo en  una palabra se describe lo que contiene la clase que son modelos y las subcarpetas las separa de ese modo.

## Palabras Reservadas

### const
Const se usa unicamente cuando ya tiene un valor por defecto y nunca cambiara por ejemplo si realizamos esta esta funcion:
```dart
//bad
const data=1+1;
//bad
const data=2;
```
En el  ejemplo vemos que no se puede usar const en datos que cambiaran ya que en el primer ejemplo const no tiene un valor como tal. y cuando lo suma su valor es 2.
Pero como es const no acepta eso por que.
* Solamente se usa const cuando la variable o valor final ya esta definido y nunca cambiara en el estado de vida del aplicativo. 
### final
Final indica que la variable o campo debe tener un inicializador, y una vez se inicialize  no podra a cambiar su valor.

*A diferencia de const final se usa cuando se necesita asignar un valor en tiempo de compilacion. 
```dart
//Se puede realizar
final int data;
data =1+1;
//Pero si intentas
final int data;
data = 1+1;
data = 3; // mal ya que solamente se puede asignar un valor unico.

```
### static

La palabra clave static se utiliza para una variable de nivel de clase y un método que es el mismo para cada instancia de una clase, esto significa que si un miembro de datos es estático, se puede tener acceso a ella sin crear un objeto.
```dart
class GlosarioPage extends StatelessWidget {
    static String keyClass = " ";
}

//Se puede acceder sin crear el objeto

//bad

GlosarioPage().keyClass;

//good

GlosarioPage.keyClass;

```

### late

Late es una palabra reservada en dart 2.0 que indica que el valor no sera  `nulo` y que se asignara un  valor mas adelante.

### extends

Usamos esta palabra reservada cuando queremos heredar las funciones y variables del padre. 

### implements

Usamos esta palabra reservada para forzar la re-implementacion de funciones de la instancia 
