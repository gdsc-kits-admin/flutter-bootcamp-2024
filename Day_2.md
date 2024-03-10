# Login Page Documentation
## Today we are going to create a simple sign in page 

### MaterialApp Widget:

```MaterialApp(
  debugShowCheckedModeBanner: false,
  home: LoginPage(),
)
```

The MaterialApp widget is the root widget of the application. It configures the top-level Navigator and manages the theme and navigation of the app. Here, we set debugShowCheckedModeBanner to false to hide the debug banner in the app. The home property is set to LoginPage(), which means that the initial route of the application is the LoginPag

### Overview
The `LoginPage` class represents the UI for user login. It contains text fields for username and password input, a button to sign in, options to reset password or register, and buttons to sign in with Google or Apple accounts.

### Import Statements

```dart
import 'package:flutter/material.dart';
import 'package:modernlogintute/components/my_button.dart';
import 'package:modernlogintute/components/my_textfield.dart';
import 'package:modernlogintute/components/square_tile.dart';
```

### Methods

`signUserIn():` Method to sign the user in. (Currently empty)

### Widgets Used

`Scaffold:` Provides the basic structure for the page.

`SafeArea:` Ensures that the content is displayed within safe areas of the screen.

`Column:` Arranges widgets vertically.

`Image.asset:` Displays an image from the assets folder.

`Text:` Displays text.

`MyTextField:` Custom text field widget for username and password input.

`MyButton:` Custom button widget for signing in.

`SquareTile:` Custom widget for square tiles.

`Divider:` Divides content with a horizontal line.

# SOURCE CODE

## main.dart 
```
import 'package:flutter/material.dart';
import 'pages/login_page.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: LoginPage(),
    );
  }
}
```

## login_page.dart
```
import 'package:flutter/material.dart';
import 'package:modernlogintute/components/my_button.dart';
import 'package:modernlogintute/components/my_textfield.dart';
import 'package:modernlogintute/components/square_tile.dart';

class LoginPage extends StatelessWidget {
  LoginPage({super.key});

  // text editing controllers
  final usernameController = TextEditingController();
  final passwordController = TextEditingController();

  // sign user in method
  void signUserIn() {}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.grey[300],
      body: SafeArea(
        child: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              const SizedBox(height: 10),

              // logo
              Image.asset(
                'lib/images/lock.png',
                width: 150,
                height: 150,
              ),
              const SizedBox(height: 50),

              // welcome back, you've been missed!
              Text(
                'Welcome back you\'ve been missed!',
                style: TextStyle(
                  color: Colors.grey[700],
                  fontSize: 16,
                ),
              ),

              const SizedBox(height: 25),

              // username textfield
              MyTextField(
                controller: usernameController,
                hintText: 'Username',
                obscureText: false,
              ),

              const SizedBox(height: 10),

              // password textfield
              MyTextField(
                controller: passwordController,
                hintText: 'Password',
                obscureText: true,
              ),

              const SizedBox(height: 10),

              // forgot password?
              Padding(
                padding: const EdgeInsets.symmetric(horizontal: 25.0),
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.end,
                  children: [
                    Text(
                      'Forgot Password?',
                      style: TextStyle(color: Colors.grey[600]),
                    ),
                  ],
                ),
              ),

              const SizedBox(height: 25),

              // sign in button
              MyButton(
                onTap: signUserIn,
              ),

              const SizedBox(height: 50),

              // or continue with
              Padding(
                padding: const EdgeInsets.symmetric(horizontal: 25.0),
                child: Row(
                  children: [
                    Expanded(
                      child: Divider(
                        thickness: 0.5,
                        color: Colors.grey[400],
                      ),
                    ),
                    Padding(
                      padding: const EdgeInsets.symmetric(horizontal: 10.0),
                      child: Text(
                        'Or continue with',
                        style: TextStyle(color: Colors.grey[700]),
                      ),
                    ),
                    Expanded(
                      child: Divider(
                        thickness: 0.5,
                        color: Colors.grey[400],
                      ),
                    ),
                  ],
                ),
              ),

              const SizedBox(height: 50),

              // google + apple sign in buttons
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: const [
                  // google button
                  SquareTile(imagePath: 'lib/images/google.png'),

                  SizedBox(width: 25),

                  // apple button
                  SquareTile(imagePath: 'lib/images/apple.png')
                ],
              ),

              const SizedBox(height: 50),

              // not a member? register now
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Text(
                    'Not a member?',
                    style: TextStyle(color: Colors.grey[700]),
                  ),
                  const SizedBox(width: 4),
                  const Text(
                    'Register now',
                    style: TextStyle(
                      color: Colors.blue,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                ],
              )
            ],
          ),
        ),
      ),
    );
  }
}
```

### Output

![image](https://github.com/Bharathlax-2005/Flutter-Learn-Bootcamp/assets/116173614/74ec9e6e-3f18-4846-b772-25e4ecd94835)

### Link

**Documentation**

https://docs.flutter.dev/ui/widgets

***Youtube***

https://youtu.be/Dh-cTQJgM-Q?si=fXFat30jnVTgYoNL



