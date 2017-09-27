### 问题：Android设备的ID是不是唯一的，使用java有什么简单的方法可以获取？

### 回答：
#### 采纳答案： 
[Settings.Secure](https://developer.android.com/reference/android/provider/Settings.Secure.html#ANDROID_ID)返回设备的ID作为每个用户唯一的64位十六进制字符串。

```
import android.provider.Settings.Secure;

private String android_id = Secure.getString(getContext().getContentResolver(),Secure.ANDROID_ID); 
```                                                    

### [StackOverflow原文链接](https://stackoverflow.com/questions/2785485/is-there-a-unique-android-device-id) 
