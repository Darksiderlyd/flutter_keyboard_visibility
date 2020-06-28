# keyboard_visibility

通知键盘隐藏显示

# 依赖
代码拉到本地放到你的项目的同一个父目录下

```
 keyboard_visibility:
    path: ../flutter_keyboard_visibility
```
或者直接依赖修改过后的我的git
```
 keyboard_visibility:
    git:
      url: git@github.com:Darksiderlyd/flutter_keyboard_visibility.git
```

# 修改了compileSdkVersion 27带来的release打包问题 修改为28

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

