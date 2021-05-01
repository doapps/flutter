# DOAPPS Flutter Style Guide

# Tabla de Contenido

1. [Variables](#variables)
2. [Clases](#clases)
3. [Métodos](#métodos)
4. [Archivos](#archivos)
5. [Palabras Reservadas](#palabras_reservadas)
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
## Archivos y Carpetas

### Nombramiento de archivos o clases

Para una mejor practica intente nombrar los archivos separando palabras con `Subguion _`, siempre la primera palabra debe indicar la pertenencia a la funcion a realizar tanto para clases o widgets.

* Siempre vea la forma que el archivo especifique la funcion del archivo de modo que usted lo entienda y otros programadores tambien.
* No use mayusculas al nombrar los archivos.
* Utilize palabras en ingles unicamente.
```

//mal

Glosario.dart

SubMenuData.dart

ProductProvider.dart

//bien
glosary_home_page.dart

glosary_sub_menu.dart

product_provider.dart
```

### Nombramiento de carpetas

* Nunca use mas de tres palabras para nombrar una carpeta.
* Intente no usar carpetas para cada archivo, debe de ver la forma de agrupar archivos segun su conteniendo, que tengan coherencia.
* No rebundar en palabras al nombrar las carpetas o subcarpetas.

```
//mal
modeloglobalnetworking
    - networkingdata
    - dbmodel

//bien

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
//Mal
const data=1+1;
//Mal
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

//Mal

GlosarioPage().keyClass;

//Bien

GlosarioPage.keyClass;

```

### late

Late es una palabra reservada en dart 2.0 que indica que el valor no sera  `nulo` y que se asignara un  valor mas adelante.

### extends

Usamos esta palabra reservada cuando queremos heredar las funciones y variables del padre. 

### implements

Usamos esta palabra reservada para forzar la re-implementacion de funciones de la instancia 
