# 安卓JS注入

## 注入

使用WebView的 **addJavascriptInterface(Object object, String name)** 方法将本地的对象注入到JS中。

例如：

```java 
class A {
    @JavascriptInterface
    public void foo(String s) {}
}

webView.addJavascriptInterface(new A(), "B");
```
那么JS代码中科通过 B.foo("abcd") 来访问本地对象A中的foo方法。 <br />

*注意：方法名必须一致。*

## AndroidJs主要方法

1. **has(String version, String method)** <br />
用于判断本地代码的当前版本是否有JS要访问的方法。

2. **invoke(String version, String method, String jsonStr, String callBack)** <br />
封装了服务器对本地代码的访问。<br />
method是JS要访问的接口名字，用于区分不同的事件。<br />
jsonStr是可解析的Json格式的字符串，是method要用到的参数。

3. 关于回调callBack
回调时执行 **mWebView.loadUrl("javascript:" + callback + "(" + jsonStr + ")");** <br />
其中，callback是服务器传下来的回调方法名，jsonStr是可解析的Json格式字符串

## 注意
1. WebView要想使addJavascriptInterface生效，必须设置 **setJavaScriptEnabled(true)**
2. API 17及以后的版本，要绑定的本地方法必须要加上 **JavascriptInterface** 注释，才能生效。所以建议服务器可以访问的本地方法都加上JavascriptInterface注释。
3. JS不能访问到本地对象的属性
4. JS和本地对象的交互是在后台进程中进行的，所以要保证线程安全。
5. JS的某些参数有可能为null、""或"undefined", 还有可能不传，注意容错。