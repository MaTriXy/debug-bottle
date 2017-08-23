<a href="https://travis-ci.org/kiruto/debug-bottle" title="Latest push build on default branch: created">
  <img src="https://travis-ci.org/kiruto/debug-bottle.svg?branch=1.0.1" alt="build:created">
</a>
<a href="https://mvnrepository.com/artifact/com.exyui.android/debug-bottle-runtime" name="status-images" title="Latest version on maven-central">
  <img src="https://img.shields.io/maven-central/v/com.exyui.android/debug-bottle-runtime.svg?maxAge=2592000" alt="version:maven-central">
</a>

[🇨🇳 中文](README-ZH.md) / [🇯🇵日本語](README-JP.md) / [🇬🇧 English](README.md)
 
# 🍼Debug Bottle

An Android debug / develop tools written using Kotlin language. All the features in Debug bottle are only available on debug build version with your app, it doesn't has an impact on release version.

- [CHANGELOG](CHANGELOG.md)
- [TODO](TODO.md)

Demo App is now available at Google Play:

<a href="https://play.google.com/store/apps/details?id=me.chunyu.dev.yuriel.kotdebugtool"><img alt="Get it on Google Play" src="https://play.google.com/intl/en_us/badges/images/apps/en-play-badge-border.png" width="300" /></a>

[<img src="screenshots/introduction.gif" width="225" height="400">](screenshots/introduction.gif)
[<img src="screenshots/quick-toggles.png"/>](screenshots/raw/quick-toggles.png)
[<img src="screenshots/features-2.png"/>](screenshots/raw/features-2.png)

## What can I do with Debug Bottle?
- [Simple OkHttp Sniffer](#okhttp-sniffer)
- [3D preview an Activity with Scalpel](#scalpel-viewer)
- [Simple shared preferences editor](#shared-preferences-editor)
- [Open strict mode any time](#strict-mode)
- [Catch crashes and get stacktrace log](crash-log)
- [Find leaks by using Leak Canary](#leak-canary)
- [Find UI Blocks by using Block Canary](#block-canary)
- [Mock Activity or function entries in developing](#development-entries)

#### OkHttp Sniffer
Enable "Network Listener" at Settings, then you can see all network traffics what requested by your app.

[<img src="screenshots/network-sniffer-1.png"/>](screenshots/raw/network-sniffer-1.png)
[<img src="screenshots/network-sniffer-2.png"/>](screenshots/raw/network-sniffer-2.png)

#### Scalpel Viewer
Enable "3D View", then you can view your Activity. When interaction is enabled the following gestures are supported:
* Single touch: Controls the rotation of the model.
* Two finger vertical pinch: Adjust zoom.
* Two finger horizontal pinch: Adjust layer spacing.

[<img src="screenshots/scalpel-view.png"/>](screenshots/raw/network-sniffer-2.png)
[<img src="screenshots/scalpel-view.gif" width="225" height="400" />](screenshots/raw/scalpel-view.gif)

#### Shared Preferences editor
Preview and edit the Shared Preferences of app more simply.

[<img src="screenshots/shared-preferences-editor-1.png"/>](screenshots/raw/network-sniffer-2.png)
[<img src="screenshots/shared-preferences-editor-2.png"/>](screenshots/raw/network-sniffer-2.png)

#### Strict Mode
Enable or disable Android strict mode at runtime. StrictMode is a developer tool which detects things you might be doing by accident and brings them to your attention so you can fix them. StrictMode is most commonly used to catch accidental disk or network access on the application's main thread, where UI operations are received and animations take place. For more information, see [Android Developers](https://developer.android.com/reference/android/os/StrictMode.html).

#### Crash Log
List all crash stacktrace logs.

[<img src="screenshots/crash.gif" width="225" height="400">](screenshots/raw/crash.gif)

#### Leak Canary
Leak Canary is fully imported. Leak Canary is a memory leak detection library for Android and Java. More about using Leak Canary by visiting [Leak Canary wiki](https://github.com/square/leakcanary/wiki/FAQ).

#### Block Canary
Detect UI blocks at runtime.

[<img src="screenshots/ui-blocks.png"/>](screenshots/raw/network-sniffer-2.png)
[<img src="screenshots/block-canary-demo.gif" width="225" height="400" />](screenshots/raw/block-canary-demo.gif)

#### Development Entries
Launch any Activity with custom Intents, or Runnable you want.

[<img src="screenshots/all-activities.png"/>](screenshots/raw/network-sniffer-2.png)
[<img src="screenshots/run-activity-with-intent.gif" width="225" height="400" />](screenshots/raw/run-activity-with-intent.gif)

## How do I use it?
After installing Debug Bottle Demo app, you'll find there are two app icons appears to launcher. Click bottle icon to run Debug Bottle.

## Setting up

#### 1. Configure your Gradle project
Add snapshot of maven central repository to primary Gradle file:
```gradle
allprojects {
    repositories {
        ...
        mavenCentral()
    }
}
```
Edit and add dependencies in your app module:

```gradle
dependencies {
    debugCompile 'com.exyui.android:debug-bottle-runtime:1.1.1'

    // Use this in your Java project
    releaseCompile 'com.exyui.android:debug-bottle-noop-java:1.1.1'
    testCompile 'com.exyui.android:debug-bottle-noop-java:1.1.1'

    // Use this in your Kotlin project
    releaseCompile 'com.exyui.android:debug-bottle-noop-kotlin:1.1.1'
    testCompile 'com.exyui.android:debug-bottle-noop-kotlin:1.1.1'

    compile 'com.android.support:appcompat-v7:23.2.0+'
}
```

Specially, Debug Bottle not only support API 23+, but also 22. To support API 22, please add dependencies like this:
```gradle
dependencies {
    debugCompile 'com.exyui.android:debug-bottle-runtime:1.0.6-support22'

    // Use this in your Java project
    releaseCompile 'com.exyui.android:debug-bottle-noop-java:1.0.6-support22'
    testCompile 'com.exyui.android:debug-bottle-noop-java:1.0.6-support22'

    // Use this in your Kotlin project
    releaseCompile 'com.exyui.android:debug-bottle-noop-kotlin:1.0.6-support22'
    testCompile 'com.exyui.android:debug-bottle-noop-kotlin:1.0.6-support22'

    compile 'com.android.support:appcompat-v7:22+'
}
```

To support API 23, add dependencies like this:
```gradle
dependencies {
    debugCompile 'com.exyui.android:debug-bottle-runtime:1.0.6-support23'

    // Use this in your Java project
    releaseCompile 'com.exyui.android:debug-bottle-noop-java:1.0.6-support23'
    testCompile 'com.exyui.android:debug-bottle-noop-java:1.0.6-support23'

    // Use this in your Kotlin project
    releaseCompile 'com.exyui.android:debug-bottle-noop-kotlin:1.0.6-support23'
    testCompile 'com.exyui.android:debug-bottle-noop-kotlin:1.0.6-support23'

    compile 'com.android.support:appcompat-v7:23+'
}
```

#### 2. Edit Manifest
Add Debug Bottle main Activity in your Manifest:
```xml
<activity
    android:name="com.exyui.android.debugbottle.components.DTDrawerActivity"
    android:theme="@style/Theme.AppCompat.Light"
    android:label="The Name You Like"/>
```
The value of tag label, will display to your android launch pad.

#### 3. Inject Debug Bottle into your Application
First, you may implement Block Canary Context:
```java
public class AppBlockCanaryContext extends BlockCanaryContext {...}
```

Now you could inject Debug Bottle in your Application like:
```java
public class MyApplication extends Application{
    @Override
    public void onCreate() {
        super.onCreate();
        DTInstaller.install(this)
            .setBlockCanary(new AppBlockCanaryContext(this))
            .setOkHttpClient(httpClient)
            .setInjector("your.package.injector.ContentInjector")
            .setPackageName("your.package")
            .enable()
            .run();
    }
}
```

Or if you use Kotlin, you can inject like:
```kotlin
class MyApplication: Application() {
    override fun onCreate() {
        super.onCreate()
        DTInstaller.install(this)
            .setBlockCanary(AppBlockCanaryContext(this))
            .setOkHttpClient(httpClient)
            .setInjector("your.package.injector.ContentInjector")
            .setPackageName("your.package")
            .enable()
            .run()
    }
}
```

## Links

* [Leak Canary](https://github.com/square/leakcanary)
* [Android Performance Monitor](https://github.com/markzhai/AndroidPerformanceMonitor)

## License

```
Debug Bottle

Copyright 2016 Yuriel (http://exyui.com).

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

Debug Bottle required features are based on or derives from projects below:
- Apache License 2.0
  - [Android Performance Monitor](https://raw.githubusercontent.com/markzhai/AndroidPerformanceMonitor/master/LICENSE)
  - [Leak Canary](https://raw.githubusercontent.com/square/leakcanary/master/LICENSE.txt)
  - [Scalpel](https://raw.githubusercontent.com/JakeWharton/scalpel/master/LICENSE.txt)
  - [Bubbles for Android](https://raw.githubusercontent.com/txusballesteros/bubbles-for-android/master/LICENSE)
  - [Takt](https://raw.githubusercontent.com/wasabeef/Takt/master/LICENSE)
