nitra-dart
==========

Nitra grammar for the Dart programming language.

## Prerequisites

### Installing Nemerle

Nitra is authored in a custom CLR language called Nemerle. Before attempting anything else you must get Nemerle working on your computer.

If you are using Visual Studio 2013 there is no offical build on the Nemerle homepage but there is one at the Visual Studio center:

http://visualstudiogallery.msdn.microsoft.com/fb29c7b2-d1e5-42e4-8a56-9b9c022c22a9

If you are not using VS2013 you could probably use one of the installer from the offical homepage:

http://nemerle.org/Downloads

Once you have installed Nemerle you can verify that it is working by starting Visual Studio and opening the create new project dialog. 
On the right hand side among the project templates, you should find a Nemerle node similar to the C# and Visual Basic nodes. There should be
a Nitra node under the Nemerle node which contains two templates, Empty parser libarary, and Sample parser application.
If you find this you probably have succeeded in installing nemerle and can move on to the next step.

### Installing Nitra

Go the to the download section of Nitra's homepage, download the installer "Nitra.Setup.msi.", close all VS instances, and run it.

http://confluence.jetbrains.com/display/Nitra/Install

## Opening the Dart grammar project

Now that nemerle and Nitra are installed you should be able to open the Dart.Grammar project by simply opening the .sln file in the root.

To build just hit Ctrl+Shift+B as usual. This should produce the Dart.Grammar.dll that is what we need.

## Testing the grammar in Nitra.Visualizer

Start the Nitra.Visualizer (the start-menu shortcut is named "Parser Visualizer"). TODO...

## Using the Dart grammar in Visual Studio

In order to use the Dart Grammar DLL in Visual Studio you must configure it as a language in the Nitra Visual Studio extension. This is done
by editing the file NitraGlobalConfig.xml which is probably located in C:\Program Files (x86)\JetBrains\Nitra. Add the following section as
a child to the <Langague> element:

    <Language Name="Dart" FileExtensions=".dart" Grammar="Dart" StartRule="CompilationUnit">
      <Module>C:\Temp\nitra\Dart.Grammar\Dart.Grammar\bin\Debug\Dart.Grammar.dll</Module>
    </Language>

In the example above I use the path to where the build output from the Dart.Grammar project ends up. This way I don't have to copy
the file to another directory. However the downside is that the file will be locked as soon as a .dart file has been opened in Visual Studio.
So to rebuild and you will have to close all .dart files, close Visual Studio, start Visual Studio, build, and then again open a .dart file.

