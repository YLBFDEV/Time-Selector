# Time-Selector 
[ ![最新版本](https://api.bintray.com/packages/liuli/maven/Time-Selector/images/download.svg) ](https://bintray.com/liuli/maven/Time-Selector/_latestVersion) [![GitHub tag](https://img.shields.io/github/tag/YLBFDEV/Time-Selector.svg)](https://github.com/YLBFDEV/Time-Selector/releases/tag/1.1.1) [![GitHub commits](https://img.shields.io/github/commits-since/YLBFDEV/Time-Selector/1.1.1.svg)](https://github.com/YLBFDEV/Time-Selector/compare/1.1.1...YLBFDEV:master) [![License](https://img.shields.io/badge/license-Apache%202.0-green.svg)](https://www.apache.org/licenses/LICENSE-2.0) [![Platform](http://img.shields.io/badge/platform-android-brightgreen.svg?style=flat)](http://developer.android.com/index.html) [![Language](http://img.shields.io/badge/language-java-orange.svg?style=flat)](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

##*控件基于[jingchenUSTC/TimePicker](https://github.com/jingchenUSTC/TimePicker)*

![预览图](https://raw.githubusercontent.com/YLBFDEV/Time-Selector/master/art/kinephoto.gif)




开始使用：
- Android Studio中直接在 gradle中加入：
```javascript
    compile 'com.feezu.liuli:timeselector:latest.release' 
```
项目中依赖了
```script
    compile 'com.android.support:appcompat-v7:25.3.1'
```

*如果遇到冲突请去除*
	```script
    	compile ('com.feezu.liuli:timeselector:latest.release'){  
        	exclude module: 'appcompat-v7'  
    	} 
	```

- Eclipse下请[下载源码](https://github.com/YLBFDEV/Time-Selector/archive/master.zip)（建议尽早迁移至Studio）


 构造1：

`TimeSelector(Context context, ResultHandler resultHandler, String startDate, String endDate)`

**参数说明：ResultHandler为选取时间后的回调 startDate，endDate为时间控件的可选起始时间和结束时间。*

```java
        TimeSelector timeSelector = new TimeSelector(this, new TimeSelector.ResultHandler() {
            @Override
            public void handle(String time) {
                Toast.makeText(getApplicationContext(), time, Toast.LENGTH_LONG).show();
            }
        }, "2015-11-22 17:34", "2015-12-1 15:20");
```

构造2：

` 
	TimeSelector(Context context, ResultHandler resultHandler, String startDate, String endDate, String workStartTime, String workEndTime)
`

**参数说明：传入workStartTime，workEndTime可选时间为起始时间和结束时间范围内的每日“时：分”的起始和结束时间，如限制可选时间为：朝9晚5。*
```java 
		TimeSelector timeSelector = new TimeSelector(this, new TimeSelector.ResultHandler() {
            @Override
            public void handle(String time) {
                Toast.makeText(getApplicationContext(), time, Toast.LENGTH_LONG).show();
            }
        }, "2015-10-30 10:34", "2015-12-1 17:34","9:00","17:00");
```
使用：
`timeSelector.show();`


* *1.1.0更新加入：*
>限制拨动 时和分
在show前调用：     
```java  timeSelector.disScrollUnit(TimeSelector.SCROLLTYPE.HOUR, TimeSelector.SCROLLTYPE.MINUTE); ```
>设置显示模式： 年月日时分（默认）|年月日
在show前调用：
```java 
timeSelector.setMode(TimeSelector.MODE.YMDHM);//显示 年月日时分（默认）；
timeSelector.setMode(TimeSelector.MODE.YMD);//只显示 年月日
```

* *1.1.1更新加入：*
>更新基础控件PickView,设置是否循环显示内容
可调用PickView实例的<code>setIsLoop(boolean isLoop)</code>方法，也可以在布局中如下使用
```xml
		<org.feezu.liuli.timeselector.view.PickerView
                    android:id="@+id/month_pv"
                    android:layout_width="0dp"
                    android:layout_height="160dp"
                    android:layout_weight="2"
                    app:isLoop="false" /> 
```            
>TimeSelector时间控件整体设置是否循环显示内容
在show()前调用：
        
```java  timeSelector.setIsLoop(false);//不设置时为true，即循环显示 ```



