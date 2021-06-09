# DOAPPS Flutter Style Guide

# Table of Contents

- [Variables](#variables)
- [Classes](#classes)
- [Methods](#methods)
- [Files and Folders](#files-and-folders)
- [Reserved Words](#reserved-words)
- [Imports](#imports)
- [Spacing](#spacing)

## Variables

### Naming

Variables should be declared in English:

- Use the `camelCase` notation when naming a `variable`.

```dart
//bad
int PAGINA_INICIAL = 1;

//good
int initialPage = 1;
```

- If the variable will be created inside a `Widget` it must be private.

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

- When a variable is created within the `build` method of a `Widget` it should not be private.

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

### Naming

- Use the `PascalCase` notation when naming a `class`.

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

### Exports

- If a `class` will not be exported and will only be used in the same file, it must be private, so you must prepend a `_` in its name.

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

### Naming

- Use the `camelCase` notation when naming a `method`.

- If a `method` will not be exported and will only be used in the same file, it must be private, so you must prepend a `_` in its name.

### Return value

- It must indicate what type of data the method returns.

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

- If the case that the method is asynchronous it must return a `Future <type>`

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

### Not return value

- If the method does not return any value, the method must be of type `void`.

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

- In the case that the method is asynchronous it must return a `Future <void>`

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

### Sending parameters

- Methods with sending parameters, these must be indicated with their type when declaring the method, the name of the parameters must follow the `camelCase` notation and the parameters must have a space between them.

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

## Files and Folders

### File Naming

For a better practice try to name the files separating words with `Sub-hyphen_`, always the first word must indicate the membership of the function to be performed for both classes or widgets.

- Always see the way the file specifies the function of the file so that you and other programmers understand it as well.
- Do not use capital letters when naming files.
- Use English words only.

```dart
//bad
Glosario.dart
SubMenuData.dart
ProductProvider.dart

//good
glosary_page.dart
glosary_sub_menu.dart
product_provider.dart
```

### Folders naming

- Never use more than three words to name a folder.
- Try not to use folders for each file, you should see how to group files according to their content, that they have consistency.
- Do not boil over in words when naming folders or subfolders.

```dart
//bad
modeloglobalnetworking
    - networkingdata
    - dbmodel

//good
model
    -network
    -entitydb
```

- In the first example the class is not very well understood and in the sub folders it makes the modelglobalnetworkin class redundant.
- In the good example, one word describes what the class contains, which are models, and separates the subfolders in that way.

## Reserved Words

### const

Const is only used when it already has a default value and it will never change for example if we perform this function:

```dart
//bad
const data = 1 + 1;

//good
const data = 2;
```

In the example we see that const cannot be used in data that will change since in the first example const does not have a value as such. and when he adds it, its value is 2.
But since it is const it does not accept that because.

- Const is only used when the variable or final value is already defined and will never change in the application's life state.

### final

Final indicates that the variable or field must have an initializer, and once it is initialized it will not be able to change its value.

- Unlike final const it is used when you need to assign a value at compile time.

```dart
//Can be done
final int data;
data = 1 + 1;

//But if you try
final int data;
data = 1 + 1;
data = 3; // bad as only a single value can be assigned.

```

### static

The static keyword is used for a class-level variable and a method that is the same for every instance of a class, this means that if a data member is static, it can be accessed without creating an object.

```dart
class GlosarioPage extends StatelessWidget {
    static String keyClass = ' ';
}

//Can be accessed without creating the object

//bad
GlossaryPage().keyClass;

//good
GlossaryPage.keyClass;

```

### late

Late is a reserved word in dart 2.0 that indicates that the value will not be `null` and that a value will be assigned later.

### extends

We use this reserved word when we want to inherit functions and variables from the parent.

### implements

We use this reserved word to force re-implementation of instance functions

## Imports

- All imports must be through packages, that is, through absolute path.
- Imports must be arranged alphabetically.

```dart
//bad
import '../presentation/routes/routes.dart';
import '../presentation/ui/onboarding/widgets/onboarding_card.dart';
import '../core/language/translator.dart';

//good
import 'package:userapp/core/language/translator.dart';
import 'package:userapp/presentation/routes/routes.dart';
import 'package:translateapp/presentation/ui/onboarding/widgets/onboarding_card.dart';
```

## Spacing

### Variables

- You should see a space when using the '=' and the variable value

```dart
//bad
final counter=0;

//good
final counter = 4;
```

### Classes

- In the case of classes, there must be a space between the name and the sign '{'

```dart
//bad
class UserModel{
    ...
}

//good
class UserModel {
    ...
}
```

```dart
//bad
class UserBloc extends NotifierListener{
    ...
}

//good
class UserBloc extends NotifierListener {
    ...
}
```

### Methods

- The methods must have a space between the last parenthesis ')' and the brace '{'

```dart
//bad
Widget build(BuildContext context){
    return ...;
}

//good
Widget build(BuildContext context) {
    return ...;
}
```

- For methods that receive parameters you should see a spacing of a ',' and a space between the parameters

```dart
//bad
int addition(int num1,int num2){
    return ...;
}

//good
int addition(int num1, int num2) {
    return ...;
}
```
