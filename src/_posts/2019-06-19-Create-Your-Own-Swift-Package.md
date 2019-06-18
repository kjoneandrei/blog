---
title: Create Your Own Swift Package
date: 2019-06-19 10:00:00
tags: [ios,swift,swift package manager]
authorIds:
- anho
categories:
- iOS
---

## Intro 

In Part 1,  [Add a Swift Package to Your iOS Application](https://), of this Swift Package Manager series we saw how you can add an already existing package to your application. 

Now, you might be wondering, How can I create my own package? The answer is simpler than you might expect.

Below we will see how you can create your own package.

### Part 1: Creating a new Package

Since Swift Package Manger is integrated with the Swift build system, once you have Swift installed on your machine, you can access Swift Package Manager via the Terminal. This means you can also create a package with a simple command. 

To do so, create a new folder called `MySwiftPackage` and navigate to it in Terminal. Once you are here go ahead and run: 

```

$ swift package init --type library

```

This command will generate the base for your package and all the attached configuration needed. To verify this worked for you, the output of this command will look something like this: 

```

Creating library package: MySwiftPackage
Creating Package.swift
Creating README.md
Creating .gitignore
Creating Sources/
Creating Sources/MySwiftPackage/MySwiftPackage.swift
Creating Tests/
Creating Tests/LinuxMain.swift
Creating Tests/MySwiftPackageTests/
Creating Tests/MySwiftPackageTests/MySwiftPackageTests.swift
Creating Tests/MySwiftPackageTests/XCTestManifests.swift

```

The points of interests for us are the file called `Package.swift`, which represents the configuration file for our package. Here you can specify platform limitations, dependencies for our package, versions of the language supported etc.

Sometimes you might want to make your package available only for specific platforms, such as iOS. You can do this by adding a section called `platforms` to your `Package.swift`.

```swift

platforms: [
.iOS(.v12),
],

```

The above will make our package available only for the iOS, starting with version 12.  


### Part 2: Adding Functionality to Your Package 

Now that we have laid out the base for our package, we need to add some functionality to it as well. To do that, we need to look at the structure that the init command has created for us. 

In your project’s root, you will be able to see that this has generated a folder structure `Sources/MySwiftPackage`. Here, once developed, is where we will add our .swift files containing our functionality.

Once you have done this, push your package to GitHub and create a release. To learn about how you can integrate your package in a new/existing project, make sure to check [Part 1](https://) of this Swift Package Manager series.

### Part 3: Updating an Existing Framework to a Swift Package. 

In most of the scenarios, you might already have created a iOS, macOS, watchOS etc. framework, that you have already got people using and would like to support Swift Package Manager as well. 

Navigate to your project’s root in Terminal and follow the instructions presented on point 1 of this article. 

Once you have done that and you have the base for your package, you just need to link the existing code to your `Sources/MySwiftPackage` folder. 

To do this you will need to use the Terminal once again where you will be able to link your existing functionality by running the following command for all the files containing functionality in your framework: 

```
$ ln -s source target`

```

So if for example our package contains only one file `DataFormatter.swift` that is in charge of formatting some data for our application, the source will be replaced with the path of the file and the target will be replace with `Sources/MySwiftPackage`.

Now to release your package, you will need to push it to GitHub and create a release. 

## Final notes

Swift Package Manage represents an alternative to CocoaPods and Carthage when it comes to distrubuting your packages and with it now being part of Xcode 11, we expect it's popularity to increase and to see more are more packages distributed with it in the near future.

For further reading make sure to read Apple's Swift Package Manger documentation [here]("https://swift.org/package-manager/").

Hope to see you next time!
