# Flutter

# Introduction
Flutter is a powerful and intuitive framework for building beautiful, cross-platform mobile applications that uses the Dart programming language.

This essentially means that Flutter can be used to write one codebase for an app that runs natively on both iOS and Android.

With all the hype around Flutter and mobile app development, learning Flutter is both a valuable skill and a gratifying endeavor in its own right. However, the path to learning Flutter is a little unclear due to how new the language is.
- the language is constantly being updated (to the point where tutorials from just a few months ago are out of date)
- there are a lack of freely available, well thought out and comprehensive courses or books compared to some other more established frameworks and languages like python

This guide compiles tutorials, tips, examples (with screenshots), resources, and even an example project to help make the learning process for Flutter much easier. You can be a complete beginner, an intermediate or even advanced programmer to use this guide. I hope you find it helpful!

Note: See the 'code' folder in this repository for all of the code within this guide.

[What makes Flutter different for app development?](https://www.youtube.com/watch?v=l-YO9CmaSUM)
# Setting Up for Flutter Development
* [Getting Started: Installing Flutter](https://docs.flutter.dev/get-started/install)
* [Git for Windows](https://git-scm.com/downloads)
* [Install Android Studio](https://developer.android.com/studio)\

Once finished, run this command in the terminal to make sure your environment is all ready to go.
```flutter
$ flutter doctor
```
# Dart Language
## Hello World
Every app has a `main()` function. To display text on the console, you can use the top-level `print()` function:
```dart
void main() {
  print('Hello, World!');
}
```
## Variables
Even in type-safe Dart code, most variables don’t need explicit types, thanks to type inference:
```dart
var name = 'Voyager I';
var year = 1977;
var antennaDiameter = 3.7;
var flybyObjects = ['Jupiter', 'Saturn', 'Uranus', 'Neptune'];
var image = {
  'tags': ['saturn'],
  'url': '//path/to/saturn.jpg'
};
```
## Control flow statements
Dart supports the usual control flow statements:
```dart
if (year >= 2001) {
  print('21st century');
} else if (year >= 1901) {
  print('20th century');
}

for (final object in flybyObjects) {
  print(object);
}

for (int month = 1; month <= 12; month++) {
  print(month);
}

while (year < 2016) {
  year += 1;
}
```
## Functions
We recommend specifying the types of each function’s arguments and return value:
```dart
int fibonacci(int n) {
  if (n == 0 || n == 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

var result = fibonacci(20);
```

# Widgets
Flutter apps are built using things called Widgets. If you are familiar with a frontend javascript framework, these are akin to components, but many come already built by the framework. Widgets are also quite similar to HTML elements like 'p' (for paragraph), 'h1' (for header 1), etc.

Widgets are essentially the basic elements or building blocks of an app that Flutter has created for us. They are instantiated with specific properties or parameters that Flutter is expecting from you. For example, to display text on the app screen, we use a widget called the Text widget, comparable to the html 'p' element, that is instantiated by passing in a string. Here's what it looks like, in code and on an app.
```flutter
// displays the text on the app screen
Text('Some string here');
```
![text_widget](text_widget.png)

There's also a prebuilt button widget from the Flutter library called the ElevatedButton (just a Material theme button) which takes in an onPressed property (the code to be executed after the button is pressed) and a child property (the Text widget that displays the text of the button). Another one is the TextField, which handles input text.
