### 问题：如何解决Android系统NetworkOnMainThreadException?

### 回答：
#### 采纳答案： 
当应用程序试图执行网络操作主线程，这个异常会发生。在`AsyncTask`运行代码:

```
class RetrieveFeedTask extends AsyncTask<String, Void, RSSFeed> {

    private Exception exception;

    protected RSSFeed doInBackground(String... urls) {
        try {
            URL url = new URL(urls[0]);
            SAXParserFactory factory = SAXParserFactory.newInstance();
            SAXParser parser = factory.newSAXParser();
            XMLReader xmlreader = parser.getXMLReader();
            RssHandler theRSSHandler = new RssHandler();
            xmlreader.setContentHandler(theRSSHandler);
            InputSource is = new InputSource(url.openStream());
            xmlreader.parse(is);

            return theRSSHandler.getFeed();
        } catch (Exception e) {
            this.exception = e;

            return null;
        }
    }

    protected void onPostExecute(RSSFeed feed) {
        // TODO: check this.exception
        // TODO: do something with the feed
    }
}
```      
                                              
如何执行这个`Task`

在`MainActivity.java`文件中你可以添加这行代码到你的`oncreate()`方法内
```
 new RetrieveFeedTask().execute(urlToRssFeed);
```
不要忘记添加网络权限到`AndroidManifest.xml`中

```
<uses-permission android:name="android.permission.INTERNET"/>
```



### [StackOverflow原文链接](https://stackoverflow.com/questions/6343166/how-do-i-fix-android-os-networkonmainthreadexception) 
