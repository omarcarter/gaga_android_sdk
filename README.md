# Gaga Android SDK Integration Guide

A concise integration guide for adding the Gaga Miner Android SDK to your app.

## Overview

This repository documents end-to-end integration of the `gaga_android_sdk` and links to the
official sample application. Use it as a quick-start checklist when wiring mining SDK
functionality into an Android project.

## Prerequisites

- Android Studio or equivalent Gradle-based Android build setup
- Internet and network-state permissions declared in `AndroidManifest.xml`

## Installation

1. Download the latest release `gaga_sdk` `.jar` package from the [official SDK repo](https://github.com/gaganode/gaga_android_sdk).
2. Place the `.jar` in your app module's `libs/` folder.
3. Register it as a module library in your IDE project settings.

## Permissions

Declare these entries in `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Initialize the SDK

Replace the placeholder below with a real token before release:

```java
String token = "{your token}";
SharedPreferences miner_sdk_sp = getSharedPreferences("miner_sdk", MODE_PRIVATE);
long node_id = miner_sdk_sp.getLong("node_id", Math.abs(new Random().nextLong()));
miner_sdk_sp.edit().putLong("node_id", node_id).apply();

MinerSdk.Init(token, node_id);
MinerSdk.Start();
```

## Notes

- Store actual tokens securely; don’t ship placeholder tokens in production builds.
- See [Gaga Android](https://github.com/gaganode/gaga_android) for a complete working sample.

## License

This integration guide is released as-is. If you are redistributing or packaging the
SDK itself, follow the license terms bundled with the upstream Gaga Miner SDK artifacts.
