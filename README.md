# Simple Animations 1.x migration

Thank you for using **Simple Animations** in your recent projects. Every framework needs to evolve and Simple Animation is no exception.

Simple Animation `2.x.x` has been completely redesigned from ground up and is no longer compatible. Of course you can stay with the lasted version `1.x.x`. 

**But if you want to profit from the new features**, you need to **upgrade** the `simple_animations` dependency to `^2.0.0`. Then you will lose access to `1.x.x` classes and features.

But you don't need to worry. The propose of this package is to supply your project with classes and features from version `1.x.x`. In parallel you can use the new features.

## Migration guide

This guide will lead you through the upgrading process of Simple Animation.

### Upgrade project dependencies 

Change your pubspec.yaml:

- Add the dependency `sa_v1_migration: ^1.0.0` to your project.

- Upgrade the Simple Animations dependency `simple_animations: ^2.0.0`.

- Execute a **pub upgrade**.

Use your IDEs search and replace feature to replace

```dart
import 'package:simple_animations/simple_animations.dart';
```

with

```dart
import 'package:simple_animations/simple_animations.dart';
import 'package:sa_v1_migration/sa_v1_migration.dart';
```

Now everything will compile. You can now

### Content of this package

This package (`sa_v1_migration`) contains the lastest stable release of Simple Animation version `1.x`. This way you can use classes from version `1.x.x` along with `2.x.x`.


### Replacing mechanisms

Now you can focus on replacing your existing code with the new mechanisms.

#### ControlledAnimation widget

All aspects of the `ControlledAnimation` widget are available on version `2.x.x`. The new `CustomAnimation` comes closest to the feature set of `ControlledAnimation`.

You might also take a look at `PlayAnimation`, `LoopAnimation` and `MirrorAnimation` widgets as they represent simpler variants of `CustomAnimation`.

Look at [**Stateless Animation README**](https://pub.dev/packages/sa_stateless_animation) for further details.


#### MultiTrackTween

The `MultiTrackTween` has been reworked into a new `MultiTween`. It has the same feature set but it's easier to use and fully type-safe.

Look at [**MultiTween README**](https://pub.dev/packages/sa_multi_tween) for further details.


#### AnimationControllerX

The `AnimationControllerX` or a similar alternative implementation of an `AnimationController` is not available in version `2.x.x`.

Simple Animations version `2.x.x` focuses on utilizing the core mechanics of the Flutter framework and to simplify on top of them. Providing an alternative to a core feature of Flutter may introduce problems in the future. Further investions into that direction are not rewarding to the platform.

#### AnimationControllerMixin

The `AnimationControllerMixin` came along with `AnimationControllerX` and helped with initializing and disposing an `AnimationControllerX` instance inside a stateful class.

Simple Animations version `2.x.x` offers a similar mechanism called `AnimationMixin` that effordlessly creates managed `AnimationController` instances. 

Look at [**Anicoto README**](https://pub.dev/packages/sa_anicoto) for further details.

#### Rendering

A similar mechanism to `Rendering` widget isn't available in Simple Animation version `2.x.x`. The use cases for that widget are rare. Also the `Rendering` widget alone doesn't help developers enough.

I recommend using a `LoopAnimation` widget to create an endless animation and to track the "passed time" yourself.