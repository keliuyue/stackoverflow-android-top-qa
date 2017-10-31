### 问题：如何获取屏幕尺寸而且以像素为单位？

### 回答：
#### 采纳答案：

如果你想要显示的像素可以使用[getSize](http://developer.android.com/reference/android/view/Display.html#getSize%28android.graphics.Point%29) 方法

```
Display display = getWindowManager().getDefaultDisplay();
Point size = new Point();
display.getSize(size);
int width = size.x;
int height = size.y;
```

如果你不是在一个`Activity`你可以通过`WINDOW_SERVICE`默认显示:

```
WindowManager wm = (WindowManager) context.getSystemService(Context.WINDOW_SERVICE);
Display display = wm.getDefaultDisplay();
```

之前介绍了`getSize`(在API级别13),您可以使用现在过时的`getWidth`和`getHeightmethods`:

```
Display display = getWindowManager().getDefaultDisplay();
int width = display.getWidth();  // deprecated
int height = display.getHeight();  // deprecated
```

然而,对于你的用例描述,`margin`/`padding`在布局似乎更合适。

另一个方法是:`DisplayMetrics`

一种描述一般显示信息的结构类,如它的大小,密度,和字体缩放。访问`DisplayMetrics`成员,初始化一个对象是这样的:

```
DisplayMetrics metrics = new DisplayMetrics();
getWindowManager().getDefaultDisplay().getMetrics(metrics);
```

我们可以使用`widthPixels`获取信息:
意思是：在屏幕上用像素显示的绝对宽度

**Sample**
```
Log.d("ApplicationTagName", "Display width in px is " + metrics.widthPixels);
```

### [StackOverflow原文链接](https://stackoverflow.com/questions/1016896/get-screen-dimensions-in-pixels)