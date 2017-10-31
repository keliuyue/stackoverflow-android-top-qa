### 问题：使用SaveInstanceState保存Android Activity的状态

### 回答：
#### 采纳答案： 
你需要重写`onSaveInstanceState(Bundle savedInstanceState)`方法然后写下你想要修改的的应用的值到`Bundle`参数中,像这样：

```
@Override
public void onSaveInstanceState(Bundle savedInstanceState) {
  super.onSaveInstanceState(savedInstanceState);
  // Save UI state changes to the savedInstanceState.
  // This bundle will be passed to onCreate if the process is
  // killed and restarted.
  savedInstanceState.putBoolean("MyBoolean", true);
  savedInstanceState.putDouble("myDouble", 1.9);
  savedInstanceState.putInt("MyInt", 1);
  savedInstanceState.putString("MyString", "Welcome back to Android");
  // etc.
}
```      
                                              
Bundle本质上是存储NVP(键值对)map,它会传递到`onCreate()`和`onRestoreInstanceState()`,r然后你需要提取，像这样：
```
@Override
public void onRestoreInstanceState(Bundle savedInstanceState) {
  super.onRestoreInstanceState(savedInstanceState);
  // Restore UI state from the savedInstanceState.
  // This bundle has also been passed to onCreate.
  boolean myBoolean = savedInstanceState.getBoolean("MyBoolean");
  double myDouble = savedInstanceState.getDouble("myDouble");
  int myInt = savedInstanceState.getInt("MyInt");
  String myString = savedInstanceState.getString("MyString");
}
```
你通常可以使用这种技术为您的应用程序来存储实例的值（选择保存的文本，等等）。


### [StackOverflow原文链接](https://stackoverflow.com/questions/151777/saving-android-activity-state-using-save-instance-state) 
