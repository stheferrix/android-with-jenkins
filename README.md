# How to build an android app with Jenkins

Sometimes you need to build especific applications with Jenkins.
Is this article, we talk about build an Android application with Jenkins using Gradle!

## What do you need to know

Let's start with baby step. First of all, make sure you are familiarized with contexts below:

- Android application: It's an application that work over Java or Kotlin language with prorpose mobile devices 

- Jenkins: A software that provide a enviroment for Continuous Integration and Continous Delivery

- Gradle: Gradle: Is a system based in Java, that automate builds 

To learn more each one, follow:

Android - https://developer.android.com/docs
Jenkins - https://www.jenkins.io/doc/
Gradle- https://docs.gradle.org/current/samples/sample_building_kotlin_applications.html

## Install Java

Jenkins work over Java, so it's important that you have totally control and install it first.

If you have work with Jenkins and Docker, I suggest you skip to next step or look for other documentation because the oficial Jenkins image of Docker is complete and already have Java. See more in: 
https://github.com/jenkinsci/docker/blob/master/README.md

If you are install Jenkins in a virtual machine, you can follow this instructions to install Java Open JDK:

```sudo apt-get install java-8-openjdk```

It's important to know where is Java instalation because we need to set JAVA_HOME enviroment in Jenkins configurations. To know where is java instalation, use this command:

```update-alternatives --config java```

## SDK

How do you need build an Android app, it's necessary that you have installed the SDK Android. This part grants you to compile the application and keep integrated.

To install SDK, you can visit the site of provider or follow the instructions:

The package is in zip format, so if you don't have the unzip utilitarie, install it with:

```sudo apt-get install unzip```

Make a download of SDK package:

```sudo wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip```

Create a folder, in a local of your preference and unzip the package:

```mkdir android-sdk```

```unzip sdk-tools-linux-3859397.zip -d android-sdk```

Accept the license. Don't skip this step, because you have future troubles in a build step:

```yes | android-sdk/tools/bin/sdkmanager --licenses```



Jenkins
instalçao e configuração

Build
configuração de pipeline com gradlew

Artefato
gerar apk como artefato

Referencias
https://medium.com/simform-engineering/getting-started-with-jenkins-android-1138ee3d1e99
https://medium.com/@guibasconti/set-up-jenkins-for-android-apps-a3dfbd80940f

update-alternatives --config java

