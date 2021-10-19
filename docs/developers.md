[![Logisim-evolution](img/logisim-evolution-logo.png)](https://github.com/logisim-evolution/logisim-evolution)

---

# Developers #

* [« Go back](../README.md)
* **Developer's corner**
  * [Requirements](#requirements)
  * [Gradle](#gradle)
  * [Import project into IDE](#import-project-into-ide)
    * [Eclipse](#import-project-into-ide)
    * [InteliJ IDEA](#import-project-into-ide)
  * [Building from sources](#building-from-sources)
  * [Testing development code](#testing-development-code)
  * [Code style](style.md)
    * [Checking code style with InteliJ IDEA](style.md#checking-code-style-with-intelij-idea)
    * [Using Gradle plugin](style.md#using-gradle-plugin)
    * [Using `pre-commit`](style.md#using-pre-commit-hooks)
  * [Translations](localization.md)
    * [Updating existing translation](localization.md#updating-existing-translation)
    * [Adding new translation](localization.md#adding-new-translation)
    * [Using trans-tool](localization.md#using-trans-tool)
  * [How to contribute](#how-to-contribute)

---

## Requirements ##

`Logisim-evolution` is written in Java 16. To build it from sources you need JDK
(or equivalent, e.g. [OpenJDK](https://adoptopenjdk.net/)) version 16 or newer.

**NOTE:** Ensure your `$JAVA_HOME` environment variable points to the proper JDK version.

## Gradle ##

`Logisim-evolution` uses the [Gradle](https://gradle.org) build system, which means it can be easily imported into modern IDEs
that support it, including [Eclipse](https://www.eclipse.org) and [IntelliJ IDEA](https://www.jetbrains.com/idea/).

## Import project into IDE ##

How to import a Gradle project:

* [How to import Gradle project into Eclipse](https://www.eclipse.org/community/eclipse_newsletter/2018/february/buildship.php),
* [How to import Gradle project into IntelliJ IDEA](https://www.jetbrains.com/help/idea/gradle.html) (section "Importing a project
  from a Gradle model").

**Note for Eclipse users:**

To successfully import the project in Eclipse, the complete project structure must be present,
including Java source files built by Gradle.
You can do this by running Gradle task `genFiles` before importing the project.
See [Building from sources](#building-from-sources) for how to run Gradle.

To run the task within Eclipse after importing the Logisim-evolution project:

* Bring up the `Gradle Tasks` view, if it is not already showing, by selecting the menu `Window/Show View/Other...`
  and selecting `Gradle Tasks` under Gradle.
* In the `Gradle Tasks` view, double-click on `logisim-evolution/build/genFiles`.
  Check the `Console View` to see when it finishes.
* Right click on the Logisim-evolution project in the Project Explorer and select `Gradle/Refresh Gradle Project`.
* You may then need to right click on the Logisim-evolution project and select `Refresh`.

## Building from sources ##

To build and run the `Logisim-evolution` application, invoke the `Gradle` build system and pass a task name as an argument.
`Logisim-evolution` comes with a Gradle wrapper script, which can be invoked as `./gradlew <ARGS>` on Linux or macOS, and
`gradlew <ARGS>` on Windows.

To build and run on Linux and macOS:

```bash
./gradlew run
```

or on Windows:

```bash
gradlew run
```

If you wish to create a Java JAR package, which can then be run without [Gradle](https://gradle.org), execute:

```bash
./gradlew shadowJar
```

which will create `logisim-evolution-<version>-all.jar` in `build/libs/`.
To run it with JRE/JDK 16 or higher, type:

```bash
java -jar logisim-evolution-<version>-all-jdk<jdk>.jar
```

for example:

```bash
java -jar logisim-evolution-3.6.0-all-jdk16.jar
```

You can also generate a platform-specific installer, which gets saved in `build/dist`.
Packages can be built by running the `jpackage` task:

```bash
./gradlew jpackage
```

> **NOTE:** `jpackage` creates the installer for the platform that builds it. Building cross-platform installers is not supported
> by Java's `jpackage` utility. You may also need to install additional developer tools for the platform in order to build the
> installer. See Java's [jpackage documentation](https://docs.oracle.com/en/java/javase/14/jpackage/packaging-overview.html)
> for more details of tool requirements.

To see all available tasks run: `./gradlew tasks --all`

## Testing development code ##

`Logisim-evolution` is often updated.
The [branch `develop`](https://github.com/logisim-evolution/logisim-evolution/tree/develop)
is the place where all the work on next release happens.
Once the code reaches the point it is ready for the next public release, it will
be merged into the [`master` branch](https://github.com/logisim-evolution/logisim-evolution/tree/master) and released.
But if you want to contribute, or even just see what we are currently working on, checkout the `develop` branch
and build `Logisim-evolution` from source as described above.

**If you see any issues or have any ideas for improvement, please
[create a ticket](https://github.com/logisim-evolution/logisim-evolution/issues) to make `Logisim-evolution` better!**

---

## How to contribute ##

If you want to contribute to Logisim-evolution, this is how to do it:

* Make a local *fork* of `Logisim-evolution` by clicking the *Fork* button on the
  [project GitHub page](https://github.com/logisim-evolution/logisim-evolution).
* Fix the bugs you want to fix on your local fork in the
  [`develop` branch](https://github.com/logisim-evolution/logisim-evolution/tree/develop).
* Add the features you want to add on your local fork.
* Add/modify the documentation/language support on your local fork.

Once it is running without bugs on your local fork, request a *Pull request* by:

* Go to the *Pull request*-tab and click the button *New pull request*.
* Click on *compare across forks*.
* On the right hand side select your fork, for example: *head repository: BFH-ktt1/logisim-evolution*
* On the right hand side select your branch, for example: *base: bugfixes*
* On the left hand side select the development branch *base: develop* (**Important:** All pull requests must be on
  the [branch `develop`](https://github.com/logisim-evolution/logisim-evolution/tree/develop) as
  the [branch `master`](https://github.com/logisim-evolution/logisim-evolution/tree/master) only holds the code
  of the latest stable release!)
* Make sure that there are no conflicts reported.