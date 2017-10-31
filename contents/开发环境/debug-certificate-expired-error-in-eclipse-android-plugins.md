### 问题：用Eclipse开发Android，如何调试证书过期错误？

### 回答：
#### 采纳答案： 

删除您的调试证书在`~ /.Android/debug.keystore`目录在**Linux**和**Mac OS X** 

目录就像Windows中`%USERPROFILE% / android`。

然后，当您下一次尝试构建调试包时，Eclipse插件将生成一个新的证书。你可能需要clean，然后编译生成证书。
### [StackOverflow原文链接](https://stackoverflow.com/questions/2194808/debug-certificate-expired-error-in-eclipse-android-plugins) 
