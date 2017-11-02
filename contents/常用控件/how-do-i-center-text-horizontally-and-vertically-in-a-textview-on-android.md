### 问题：在Android中，如何使TextView水平并垂直居中？

### 回答：
#### 采纳答案：

我假设您使用的是XML布局。

```
<TextView  
    android:layout_width="match_parent" 
    android:layout_height="match_parent" 
    android:gravity="center"
    android:text="@string/**yourtextstring**" />
```

在java中
```
setGravity(Gravity.CENTER);
```

#### 答案2：
```
android:layout_centerInParent="true"
```

当使用一个RelativeLayout,这个可以正常运行，布局的高度和宽度设置为wrap_content。

### [StackOverflow原文链接](https://stackoverflow.com/questions/432037/how-do-i-center-text-horizontally-and-vertically-in-a-textview-on-android)