# keyboard_visibility

通知键盘隐藏显示

# 依赖
依赖方式
```
keyboard_visibility: any
```
or 
```
keyboard_visibility: ^[CURRENT VERSION NUMBER]
```

or 代码拉到本地放到你的项目的同一个父目录下

```
 keyboard_visibility:
    path: ../flutter_keyboard_visibility
```

# 使用
在initState中添加监听销毁通知

```dart
import 'package:keyboard_visibility/keyboard_visibility.dart';


 int subscribeId;

 @protected
 void initState() {
   super.initState();
   subscribeId = KeyboardVisibilityNotification().addNewListener(
     onChange: (bool visible) {
       print(visible);
     },
   );
 }

 //及时移除防止内存泄漏问题 "A LoginInputCodeViewModel was used after being disposed."
 @override
  void dispose() {
    KeyboardVisibilityNotification().removeListener(subscribeId);
    super.dispose();
  }
```

