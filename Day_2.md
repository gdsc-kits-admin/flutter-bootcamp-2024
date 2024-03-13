# Multi-page apps in Flutter
## Today we are going to create a multi-page app in Flutter

### What is a page in flutter?
A page is a single screen that is visible at a point in time. A single page or screen can be made up of numerous widgets organized together to create the desired UI. Pages/screens in Flutter are known as Routes, and we use the Navigator widget to navigate between them.
In Flutter, everything — including multi-page applications — are widgets. Flutter uses convenient widgets (like MaterialApp) that display different screens depending on the user’s navigation and preferences

### How do you navigate pages?
The Navigator widget comes bundled with MaterialApp and manages a stack of Route objects. You can think of a route object as a representation of a single page or screen. The route at the top of this stack is visible to the user, and when the user pushes the back button, the uppermost route pops out, revealing the route below it, just like a stack of cards.

### Let's start
Let’s start by creating a MaterialApp widget that will configure the top-level Navigator along with other basic things for our app:
```
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Naviation Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const FirstPage(title: 'FirstPage'),
    );
  }
}
```

Since our app has multiple pages, we’re going to create two pages/screens called FirstPage and SecondPage.

Below is the FirstPage widget, which consists of a Scaffold with an AppBar displaying the page/screen title and a body displaying a button to navigate to the SecondPage:
```

class FirstPage extends StatelessWidget {
  const FirstPage({Key? key, required this.title}) : super(key: key);
  final String title;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
      ),
      body: Center(
        child: TextButton(
          onPressed: () {},
          child: const Text('Next'),
        ),
      ),
    );
  }
}
```

Now this is what our first page currently looks like:
<br>
![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/131938772/c06e799a-995a-406e-a5de-ddc5ea81e510)

### Navigate to Second Page
If you try to tap on the Next button, nothing will happen because we haven’t told Flutter yet what to do when the user taps on the button.
Use the Navigator.push() method to switch to a new route. The Navigator’s push() method adds a Route to the stack of routes it manages.
In order to navigate to SecondPage, first we need to create it. SecondPage will be almost identical to the FirstPage with the text now changing to Go Back:

```
class SecondPage extends StatelessWidget {
  const SecondPage({Key? key, required this.title}) : super(key: key);
  final String title;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
      ),
      body: Center(
        child: TextButton(
          onPressed: () {},
          child: const Text('Go Back'),
        ),
      ),
    );
  }
}
```

Now that our SecondPage is built, we can navigate to it by updating the onPressed() method in FirstPage. Replace theonPressed() in the TextButton of the FirstPage with the following code:
```
onPressed: () {
   Navigator.push(context, MaterialPageRoute(builder: (context) {
     return const SecondPage(title: 'SecondPage');
   }));
}
```

Most of the time we use MaterialPageRoute to navigate between pages/screens, but at times when we want more control to add things like custom transitions, then we can use PageRouteBuilder.

### Going back to the First Page.
You’ve successfully created your first multi-page app in Flutter. Now it’s time for you to navigate back to the FirstPage.
To navigate back, we use the Navigator.pop() method. It removes the current Route from the Navigator’s stack of routes.

In the SecondPage, replace onPressed() with the below code:
```
onPressed: () {
  Navigator.pop(context);
}
```

### Final Code - main.dart
```
import 'package:flutter/material.dart';
import 'package:flutter/widgets.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Naviation Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const FirstPage(title: 'FirstPage'),
    );
  }
}

class FirstPage extends StatelessWidget {
  const FirstPage({Key? key, required this.title}) : super(key: key);
  final String title;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
      ),
      body: Center(
        child: TextButton(
          onPressed: () {
            Navigator.push(context, MaterialPageRoute(builder: (context) {
              return const SecondPage(title: 'SecondPage');
   }));
},
          child: const Text('Next'),
        ),
      ),
    );
  }
}

class SecondPage extends StatelessWidget {
  const SecondPage({Key? key, required this.title}) : super(key: key);
  final String title;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
      ),
      body: Center(
        child: TextButton(
          onPressed: () {
            Navigator.pop(context);
            },
          child: const Text('Go Back'),
        ),
      ),
    );
  }
}
```



