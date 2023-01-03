# cicd-pipeline-train-schedule-jenkins

This is a simple train schedule app written using nodejs. It is intended to be used as a sample application for a series of hands-on learning activities.

## Running the app

You need a Java JDK 7 or later to run the build. You can run the build like this:

    ./gradlew build

You can run the app with:

    ./gradlew npm_start

Once it is running, you can access it in a browser at [http://localhost:3000](http://localhost:3000)

## Troubleshooting link 
### 1.
If you just configure your jenkins and project, 
you migth encounter the error saying: 
FAILURE: Build failed with an exception.

* What went wrong:
Could not determine java version from '11.0.17'.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights. :
![image](https://user-images.githubusercontent.com/37641679/210335860-6317ffc9-3ac4-4224-99e1-73341c854259.png)

To handle this error, just updrage manually Gradle version in gradle/wrapper/gradle-wrapper.properties as indicated here: (https://www.handsonprogramming.io/blog/2021/07/gradle/)

### 2. 
If you have this problem : 
![image](https://user-images.githubusercontent.com/37641679/210336470-f42695c8-3997-4272-8b32-79bf2ebb9497.png)

This mean your are trying to use the com.moowork.node Gradle Node plugin, which is no longer maintained by the original author and does not support recent versions of Gradle.

If you need to run Node tasks in your Gradle build, migrate to a plugin that is still maintained, like the com.github.node-gradle.node 15 Gradle Node plugin. ($ vi build.gradle )
plugins {
  id "com.github.node-gradle.node" version "3.5.1"
}

https://discuss.gradle.org/t/could-not-find-method-layout-on-upgrading-to-gradle-7-2/41194
https://plugins.gradle.org/plugin/com.github.node-gradle.node?_ga=2.142435003.868752252.1672739711-1691869626.1672638032
