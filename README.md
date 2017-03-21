# Pinview
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-Pinview-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/5394)
[![Release](https://jitpack.io/v/GoodieBag/Pinview.svg)](https://jitpack.io/#GoodieBag/Pinview)
[![API](https://img.shields.io/badge/API-15%2B-blue.svg?style=flat)](https://android-arsenal.com/api?level=15)

 针对Android的Pinview库 :pouting_cat:
 
![alt tag](https://media.giphy.com/media/U5BP5gk9zQaqs/giphy.gif)       ![alt_tag](https://media.giphy.com/media/CnCvLh9NT6Hio/giphy.gif)

## Gradle 依赖
将其添加到存储库末尾的 root build.gradle 文件中:
```java
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```
添加依赖关系 : 
```java
dependencies {
	   compile 'com.github.GoodieBag:Pinview:v1.3'
	}
```
就这样同步 gradle:+1:

### 特征 : 
 * Flawless focus change to the consecutive pin box when the text is entered/deleted.//文本输入/删除时，无缝对焦更改为连续的针脚框。
 * When the user taps on the Pinview, the first empty box available is focused automatically (when the cursor is hidden).//当用户点击Pinview时，可以自动对焦第一个空盒子（当光标被隐藏时）
 * Listeners for onDataEntered ( To call an API when the pin is entered) and touch exists.//onDataEntered的侦听器（当输入引脚时调用API），触摸存在
 * Customisations are available for pin box sizes, background(drawables, selectors), inputType etc.//定制可用于针盒尺寸，背景（可绘图，选择器），inputType等。
 
## 用法

### XML : 
```xml
<com.goodiebag.pinview.Pinview
        android:id="@+id/pinview"
        app:pinBackground="@drawable/example_drawable"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:pinWidth="40dp"
        app:pinHeight="40dp"
        app:pinLength="4"
        app:cursorVisible="false"
		app:forceKeyboard="true"
        app:hint="0"
        app:inputType="text"
        app:password="false"/>
```
这可以通过```findViewById```方法在java类中引用

##### 可用的xml属性和解释 : 

```app:pinBackground``` : Sets the pin box's background, accepts a drawable or a selector drawable. When a ```selector``` is used, the focused pin box is highlighted. //设置pin box's的背景，接受可绘制或可选择的绘制。当使用```selector```时，会突出显示对焦的针框<br />
```app:pinWidth``` and ```app:pinHeight``` : Sets the width and height of the pinbox.//设置pinbox的宽度和高度。 <br />
```app:pinLength``` : number of pin boxes to be displayed.//要显示的pin boxes数<br />
```app:forceKeyboard``` : forces the keyboard when the pinview is activity/fragment is opened.//当pinview是活动/片段被打开时强制键盘
```app:cursorVisibility``` : Toggles cursor visibility.//切换光标可见性。<br />
```app:hint``` : Pin box hint. <br />
```app:inputType``` : 接受 ```number``` 或 ```text``` 值. <br />
```app:password``` : 当为正确时，pin value是```*```. <br />
```app:splitWidth``` : Determines the width between two pin boxes//确定两个针盒之间的宽度.

### Java : 

以编程方式创建视图 : 
```java
Pinview pin = new Pinview(this);
```
或者从findViewById引用它
```java
pin = (Pinview) findViewById(R.id.pinview);
pin.setPinBackgroundRes(R.drawable.sample_background);
pin.setPinHeight(40);
pin.setPinWidth(40);
pin.setInputType(Pinview.InputType.NUMBER);
pin.setValue("1234");
myLayout.addView(pin);    
```
##### To get and set the pin values use the ```pin.getValue()``` and ```pin.setValue()``` methods respectively.//获取并设置引脚值分别使用```pin.getValue（）``和```pin.setValue（）```方法。

There is an event listener which is triggered when the user is done entering the otp which can be used as follows : //有一个事件监听器，当用户完成输入可以使用的otp时被触发
```java
pinview.setPinViewEventListener(new Pinview.PinViewEventListener() {
            @Override
            public void onDataEntered(Pinview pinview, boolean fromUser) {
	    	//Make api calls here or what not
                Toast.makeText(MainActivity.this, pinview.getValue(), Toast.LENGTH_SHORT).show();
            }
        });
```
#### Note : 
此库不能放心使用第三方键盘（特别是当光标关闭时）。它的工作原理如谷歌键盘。 我们将在以后的版本中增加一些解决方案。

## LICENSE
```
MIT License

Copyright (c) 2017 GoodieBag

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```


