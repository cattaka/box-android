# Android box

The `wercker/android` box runs on ubuntu 12.04 and provides a selection of the Android toolchain:

* gradle 2.2.1
* android sdk version 24.4.1
* android build tools 22.0.1 and 23.0.1
* android API 22 (android 5.1.1),API 23 (android 6.0)
* android support library
* google play service repository

The box also inherits tools from a not yet official java box, resulting in the following additional tools:

* oracle java 7
* ant and ivy
* maven

A typical android application can use the following yaml:

``` yaml
box: wercker/android
# Build definition
build:
  # The steps that will be executed on build
  steps:
    - script:
        name: show base information
        code: |
          gradle -v
          echo $ANDROID_HOME
          echo $ANDROID_BUILD_TOOLS
          echo $ANDROID_UPDATE_FILTER
    # A step that executes `gradle build` command
    - script:
        name: run gradle
        code: |
          gradle --full-stacktrace -q --project-cache-dir=$WERCKER_CACHE_DIR build
```

There are a number of environment varaibles declared for your information:

* ANDROID_SDK_VERSION : version of the sdk
* ANDROID_BUILD_TOOLS : which versions of the build tools are installed.
* ANDROID_UPDATE_FILTER : shows all sdk elements which are installed

# What's new

* update sdk version and upgraded gradle version added additional android-20/21 tools
* removed build tools 18.0.1 & 19.0.3

# Guides

* [Getting started with android and wercker - part 1](http://blog.wercker.com/2013/09/19/Gettingstarted-with-android-part-1.html)
* [Getting started with android and wercker - part 2](http://blog.wercker.com/2013/09/24/Gettingstarted-with-android-part-2.html)
* [Getting started with android and wercker - part 3](http://blog.wercker.com/2013/09/27/Gettingstarted-with-android-part-3.html)
* [Getting started with android and wercker - part 4](http://blog.wercker.com/2013/10/04/Getting-started-with-android-part-4.html)
* [Autoincrement versioning for android](http://blog.wercker.com/2013/10/11/auto-increment-versioning-for-android.html)

# License

The MIT License (MIT)

Copyright (c) 2013 wercker

# Changelog

## 1.3.0
* install android-22, android-23 tools.
* dropped build tools 22.0.1 and 23.0.1 (box size restrictions)
* dropped Android api level 19 (box size restrictions)

## 1.1.0
* install additional android-20, android-21 tools.
* dropped build tools 18.0.1 and 19.0.3 (box size restrictions)
* dropped Android api level 18 (box size restrictions)

## 1.0.9

* updated gradle to 2.2.1
* updated Android SDK to 24.0.2
* updated Android Build Tools to 21.1.2


## 1.0.8

* updated gradle to 2.2

## 1.0.7

* upgraded android sdk version to 23.0.5

## 1.0.6

* updated gradle to 2.1

## 1.0.5

* google play service repository added

## 1.0.4

* updated gradle to 1.12
* updated Android SDK to 23

## 1.0.3

* add android buildtools 19.1.0

## 1.0.2

* updated gradle to 1.11

## 1.0.1

* android buildtools 19.0.1 updated to 19.0.3

## 1.0.0

* updated gradle to 1.9
* android tools 19 updated to 19.0.1 (Android 4.4.2)
* dropped: android build tools 17, 18 and android 17 api, system image for
level 18 (reason: box size)

## 0.0.19

* sys image 18

## 0.0.18

* sys image 19

## 0.0.17

* android sdk version bumped to 22.2.1
* build tools release 19 added (Android 4.4)

## 0.0.16

* switched to gradle 1.8

## 0.0.15

* $ added for environment variables in the default wercker.yml

## 0.0.14

* expanded readme.
* ANDROID_SDK_VERSION environment variable added

## 0.0.13

* initial release
