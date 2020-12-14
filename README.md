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

If you have work with Jenkins and Docker, I suggest you skip to next step or look for other documentation because the oficial Jenkins image of Docker is complete and already have Java. See more in: https://github.com/jenkinsci/docker/blob/master/README.md

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

## Jenkins install

It's time to install Jenkins! 
To look the oficial documentation, visit: https://www.jenkins.io/download/
In my case, I use the Ubuntu Distribution. So I use this link https://pkg.jenkins.io/debian/ and step by step of oficial installation.
If you are using some different OS, go to the link https://www.jenkins.io/download/ and choose de better option for you.
However, here is how we install Jenkins on Ubuntu trought command line:

```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -

sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
    
sudo apt-get update

sudo apt-get install jenkins
```
To check if the Jenkins status, use:
```systemctl status jenkins.service```

And the output is something like that:
```
sthefania@ubuntu:~$ systemctl status jenkins.service 
● jenkins.service - LSB: Start Jenkins at boot time
     Loaded: loaded (/etc/init.d/jenkins; generated)
     Active: active (exited) since Mon 2020-12-14 09:40:50 PST; 2h 33min ago
       Docs: man:systemd-sysv-generator(8)
    Process: 984 ExecStart=/etc/init.d/jenkins start (code=exited, status=0/SUC>

Dec 14 09:40:48 ubuntu systemd[1]: Starting LSB: Start Jenkins at boot time...
Dec 14 09:40:48 ubuntu jenkins[984]: Correct java version found
Dec 14 09:40:49 ubuntu jenkins[984]:  * Starting Jenkins Automation Server jenk>
Dec 14 09:40:49 ubuntu su[1122]: (to jenkins) root on none
Dec 14 09:40:49 ubuntu su[1122]: pam_unix(su-l:session): session opened for use>
Dec 14 09:40:49 ubuntu su[1122]: pam_unix(su-l:session): session closed for use>
Dec 14 09:40:50 ubuntu jenkins[984]:    ...done.
Dec 14 09:40:50 ubuntu systemd[1]: Started LSB: Start Jenkins at boot time.
```

With service jenkins working perfectly, now you need go to a browser of your preference and take a look if Jenkins is available on the web. Jenkins use port 8080: http://localhost:8080

If all it's ok, you will see the first page of configuration Jenkins, and indicate in your OS where is the secret to unlock and proceed.
You can follow the default configuration, and in next screens you must create a user admin to login at the final configuration.

## Setting up Jenkins

After install and make a first configuration on Jenkins, you can configure the enviroments.
The configuration enrviroment indicate to Jenkins, where is Java, SDK android, and anything other full path thats necessary to build the application.
For now, we just need configurate JAVA_HOME and ANDROID_HOME.

> Go to:  **Manage Jenkins > Configure System**.
 Find **Global Settings** section and tick **Environment variables** checkbox to enable it.

In label "Name" put the enviroment name, like JAVA_HOME
In lable "Valeu" put the location that software are installed in you OS, like 

It's commun the build call for enviroment ANDROID_SDK_ROOT, so a keep the two options:

[image]

## Configure project in Jenkins


Build
configuração de pipeline com gradlew

Artefato
gerar apk como artefato

Referencias
https://medium.com/simform-engineering/getting-started-with-jenkins-android-1138ee3d1e99
https://medium.com/@guibasconti/set-up-jenkins-for-android-apps-a3dfbd80940f



