# Simple Animations 1.x migration

Thank you for using **Simple Animations** in your recent projects. Every framework needs to evolve and Simple Animation is no exception.

## Migration guide

This guide will lead you through the upgrading process of Simple Animation.

### Upgrade project dependencies 

Change your pubspec.yaml:

- Set the Simple Animations dependency `simple_animations: ^2.1.0` and execute a **pub upgrade**.

- Simple Animations will expose the content of this package.

### Content of this package

This package (`sa_v1_migration`) contains the lastest stable release of Simple Animation version `1.x`. This way you can use classes from version `1.x.x` along with `2.x.x`.

All classes from version `1.x.x` has been marked as deprecated.

### Replacing deprecated classes

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

You can replace the `Rendering` widget by using a `LoopAnimaton` with a `ConstantTween(1)` and ignore the animated value.

```dart
LoopAnimation<int>(
  tween: ConstantTween(1), // <-- any tween will satisfy the API here
  builder: (context, child, value) { // <-- ignore 'value'
    // endless rendering loop
    return ...
  },
)
```

The `Rendering` widget supplied you with the passed time. You can get that behavior by using the following snippet (uses [supercharged](https://pub.dev/packages/supercharged) syntactic sugar):

```dart
var startTime = DateTime.now().duration(); // Duration() passed since 01.01.1970
```

Instead of using `AnimationProgress` class to track the progression of your particle animation you can just save a `startTime` and a `duration` for your particle. You can get the current progress with:

```dart
double progress() {
  return ((DateTime.now().duration() - startTime) / duration)
    .clamp(0.0, 1.0)
    .toDouble();
}
```