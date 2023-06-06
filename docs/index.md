---
tag: concept
---
# ScriptoForm

## What is a ScriptoForm
A **ScriptoForm** (pronounced: "Script Oh Form") is a PowerShell script that generates and displays a [Microsoft Windows Forms](https://learn.microsoft.com/en-us/dotnet/desktop/winforms/overview/?view=netdesktop-7.0#introduction) application that can be used for a specific management or system administration task in a computer network environment.  Typically, a ScriptoForm is compiled into an executable file which hides the PowerShell console window during execution and provides a more seamless and familiar experience to the user.

A **ScriptoForm project** is the set of files and folders including the PowerShell script, typically stored in a GIT repository, that are used to compile the executable file using the Microsoft .NET CLI utility (dotnet.exe) which is available with any [Microsoft .NET SDK](https://dotnet.microsoft.com/en-us/download/dotnet).  The ScriptoForm project includes a C# file which the compiler will use as the source for the executable, and a C# project file (csproj file) which provides the set of instructions used to compile the executable.

### Why use a ScriptoForm
A ScriptoForm, which was developed to simplify running complicated IT workflows with PowerShell scripts that require user interaction, is essentially a PowerShell script that provides the user interaction to the script with a Windows Forms (WinForms) instead of a command line interface.  When coded to do so, it provides many user friendly features that we are accustomed to with a WinForms application.  For example, you can code a ScriptoForm to:
- Pre-load text into a textbox that enforces naming standards (e.g. all mail distributions lists should start with the prefix "DG_" per your corporate standards)
- Enforce a specific case for data in real time (e.g. a Windows server name should always be UPPERCASE per your corporate standards)
- Enforce text length in real time (e.g. a Windows server name should never be more that 15 character long per NETBIOS requirements)
- Notify the user that they are typing in invalid characters as they type them (e.g. a Windows server name should not contain a space or other special character)
- Enforce a specific date range (e.g. a user should never be allowed to select a date in the past)

A ScriptoForm not only provides a user friendly experience for script interaction but also helps to ensure that corporate IT naming standards and business rules are followed and can provide instant feedback if they are not.

### Default vendor management tools
The management tools provided provided by vendors to manage their individual products, by their very nature, are designed to be as generic as possible.  They need to be able to handle all possible combinations of settings and options because they cannot possibly know what specific task you are trying to accomplish or your corporate requirements, IT naming standards, or business rules.  Thus they typically provide a "single pane of glass" management application. 

A ScriptoForm allows you to perform the exact task you need to complete without having to navigate through the complicated management tool provided by the vendor.  If designed properly, a ScriptoForm can enforce all your corporate IT naming standards and business rules and eliminate all the individual steps normally required in the vendors native tool.  No clicking through menus, wizards, or other complex interfaces - you simply type in the require information and click the "Run" button.

### [SmartAceDesigns.ScriptoFormTemplates](https://github.com/Smart-Ace-Designs/SmartAceDesigns.ScriptoFormTemplates) Module
This PowerShell module was designed to provide a simple method to scaffold a Windows Forms application, built with PowerShell, that can be used as a starting point for your ScriptoForm project.  A lot of initial coding is required to setup a ScriptoForm from scratch.  This module was developed to alleviate that problem.  When used with the [Visual Studio Code snippets](https://github.com/Smart-Ace-Designs/SmartAceDesigns.ScriptoFormTemplates/blob/main/VSCode/powershell.json) file, you can easily add any addition controls to the form as needed, or you can manually code them once you become more comfortable working with .NET WinForms objects in PowerShell, to provide user interaction and feedback.  You then add PowerShell code to work with the user input provided by the form, that follows and enforces your business logic and rules, to complete the steps in the workflow that the ScriptoForm will be used to complete.

A means to compile the ScriptoForm script and optional support files (referenced by the script) into an executable was developed to provide a more user-friendly method of running the script and is included natively with this module.  This process was designed with four goals in mind:

* The executable should be easy to compile and not require a complicated development environment.  For example, a script developer should be able to use a simple one-line command and the widely available .NET SDK to generate the executable.  The script file should be embedded into the executable as a resource file.
* The script file should be able to reference any number of separate support files that are included in the executable.  For example, a static HTLM email template file used by the script when sending an email should be packaged, also as resource files, along with the script file in the executable.  This makes the executable more portable.
* The executable should be able to select the version of PowerShell to use when running the script file but also controlled the user as needed.  For example, if PowerShell 7 is installed, the script should default to that version unless explicitly excluded by the user with a command line argument to the executable.  If no versions of PowerShell are installed, then the script should fall back to Windows PowerShell.
* The executable should be seamless and hide the PowerShell console window when executed.  This makes for a familiar experience that users of a WinForms application are accustomed to.

### Commercial products
There are several professional commercial products in the market that allow you to create WinForms or WPF applications with PowerShell.  These products include a forms designer for drag-and-drop functionality, an advanced IDE, and technical support, among other things.  These are all great products and I highly recommend you check them out.

However, these products do not fit my personal needs.  I created the ScriptoForm because I wanted 100% control over the format, layout, and naming standards used in my PowerShell scripts.