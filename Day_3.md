# Signin and Signup using Email + Authendication using Firebase 

## Step 1
  - ### Open Firebase Console

      https://console.firebase.google.com/
    
    if your not signedin already signup using your kmail

  - ### Add Project
    
      1) Give **Project Name** and click next
      2) **Disable** the Google Analytics for this Project
      3) Click **Create Project** Button to create your Project
   

## Now get Started with Firebase Authentication on Flutter

  - ###  First Install Firebase CLI
  
    **For Windows** - https://firebase.tools/bin/win/instant/latest
  
    **For Mac** - https://firebase.tools/bin/macos/latest
  
    **For Linux** - https://firebase.tools/bin/linux/latest

##  Add Firebase to your Flutter app

  **Official Doc Link**

  https://firebase.google.com/docs/flutter/setup

  ### STEP 1: Install the required command line tools
  
  - If you haven't already, install the Firebase CLI.
  - Log into Firebase using your Google account by running the following command:

  ```
  firebase login
  ```
  - Install the FlutterFire CLI by running the following command from any directory:

  ```
  dart pub global activate flutterfire_cli
  ```

  ## You should have to setup the the flutter fire bin path in your environment 

  Update the PATH Environment Variable:

   - Locate the directory where the 'flutterfire' executable is installed. In your case, it seems to be `C:\Users\bharath kumar\AppData\Local\Pub\Cache\bin.` Follow the instructions for your specific version of Windows to `update the PATH environment variable.` You can search online for `"configure windows path"` for detailed instructions.
 
   - Add the directory containing the 'flutterfire' executable `(C:\Users\bharath kumar\AppData\Local\Pub\Cache\bin)` to the PATH environment variable. Use the Full Path to Execute the Command:

  - Instead of relying on the PATH variable, you can execute the 'flutterfire' command by providing the full path to the executable. For example: makefile

**Copy code**

 ```
 C:\Users\bharath kumar\AppData\Local\Pub\Cache\bin\flutterfire configure
 ```
**Verify Flutterfire Installation:**

  - Double-check that Flutterfire is correctly installed by running pub global activate flutterfire again. Make sure there are no errors during the installation process.
After performing one of these actions, try running the `'flutterfire'` command again in your command prompt to see if the issue is resolved.



  ### Step 2: Configure your apps to use Firebase

  Use the FlutterFire CLI to configure your Flutter apps to connect to Firebase.

  From your Flutter project directory, run the following command to start the app configuration workflow:

  ```
  flutterfire configure
  ```

  ### Step 3: Initialize Firebase in your app

  From your Flutter project directory, run the following command to install the core plugin:

  ```
  flutter pub add firebase_core
  ```

  ```
  flutter pub add firebase_auth
  ```

   ```
  flutterfire configure
  ```


  # SOURCE CODE 

  ## main.dart

  ```
import 'package:flutter/material.dart';
import 'package:modernlogintute/pages/auth_page.dart';
import 'package:firebase_core/firebase_core.dart';
import 'firebase_options.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: AuthPage(),
    );
  }
}
```

# Pages 

  - **auth_page.dart**
  - **home_page.dart**
  - **login_or_register_page.dart**
  - **login_page.dart**
  - **register_page.dart**

## auth_page.dart

```
import 'package:firebase_auth/firebase_auth.dart';
import 'package:flutter/material.dart';
import 'package:modernlogintute/pages/login_or_register_page.dart';
import 'package:modernlogintute/pages/login_page.dart';
import 'home_page.dart';

class AuthPage extends StatelessWidget {
  const AuthPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: StreamBuilder<User?>(
        stream: FirebaseAuth.instance.authStateChanges(),
        builder: (context, snapshot) {
          // user is logged in
          if (snapshot.hasData) {
            return HomePage();
          }

          // user is NOT logged in
          else {
            return LoginOrRegisterPage();
          }
        },
      ),
    );
  }
}

```
## home_page.dart

```
import 'package:firebase_auth/firebase_auth.dart';
import 'package:flutter/material.dart';
import 'package:modernlogintute/pages/login_or_register_page.dart';
import 'package:modernlogintute/pages/login_page.dart';
import 'home_page.dart';

class AuthPage extends StatelessWidget {
  const AuthPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: StreamBuilder<User?>(
        stream: FirebaseAuth.instance.authStateChanges(),
        builder: (context, snapshot) {
          // user is logged in
          if (snapshot.hasData) {
            return HomePage();
          }

          // user is NOT logged in
          else {
            return LoginOrRegisterPage();
          }
        },
      ),
    );
  }
}

```

## login_or_register_page.dart

```
import 'package:flutter/material.dart';
import 'package:modernlogintute/pages/login_page.dart';
import 'package:modernlogintute/pages/register_page.dart';

class LoginOrRegisterPage extends StatefulWidget {
  const LoginOrRegisterPage({super.key});

  State<LoginOrRegisterPage> createState() => _LoginOrRegisterPageState();
}

class _LoginOrRegisterPageState extends State<LoginOrRegisterPage> {
  // initially show login page
  bool showLoginPage = true;

  // toggle between login and register page
  void togglePages() {
    setState(() {
      showLoginPage = !showLoginPage;
    });
  }

  Widget build(BuildContext context) {
    if (showLoginPage) {
      return LoginPage(
        onTap: togglePages,
      );
    } else {
      return RegisterPage(
        onTap: togglePages,
      );
    }
  }
}

```

## login_page.dart

```
import 'package:flutter/material.dart';
import 'package:modernlogintute/pages/login_page.dart';
import 'package:modernlogintute/pages/register_page.dart';

class LoginOrRegisterPage extends StatefulWidget {
  const LoginOrRegisterPage({super.key});

  State<LoginOrRegisterPage> createState() => _LoginOrRegisterPageState();
}

class _LoginOrRegisterPageState extends State<LoginOrRegisterPage> {
  // initially show login page
  bool showLoginPage = true;

  // toggle between login and register page
  void togglePages() {
    setState(() {
      showLoginPage = !showLoginPage;
    });
  }

  Widget build(BuildContext context) {
    if (showLoginPage) {
      return LoginPage(
        onTap: togglePages,
      );
    } else {
      return RegisterPage(
        onTap: togglePages,
      );
    }
  }
}

```

## register_page.dart

```
import 'dart:ui';

import 'package:firebase_auth/firebase_auth.dart';
import 'package:flutter/material.dart';
import 'package:modernlogintute/components/my_button.dart';
import 'package:modernlogintute/components/my_textfield.dart';
import 'package:modernlogintute/components/square_tile.dart';

class RegisterPage extends StatefulWidget {
  final Function()? onTap;
  RegisterPage({super.key, required this.onTap});

  @override
  State<RegisterPage> createState() => _RegisterPageState();
}

class _RegisterPageState extends State<RegisterPage> {
  // text editing controllers
  final emailController = TextEditingController();
  final passwordController = TextEditingController();
  final confirmpasswordController = TextEditingController();
  // sign user in method
  void signUserUp() async {
    // show loading circle
    showDialog(
      context: context,
      builder: (context) {
        return const Center(
          child: CircularProgressIndicator(),
        );
      },
    );

    // try sign in
    try {
      // check password
      if (passwordController.text == confirmpasswordController.text) {
        await FirebaseAuth.instance.createUserWithEmailAndPassword(
          email: emailController.text,
          password: passwordController.text,
        );
      } else {
        // error msg
        showErrorMessage("Password Not Match");
      }

      // pop the loading circle
      Navigator.pop(context);
    } on FirebaseAuthException catch (e) {
      // pop the loading circle
      Navigator.pop(context);
      // show error code
      showErrorMessage(e.code);
    }
  }

  // error message to user
  void showErrorMessage(String message) {
    showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          backgroundColor: Colors.deepPurple,
          title: Center(
            child: Text(
              message,
              style: const TextStyle(color: Colors.white),
            ),
          ),
        );
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.grey[300],
      body: SafeArea(
        child: Center(
          child: SingleChildScrollView(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                const SizedBox(height: 25),

                // logo
                const Icon(
                  Icons.lock,
                  size: 50,
                ),

                const SizedBox(height: 25),

                // welcome back, you've been missed!
                Text(
                  'Lets Create Your  Account',
                  style: TextStyle(
                    color: Colors.grey[700],
                    fontSize: 16,
                  ),
                ),

                const SizedBox(height: 25),

                // email textfield
                MyTextField(
                  controller: emailController,
                  hintText: 'Email',
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

                // Confirm password textfield
                MyTextField(
                  controller: confirmpasswordController,
                  hintText: ' Confirm Password',
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
                  text: "Sign Up",
                  onTap: signUserUp,
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
                      'Already have an account',
                      style: TextStyle(color: Colors.grey[700]),
                    ),
                    const SizedBox(width: 4),
                    GestureDetector(
                      onTap: widget.onTap,
                      child: const Text(
                        'Login now',
                        style: TextStyle(
                          color: Colors.blue,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                    ),
                  ],
                )
              ],
            ),
          ),
        ),
      ),
    );
  }
}

```

# components 

  - **my_button.dart**
  - **my_textfield.dart**
  - **square_tile.dart**
    

## my_button.dart

```
import 'package:flutter/material.dart';

class MyButton extends StatelessWidget {
  final Function()? onTap;
  final String text;

  const MyButton({super.key, required this.onTap, required this.text});

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: onTap,
      child: Container(
        padding: const EdgeInsets.all(25),
        margin: const EdgeInsets.symmetric(horizontal: 25),
        decoration: BoxDecoration(
          color: Colors.black,
          borderRadius: BorderRadius.circular(8),
        ),
        child: Center(
          child: Text(
            text,
            style: const TextStyle(
              color: Colors.white,
              fontWeight: FontWeight.bold,
              fontSize: 16,
            ),
          ),
        ),
      ),
    );
  }
}

```

## my_textfield.dart

```
import 'package:flutter/material.dart';

class MyTextField extends StatelessWidget {
  final controller;
  final String hintText;
  final bool obscureText;

  const MyTextField({
    super.key,
    required this.controller,
    required this.hintText,
    required this.obscureText,
  });

  @override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.symmetric(horizontal: 25.0),
      child: TextField(
        controller: controller,
        obscureText: obscureText,
        decoration: InputDecoration(
            enabledBorder: const OutlineInputBorder(
              borderSide: BorderSide(color: Colors.white),
            ),
            focusedBorder: OutlineInputBorder(
              borderSide: BorderSide(color: Colors.grey.shade400),
            ),
            fillColor: Colors.grey.shade200,
            filled: true,
            hintText: hintText,
            hintStyle: TextStyle(color: Colors.grey[500])),
      ),
    );
  }
}

```

## square_tile.dart

```
import 'package:flutter/material.dart';

class SquareTile extends StatelessWidget {
  final String imagePath;
  const SquareTile({
    super.key,
    required this.imagePath,
  });

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.all(20),
      decoration: BoxDecoration(
        border: Border.all(color: Colors.white),
        borderRadius: BorderRadius.circular(16),
        color: Colors.grey[200],
      ),
      child: Image.asset(
        imagePath,
        height: 40,
      ),
    );
  }
}

```

  ## images

  images are available in the repo folder name called images 


  # Output 

  ### Authentication

  ![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/116173614/46e4e636-e031-450a-9dcd-0f4e463913de)


 ### Sign in and Sign up 

 
![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/116173614/3d8573ec-1e5a-4534-be92-48dd9088efd3)


![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/116173614/3dd52fa6-f85b-4118-9c1e-5f8f01b455a5)


![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/116173614/842760a9-4a6e-467f-b730-db2db4cade6d)


![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/116173614/a1e18360-b129-4fca-b3a8-643aa3d9a804)




  
  
  
  




    

