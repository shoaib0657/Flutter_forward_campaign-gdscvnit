# Flutter

# Introduction
Flutter is a powerful and intuitive framework for building beautiful, cross-platform mobile applications that uses the Dart programming language.
# Setting Up for Flutter Development
* Getting Started: Installing Flutter
* Git for Windows
* Install Android Studio\
\
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

# Widgets
Flutter apps are built using things called Widgets. If you are familiar with a frontend javascript framework, these are akin to components, but many come already built by the framework. Widgets are also quite similar to HTML elements like 'p' (for paragraph), 'h1' (for header 1), etc.

Widgets are essentially the basic elements or building blocks of an app that Flutter has created for us. They are instantiated with specific properties or parameters that Flutter is expecting from you. For example, to display text on the app screen, we use a widget called the Text widget, comparable to the html 'p' element, that is instantiated by passing in a string. Here's what it looks like, in code and on an app.
```flutter
// displays the text on the app screen
Text('Some string here');
```
![text_widget](text_widget.png)
