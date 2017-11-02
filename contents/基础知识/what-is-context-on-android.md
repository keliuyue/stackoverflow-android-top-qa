### 问题：Android中Context是什么？

### 回答：
#### 采纳答案：

简单地说：

顾名思义，它是应用程序/对象当前状态的上下文。它让新创建的对象了解正在发生的事情。通常，您调用它获取关于程序（activity and package/application）的另一部分的信息。


你可以通过调用getapplicationcontext()，获得语境getcontext()，getbasecontext()或this（在一个从上下文，如Application, Activity, Service and IntentService类）。

典型用法：

- 创建新对象：创建新视图、适配器、监听器：

```
TextView tv = new TextView(getContext());
ListAdapter adapter = new SimpleCursorAdapter(getApplicationContext(), ...);
```

- 访问公共资源：如LAYOUT_INFLATER_SERVICE服务

```
context.getSystemService(LAYOUT_INFLATER_SERVICE)
getApplicationContext().getSharedPreferences(*name*, *mode*);
```
- 隐式访问组件：关于content providers, broadcasts, intent
```
getApplicationContext().getContentResolver().query(uri, ...);
```


#### 答案2：

**Context的定义**

- Context表示环境数据
- 它提供对数据库等事物的访问。

**简单的例子：**

- 考虑x-man是初创软件公司的首席执行官。
- 公司中有一位首席架构师，这个架构师负责公司的所有工作，如数据库、UI等。
- 现在首席执行官雇佣了一个新的开发人员。
- 建筑师是根据新员工的技能来说明新员工的责任，即他是否会在数据库或UI等方面工作。

**简单的例子2：**
- 这就像访问Android Activity到应用程序的资源一样。
- 这跟你去旅馆的时候是一样的，你想在适当的时间吃早餐、午餐和晚餐，对吗？
- 在逗留期间你还喜欢其他许多事情。你怎么得到这些东西？
- 你叫客房服务员帮你拿这些东西。
- 这里的客房服务人员是考虑到你是一个单一的活动和酒店作为你的应用程序的上下文，最后的早餐，午餐和晚餐必须是资源。

**涉及上下文的东西是：**

1. 加载资源。
2. 创建新的Activity。
3. 创建视图。
4. 获取系统服务。

**Context是Activity、Service、Application的基类。**

另一种描述这一点的方式是：将Context视为电视的遥控器&电视中的频道是资源、服务、使用意图等——这里远程充当访问所有不同资源到前台的访问。

因此，远程可以访问诸如资源、服务、使用意图等通道。
同样.....访问远程的人自然可以访问所有的东西，如资源、服务、使用意图等。

**可以获得上下文的不同调用方法**

- getApplicationContext()
- getContext()
- getBaseContext()
- 或者 this (当在Activity中)

例子：

```
TextView TV=new TextView(this);
```
this指当前活动的Context。

### [StackOverflow原文链接](https://stackoverflow.com/questions/3572463/what-is-context-on-android)