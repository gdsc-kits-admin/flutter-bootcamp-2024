# App Drawer widget
## Today we will add a drawer widget in our flutter app

### Drawer widget in Flutter
Drawer widget is used to provide access to different destinations and functionalities provided in your application. It is represented by three horizontal parallel lines on the upper end of the scaffold.  It has a horizontal movement from the edge of the Scaffold that navigates the link to different routes in the flutter app.

## Let's Start

### 1. Imports and main function
```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}
```

### 2. MyApp class
```
class MyApp extends StatelessWidget {
  final appTitle = 'Flutter Drawer Demo';

  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: appTitle,
      home: MyHomePage(title: appTitle),
    ); // MaterialApp
  }
}
```

### 3. MyHomePage Class

The MyHomePage class is a StatelessWidget that returns a Scaffold widget. The Scaffold widget is a layout widget that provides a number of features such as an app bar, body, and drawer.

The appBar property sets the app bar of the page to a AppBar widget with a green background and the title of the app. The body property sets the body of the page to a Center widget with a Text widget that displays the message "A drawer is an invisible side screen."

The drawer property sets the drawer of the page to a Drawer widget with a child ListView widget. The ListView widget contains a number of ListTile widgets that display icons and text, and are used to navigate to different pages.

```

class MyHomePage extends StatelessWidget {
  final String title;
 
  const MyHomePage({Key? key, required this.title}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
        backgroundColor: Colors.green,
      ),
      body: const Center(
          child: Text(
        'A drawer is an invisible side screen.',
        style: TextStyle(fontSize: 20.0),
      )),
      drawer: Drawer(
        child: ListView(
          padding: const EdgeInsets.all(0),
          children: [
            const DrawerHeader(
              decoration: BoxDecoration(
                color: Colors.green,
              ), //BoxDecoration
              child: UserAccountsDrawerHeader(
                decoration: BoxDecoration(color: Colors.green),
                accountName: Text(
                  "Cyril Jacob",
                  style: TextStyle(fontSize: 18),
                ),
                accountEmail: Text("cyriljacob@karunya.edu.in"),
                currentAccountPictureSize: Size.square(50),
                currentAccountPicture: CircleAvatar(
                  backgroundColor: Color.fromARGB(255, 165, 255, 137),
                  child: Text(
                    "C",
                    style: TextStyle(fontSize: 30.0, color: Colors.blue),
                  ), //Text
                ), //circleAvatar
              ), //UserAccountDrawerHeader
            ), //DrawerHeader
            ListTile(
              leading: const Icon(Icons.person),
              title: const Text(' My Profile '),
              onTap: () {
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.book),
              title: const Text(' My Course '),
              onTap: () {
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.workspace_premium),
              title: const Text(' Go Premium '),
              onTap: () {
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.video_label),
              title: const Text(' Saved Videos '),
              onTap: () {
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.edit),
              title: const Text(' Edit Profile '),
              onTap: () {
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.logout),
              title: const Text('LogOut'),
              onTap: () {
                Navigator.pop(context);
              },
            ),
          ],
        ),
      ), //Drawer
    );
  }
}
```

### Output
![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/131938772/85c19ab1-dcf3-4bd7-94fc-17562f9bbc2e)

![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/131938772/dd4f34af-64ce-44dc-ad2c-cb3bfba20901)

