# Flutter State Management Comparison

This repository provides an overview and comparison of various state management techniques in Flutter. Each technique has its own directory with a simple counter app example to demonstrate its usage.

## State Management Techniques

### Provider

- Suitable for simple to moderate complexity applications.
- Easy to understand and implement, making it a good choice for beginners.
- Provides a straightforward way to manage state and communicate between widgets.

**Example:**

```dart
class CounterProvider extends ChangeNotifier {
  int _count = 0;
  int get count => _count;

  void increment() {
    _count++;
    notifyListeners();
  }
}
```

### Riverpod

- An evolution of the Provider pattern that offers more flexibility and testability.
- Suitable for applications of all complexities.
- Offers better scalability and a more robust approach to state management.

**Example:**

```dart
final counterProvider = StateProvider((ref) => 0);
```

### BLoC/Cubit

- Ideal for complex applications with multiple states and events.
- Provides a clear separation of concerns, making it easier to manage and test.
- Well-suited for large teams and projects that require a structured approach to state management.

**Example (Cubit):**

```dart
class CounterCubit extends Cubit<int> {
  CounterCubit() : super(0);

  void increment() => emit(state + 1);
}
```

### Redux

- Suitable for large-scale applications with complex state management needs.
- Offers a predictable state container, making it easier to track state changes.
- Can be more challenging to learn and implement compared to other patterns.

**Example:**

```dart
class IncrementAction {}

int counterReducer(int state, dynamic action) {
  if (action is IncrementAction) {
    return state + 1;
  }
  return state;
}
```

### GetX

- Offers a simple and efficient way to manage state, navigation, and dependencies.
- Suitable for applications of all sizes.
- Provides a balance between simplicity and functionality.

**Example:**

```dart
class CounterController extends GetxController {
  var count = 0.obs;

  void increment() => count.value++;
}
```

### MobX

- Ideal for applications that require reactive state management.
- Offers a simple and intuitive API for managing state.
- Well-suited for applications with complex state interactions.

**Example:**

```dart
class Counter = _Counter with _$Counter;

abstract class _Counter with Store {
  @observable
  int value = 0;

  @action
  void increment() {
    value++;
  }
}
```

