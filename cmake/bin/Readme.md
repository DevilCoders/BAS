This repository contains BAS build system.

**How to build.**

1.  Install git client from here https://git-scm.com/download/win. git.exe must be in your path.
2.  Install ```Visual Studio Express 2013 for Windows Desktop``` from contrib/vs folder.
3.  Install ```Visual Studio Express 2015 for Windows Desktop``` from contrib/vs folder.
4.  Tweak config.json file. Change ```gitlab-login``` and ```gitlab-password``` settings.
5.  Use ```DistrPublic.bat``` or ```Development.bat``` in order to build BAS.

In case if you are not sure, if everything was configured correctly, you can just start build process. Build system will verify your settings and report if something is missing.

**How to build modified BAS version.**

If you want to change source code and rebuild do following steps:

1.  Run steps from ```How to build.``` section
2.  Change source code located in ```build\build\x64\source\bas\Solution``` folder. You can checkout specific branch or just edit files.
3.  Set ```pull-before-build``` setting to false. This will prevent build system from reverting your changes.
4.  Use ```DistrPublic.bat``` or ```Development.bat``` in order to build modified BAS version.
  
Don't forget to reset ```pull-before-build``` if you want original build later.


**Build tasks.**

```Development.bat``` - Build BAS and save result into folder. Depending on ```pull-before-build``` setting source code will be obtained from repository or from local folder. This type of build best used for testing and development, because it is much faster than others. Unlike other build types, it doesn't create any installer or archives.

```DistrPublic.bat``` - Build BAS and create installer. This tasks doesn't create premium version build or protect source code.

```DistrPrivate.bat``` - Build BAS and create installer. This tasks creates premium version and protects source code. Requires ```private``` folder obtained from BASBuildPrivate repository.

```Clean.bat``` - Cleans all data compiled on previous build. Use it before any other type of build if you want to ensure, that the old data does not affect the new build.

**Config settings.**

Build may be configured by editing ```config.json``` files. List of settings:

```pull-before-build``` - If build system will reset all uncomitted changes in repository and pull new commits. Disable this option if you want to build BAS with custom changes. Repository is located in ```build\build\x64\source\bas\Solution```.

```gitlab-login``` and ```gitlab-password``` - Your gitlab auth, account must have access at least to BAS repository.

```vs-bas-x86``` - Path to vcvars32.bat file from Visual Studio 2013. Default values must be fine if VS is installed in default folder.

```vs-bas-x64``` - Path to vcvarsx86_amd64.bat file from Visual Studio 2013. Default values must be fine if VS is installed in default folder.

```vs-chrome-x86``` - Path to vcvars32.bat file from Visual Studio 2015. Default values must be fine if VS is installed in default folder.

Rest of options are used for private build only. For development or public build may be set to any value.
