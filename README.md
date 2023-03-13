# Flutter

# Introduction
Flutter is a powerful and intuitive framework for building beautiful, cross-platform mobile applications that uses the Dart programming language.

This essentially means that Flutter can be used to write one codebase for an app that runs natively on both iOS and Android.

Learning Flutter is both a valuable skill and a gratifying endeavor in its own right. However, the path to learning Flutter is a little unclear due to how new the language is.
- the language is constantly being updated (to the point where tutorials from just a few months ago are out of date)
- there are a lack of freely available, well thought out and comprehensive courses or books compared to some other more established frameworks and languages like python

[What makes Flutter different for app development?](https://www.youtube.com/watch?v=l-YO9CmaSUM)
# Setting Up for Flutter Development
* [Getting Started: Installing Flutter](https://docs.flutter.dev/get-started/install)
* [Git for Windows](https://git-scm.com/downloads)
* [Install Android Studio](https://developer.android.com/studio)\

Once finished, run this command in the terminal to make sure your environment is all ready to go.
```flutter
$ flutter doctor
```
# Learning Dart

Dart is a language developed by Google that is the backbone to the flutter framework. It is the language you will be using when you code up apps with the Flutter framework.
- [Dart Programming in 4 hours | Full beginners tutorial](https://youtu.be/5xlVP04905w)


### Hello World
Every app has a `main()` function. To display text on the console, you can use the top-level `print()` function:
```dart
void main() {
  print('Hello, World!');
}
```
### Variables

Variables in dart are type-checked, which means that every variable must be declared with a specific type, and that type must match with what the variable is assigned throughout your programs.

Here are some basic types and examples:

```dart
String foo = 'foo';
int bar = 0;
double foobar= 12.454;
bool isCool = true;
List<String> foobarList = ['foo', 'bar'];
```

Dictionaries (which map keys to values) are specificed as the 'Map' type in dart. You have to specify the key type and the value type, like as follows.

```dart
Map<String, int> grades = {
  'John': 99,
  'Doe': 30,
};
```

You will get an error if you assign an incompatible type to the same variable.
    
```dart
String errorExample = 'foo';
errorExample = 2; // ERROR
```
    
You can use 'var' and 'dynamic' to make a variable type dynamic, but it is usually not a good idea to do this, as it could end up in frustrating errors down the line.

Additionally, dart has a unique 'final' and 'const' operator that can be used for declaring variables. 'final' is generally used to declare a variable that won't change once it's declared. For example, if a user types in their name and we save it to a variable, we know that variable (their name) won't change, so we can initialize / declare it like so:

```dart
final String name;
```

The 'const' keyword is a little more of a specific use case - it makes the variable constant from compile-time only. It will be useful later down the line for the Flutter framework.

    
### Functions

Functions are declared by specifying the return type, the name of the function, and the parameters within paranetheses. Void is used to specify the return type if nothing is returned. 

```dart
// doesn't return anything but still executes some code
void main() {
  print('hello world');
}

// prints 'hello' but also returns the string 'complete'
String hello(int reps) {
  for (int i = 0; i < reps; i++) {
    print('hello');
  }
  return 'complete';
}

// returns a list of strings (List<String>)
List<String> people() {
  return ['John', 'Doe'];
}
```

Asynchronous functions are functions that can execute different commands at the same time - asynchronously. 

An example of how this would be useful is in calling APIs (basically, trying to retrieve some sort of useful information or data that was programmed by someone else, from the web). If our function calls an API and assigns a variable to the API's response, but our entire App is waiting for that function to finish executing in order to do something, then it isn't very efficient. If we make this function asynchronous, the function calling the API can then execute at the same time that the App allows other functions to execute, or while the App does something else.

Within an asynchronous function, if we ever need our function to wait for some line of code to finish before we continue, we simply precede the code with the keyword, 'await'.
    
For asynchronous functions in dart, add the 'async' keyword between the parentheses and the curly braces, and enclose the return type in 'Future<[return type]>'.

```dart
Future<String> retrieveData() async {
  String response = await someAPICall(); // assuming the api call returns a string
  return response;
}
```

### Conditionals

If statements are simply written as follows:

```dart
bool someCondition = true;

if (someCondition) {
  print('someCondition is true');
} else {
  print('someCondition is false');
}
```

### Loops

For loops are very important in all programming languages, and there are a few ways to implement them in dart.

```dart
List words = ['hello', 'world', '!'];

// 1st way
// declare an int i, increment it by 1 until it is no longer 
// less than words.length (3 in this case)
for (int i = 0; i < words.length; i++) {
  print(words[i]);
} 

// 2nd way
// for each element in word, dart will take that element (in this case, a string, word)
// and will allow you to execute code using that element (here, we just print it out)
// the rocket notation (=>) allows us to write only a single statement to execute
// on the right side. otherwise, we would do (word) { print('hey!'); print(word); }
words.forEach((word) => print(word));

// 3rd way
// very similar to the 2nd way but a different syntax
for (String word in words) {
  print(word);
}
```
### Classes, Objects, and Constructors

Classes are essentially blueprints, or templates, for creating your own data type in your programs. For example, if you wanted to write programs about cars, it would be very difficult to do so using the primitive data types of String, int, bool, etc. 

Using classes, we can create our own data types or models by defining a class, and its attributes. These attributes are of primitive data types, but the resulting class allows us to write more complex code in a simpler manner.

When we need to create a specific instance of a class (i.e. we want to use the blueprint to actually create a car), we 'instantiate' it with the attributes we want, and the result is called an Object. 

An object is simply a specific instance of a class - the class would be 'Car', and the object would be something like a Tesla Model S. Another object you might create would be a Lamborghini Aventador. You can create as many objects as you want using the same class!

Classes can be created and used like this. Notice how the type of the object that is instantiated is declared, and how the object is instantiated.

```dart
class Car {
  String name;
  int price;
  bool isMadeByElonMusk;
}

void main() {
  // type 'Car'
  Car tesla = Car(); // class is instantiated with parentheses, ()
  // populating each of the attributes we defined in the above class
  tesla.name = 'Model S';
  tesla.price = 50000;
  tesla.isMadeByElonMusk = true;
}
```

Now, it would be very tedious and inefficient to manually set all the attributes of an object after we've created one. Doing tesla.name, tesla.price, ..., isn't good enough for us.

That's where constructors come in. Constructors allow us to define a function in our class that will deal with setting all the attributes for us. Then, to instantiate a class, all we have to do is pass in the parameters. See the example below.

Another important concept relating to classes is methods.

Methods are functions defined in our class, that deal with data and perform special operations relating to our class. For example, we might want to check whether or not our car is expensive. We can do so by defining an 'isExpensive()' method inside our class. 

Note that methods defined within a certain class have access to the attributes associated with the object it was called upon. If the 'isExpensive()' method is called upon our tesla object, it has access to the tesla.price value.

```dart
// define a class named car
class Car {
  // define a constructor that takes in a String name, int price and bool isMadeByElonMusk
  Car(String name, int price, bool isMadeByElonMusk) {
    // set all the object's attributes equal to the inputs passed in
    this.name = name;
    this.price = price;
    this.isMadeByElonMusk = isMadeByElonMusk;
  }
  // defining the attributes of the class
  String name;
  int price;
  bool isMadeByElonMusk;
  
  // defining the method 'isExpensive' that returns type bool
  bool isExpensive() {
    // 'this.price' refers specifically to the price value of the object it was called upon
    if (this.price > 30000) {
      return true;
    } else {
      return false;
    }
  }
}

void main() {
  // instantiate the class by using its constructor, passing in the expected parameters
  // we defined already
  Car tesla = Car('Model S', 50000, true);
  // returns true by using the Car class's method, isExpensive, because tesla.price = 50,000
  bool isCarExpensive = tesla.isExpensive();
}
```

    
### More Dart Resources

- [Dart Docs - Dart Cheatsheet](https://dart.dev/codelabs/dart-cheatsheet)
- [Dart Programing Tutorial - Full Course](https://youtu.be/Ej_Pcr4uC2Q)
- [Dart Tutorials](https://dart.dev/tutorials)

# Widgets

[Introduction of Widgets](https://docs.flutter.dev/development/ui/widgets-intro)

Flutter apps are built using things called Widgets. If you are familiar with a frontend javascript framework, these are akin to components, but many come already built by the framework. Widgets are also quite similar to HTML elements like 'p' (for paragraph), 'h1' (for header 1), etc.

Widgets are essentially the basic elements or building blocks of an app that Flutter has created for us. They are instantiated with specific properties or parameters that Flutter is expecting from you. For example, to display text on the app screen, we use a widget called the Text widget, comparable to the html 'p' element, that is instantiated by passing in a string. Here's what it looks like, in code and on an app.

```flutter
// displays the text on the app screen
Text('Some string here');
```
![text_widget](text_widget.png)

There's also a prebuilt button widget from the Flutter library called the ElevatedButton (just a Material theme button) which takes in an onPressed property (the code to be executed after the button is pressed) and a child property (the Text widget that displays the text of the button). Another one is the TextField, which handles input text.
