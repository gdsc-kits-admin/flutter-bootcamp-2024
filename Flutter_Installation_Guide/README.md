# Install Flutter SDK:

Download the Flutter SDK from the official Flutter website (): Flutter SDK.
Extract the downloaded ZIP file to a location on your PC (e.g., C:\src\flutter).
Set Up Flutter Environment Variables:

## Add the Flutter bin directory to your **system's PATH environment variable**:

1) Open Control Panel > System and Security > System.
2) Click on "Advanced system settings" on the left sidebar.
3) Click on the "Environment Variables" button.
4) Under "System variables," select the "Path" variable and click "Edit."
5) Click "New" and add the path to the Flutter bin directory (e.g., C:\src\flutter\bin).
6) Click "OK" to save the changes.


## Install Flutter and Dart Plugins for VS Code:

Install the Flutter and Dart plugins from the Visual Studio Code Marketplace.
Create a Flutter Project:

### Open a terminal window.
Run the following command to verify everything is perfectly Setup or not

```
   flutter doctor
```

### Error while running code -- if your already having vs / old version or without c++ workload 
```
Visual Studio - develop Windows apps (Visual Studio Build     
    Tools 2022 17.7.6)
    X Visual Studio is missing necessary components. Please re-run
      the Visual Studio installer for the "Desktop development    
      with C++" workload, and include these components:
        MSVC v142 - VS 2019 C++ x64/x86 build tools
         - If there are multiple build tool versions available,   
         install the latest
        C++ CMake tools for Windows
        Windows 10 SDK
```

# Not having Visual Studio 2022 -- Installer download it &  it is not vs code 

![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/116173614/44a3eb41-9e66-4845-a2b2-51cd34c22510)


## Download using this link directly --- https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&channel=Release&version=VS2022&source=VSLandingPage&cid=3600&passive=false

or download by search vs 2022 installer in your browser and download the community version 
        
## Your doing for the first time or follow this steps to fix your errors 

**1) Open Visual Studio 2022 Installer:**

- Press the "Windows" key on your keyboard or click on the Windows icon in the taskbar to open the Start menu.
- Type "Visual Studio Installer" in the search bar and press "Enter" to launch the application.

**2) Modify Installation:**

- In the Visual Studio Installer window, you should see a list of installed Visual Studio versions (e.g., Visual Studio 2022). Find the version you are using and click on it.
- If you don't see your installed version, make sure you've opened the correct installer for the version of Visual Studio you have.

**3) Select Workloads:**

- After selecting your Visual Studio version, you'll see several tabs at the top of the window. Click on the "Modify" button next to your installed version.
- This will take you to the "Workloads" tab, where you'll see a list of available workloads.
Choose "Desktop development with C++" 

**4)Workload:**

- Scroll through the list of workloads and make sure that the "Desktop development with C++" workload is selected.
If it's not already selected, click the checkbox next to it to select it.

**5)Select Individual Components:**
- Next, click on the "Individual Components" tab at the top of the window.
This tab allows you to select specific components to install or modify.

**6)Check Necessary Components:**
-Look for the following components in the list:

   - **MSVC v142 - VS 2019 C++ x64/x86 build tools**

   - **C++ CMake tools for Windows**

   - **Windows 10 SDK**
        - If your having windows 11 select latest version of 11 and 10
        - If your having windows 10 select only latest version of 10 only 

If any of these components are not selected, click the checkbox next to them to select them.

**7)Install Updates:**

- If there are multiple versions available for any of the components, ensure you select the latest version.
Visual Studio installer automatically selects the latest version by default.

**8)Install/Modify:**
    
- Once you've verified that the necessary components are selected, click on the "Modify" button at the bottom right corner of the window.

**9)Wait for Installation:**

- The installer will now download and install the selected components. The progress bar will indicate the installation progress.
Depending on your internet speed and the size of the components, this process may take some time.

**10)Restart if Required:**

- After the installation is complete, you may be prompted to restart your computer. If so, follow the instructions to restart your system.

**11)Verify:**

- After restarting, reopen Visual Studio.
Create a new project or open an existing one to ensure that the missing components error no longer appears.
   - run flutter doctor to verify
     

![image](https://github.com/gdsc-kits-admin/flutter-bootcamp-2024/assets/116173614/ab8cf47a-37bf-4906-a6d8-159dd9b0465d)

verify using this img , in this vs has no issues so its perfect 


# Open a terminal window.
Navigate to the directory where you want to create your Flutter project.
Run the following command to create a new Flutter project:
```
   flutter create my_flutter_project
```
once the folder is created open that folder in vs code and `start debug` by run your code or `click f5`


