# Simple Animations 1.x migration

Thank you for using **Simple Animations** in your recent projects. Every framework needs to evolve and Simple Animation is no exception.

Simple Animation `2.x.x` has been completely redesigned from ground up and is no longer compatible. Of course you can stay with the lasted version `1.x.x`. 

**But if you want to profit from the new features**, you need to **upgrade** the `simple_animations` dependency to `^2.0.0`. Then you will lose access to `1.x.x` classes and features.

But you don't need to worry. The propose of this package is to supply your project with classes and features from version `1.x.x`. In parallel you can use the new features.

## Migration guide

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

