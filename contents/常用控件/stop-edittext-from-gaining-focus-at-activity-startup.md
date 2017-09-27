### 问题：在Activity启动后，使EditText停止获取焦点

### 回答：
#### 采纳答案：

```

<!-- Dummy item to prevent AutoCompleteTextView from receiving focus -->
<LinearLayout
    android:focusable="true" 
    android:focusableInTouchMode="true"
    android:layout_width="0px" 
    android:layout_height="0px"/>

<!-- :nextFocusUp and :nextFocusLeft have been set to the id of this component
to prevent the dummy from receiving focus again -->
<AutoCompleteTextView android:id="@+id/autotext"
    android:layout_width="fill_parent" 
    android:layout_height="wrap_content"
    android:nextFocusUp="@id/autotext" 
    android:nextFocusLeft="@id/autotext"/>
```
#### 答案2：
实际的问题,你只是不想让它获取焦点呢?或者你不想让它显示虚拟键盘由于聚焦`EditText`吗?`EditText`在`onStart`，我没看到它有焦点。当用户没有明确请求关注`EditText`(和打开键盘)，它让softInput窗口打开，它绝对是一个问题。

如果是虚拟键盘的问题
查看 [activity-element](https://developer.android.com/guide/topics/manifest/activity-element.html#activity.)文档

`android:windowSoftInputMode="stateHidden"`在进入`Activity`的时候一直可以让软键盘隐藏

或者使用`android:windowSoftInputMode="stateUnchanged"`
### [StackOverflow原文链接](https://stackoverflow.com/questions/1555109/stop-edittext-from-gaining-focus-at-activity-startup)