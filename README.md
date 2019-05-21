# Netmera

## Installation with Carthage
[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager for Cocoa application. To install the carthage tool, you can use [Homebrew](https://brew.sh).

```
$ brew update
$ brew install carthage
````

To integrate Netmera into your Xcode project using Carthage, specify it in your Cartfile:

```
github "Netmera/Netmera"
github "mutualmobile/MMWormhole" ~> 2.0.0
github "AFNetworking/AFNetworking" >=2.0
github "kishikawakatsumi/UICKeyChainStore" ~>2.0
github "ccgus/fmdb"
```
Then, run the following command to build the Netmera framework and It's dependencies:

```carthage update --platform iOS```

At last, you need to set up your Xcode project manually to add the all frameworks:

1. On your application targets’ “General” settings tab, in the “Linked Frameworks and Libraries” section, drag and drop each framework you want to use from the Carthage/Build folder on disk.

2. On your application targets’ “Build Phases” settings tab, click the “+” icon and choose “New Run Script Phase”. Create a Run Script with the following content:

````/usr/local/bin/carthage copy-frameworks ````

3. Add the paths to the frameworks you want to use under “Input Files”:

````
$(SRCROOT)/Carthage/Build/iOS/Netmera.framework
$(SRCROOT)/Carthage/Build/iOS/FMDB.framework
$(SRCROOT)/Carthage/Build/iOS/AFNetworking.framework
$(SRCROOT)/Carthage/Build/iOS/MMWormhole.framework
$(SRCROOT)/Carthage/Build/iOS/UICKeyChainStore.framework
````

4. Add the paths to the copied frameworks to the “Output Files”:
````
$(BUILT_PRODUCTS_DIR)/$(FRAMEWORKS_FOLDER_PATH)/Netmera.framework
$(BUILT_PRODUCTS_DIR)/$(FRAMEWORKS_FOLDER_PATH)/FMDB.framework
$(BUILT_PRODUCTS_DIR)/$(FRAMEWORKS_FOLDER_PATH)/AFNetworking.framework
$(BUILT_PRODUCTS_DIR)/$(FRAMEWORKS_FOLDER_PATH)/MMWormhole.framework
$(BUILT_PRODUCTS_DIR)/$(FRAMEWORKS_FOLDER_PATH)/UICKeyChainStore.framework
$(BUILT_PRODUCTS_DIR)/$(FRAMEWORKS_FOLDER_PATH)/AFNetworking.framework
````
For more information about how to use Carthage, please see its [project page](https://github.com/Carthage/Carthage).
