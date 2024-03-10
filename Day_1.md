
# Simple Flutter Application with Material Design Theme

### First create Yor Flutter Workspace using Cmd
Search cmd in your search bar and choose your path you want ex.. Downloads or Desktop
```
cd
```
Now Run this Commsnd in your cmd to create a flutter Workspace 
```
flutter create first_flutter_learn
```
Now all set correctly we are ready to start 

## This is a simple Flutter application that creates a basic user interface (UI) with a Material Design theme. Let's break it down:

### Import Statements
```dart
import 'package:flutter/material.dart';
```
This imports the Flutter framework's material package which contains widgets implementing Material Design.

### Main Function
```
void main() {
  runApp(const MyApp());
}
```
The main() function is the entry point of the application. It calls runApp() with an instance of MyApp. MyApp is a Flutter widget that represents the whole application.

### MyApp Class
```
class MyApp extends StatelessWidget {

```
This class extends StatelessWidget, indicating that the widget is immutable and its state cannot change once it's built.

```
const MyApp({super.key});
```
The constructor of MyApp doesn't do much except calling the super constructor with an optional named parameter.

```
Widget build(BuildContext context) {
```
The build method is overridden here to describe the UI of the widget.

### MaterialApp Widget

```
MaterialApp(
  debugShowCheckedModeBanner: false,
  home: Scaffold(
    ...
  ),
)
```
MaterialApp is the root widget of the application. It configures the top-level Navigator and manages the theme and navigation of the app. Inside it, a Scaffold widget is used which provides a framework for implementing the basic material design layout structure.

### Scaffold Widget
```
Scaffold(
  appBar: AppBar(
    ...
  ),
  body: Center(
    ...
  ),
  bottomNavigationBar: BottomNavigationBar(
    ...
  ),
)
```
Scaffold provides several properties like appBar, body, and bottomNavigationBar to define the basic structure of the app's layout.

### AppBar Widget
```
AppBar(
  backgroundColor: const Color.fromARGB(255, 0, 255, 247),
  title: const Text('First Flutter'),
)
```
The AppBar widget represents the app bar at the top of the screen. It contains a title and can also contain other widgets like icons and action buttons.

### Center Widget
```
Center(
  child: ElevatedButton(
    ...
  ),
)
```
The Center widget is used to center its child widget in both axes. Here, it contains an ElevatedButton widget.

### ElevatedButton Widget
```
ElevatedButton(
  onPressed: () {},
  style: ButtonStyle(
    backgroundColor: MaterialStateProperty.all<Color>(Colors.blue),
  ),
  child: const Text('click'),
)
```
ElevatedButton is a button with a filled background. It has an onPressed callback, a style property to define the appearance, and a child widget which is a Text widget displaying 'click'.

### BottomNavigationBar Widget
```
BottomNavigationBar(
  items: const [
    BottomNavigationBarItem(label: 'Home', icon: Icon(Icons.home)),
    BottomNavigationBarItem(label: 'Settings', icon: Icon(Icons.settings)),
  ],
)
```
BottomNavigationBar is a widget that displays a horizontal row of tabs at the bottom of the screen. It contains multiple BottomNavigationBarItem widgets, each representing a tab. In this case, there are two tabs: 'Home' and 'Settings', each with an icon and a label.

## main.dart
Copy this whole code and use 
```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          backgroundColor: const Color.fromARGB(255, 0, 255, 247),
          title: const Text('First Flutter'),
        ),
        body: Center(
          child: ElevatedButton(
            onPressed: () {},
            style: ButtonStyle(
              backgroundColor: MaterialStateProperty.all<Color>(Colors.blue),
            ),
            child: const Text('click'),
          ),
        ),
        bottomNavigationBar: BottomNavigationBar(
          items: const [
            BottomNavigationBarItem(label: 'Home', icon: Icon(Icons.home)),
            BottomNavigationBarItem(
              label: 'Settings',
              icon: Icon(Icons.settings),
            )
          ],
        ),
      ),
    );
  }
}
```
### Output

![Screenshot 2024-03-10 153123](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/116173614/346b71ae-ef89-469e-b82a-12d29413b436)


### Link

**Documentation**

https://docs.flutter.dev/

**Youtube**

https://youtu.be/CD1Y2DmL5JM?si=KAsYVBZHXL3V1hJ0
