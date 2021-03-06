# Android Final Group Project Report 

### 小组成员：	17301127 李朴 

### 					   17301138 唐麒 

### 					   17301145 张钰铎

### 					   17301145 郑栩侗



## 一、报告概述

本报告展示安卓最终大项目的全部界面并介绍实现功能及部分技术细节。

**项目特色 项目采用Kotlin语言及MVVM的模式进行开发**



## 二、需求实现情况一览





## 三、详细设计说明

PS: 该部分以功能设计介绍为主，部分任务需求的实现说明请看`四、部分需求实现说明`。

### 3.1 引导页

<div align="center"><img src="http://static.zybuluo.com/TangWill/i1adjfar6f75duveyzaceztv/uoko_guide_background_1.jpg" alt="11" width="25%" height="25%" />   <img src="http://static.zybuluo.com/TangWill/1000405oowog8zg84lp8vhtz/uoko_guide_background_2.jpg" alt="12" width="25%" height="25%" />    <img src="http://static.zybuluo.com/TangWill/l3iwqc6b4qb16lmi079qirm1/uoko_guide_background_3.jpg" alt="09" width="25%" height="25%" />  </div>


### 3.2 登录界面
<div align="center"><img src="http://static.zybuluo.com/TangWill/119sezonqj00oz8grx4fhie6/Screenshot_20200105-212344.jpg" alt="01" width="25%" height="25%" /></div>


+ 我们的登录界面实现了第三方登录，图中展示了微信、QQ、微博的登录选择，但实际上我们只实现了QQ第三方登录的功能。

+ 输入密码时，如果密码输入格式不符合要求（不到5个字符），会有警告提示。
+ 当密码符合要求时，用户点击登录按钮，所输入数据将与数据库中的数据进行匹配，如果成功匹配，则跳转至***主页***，如果无法成功匹配，则登录失败,在本项目中，当需要请求网络资源时，采用模拟模态对话框的方式禁止用户在长时间加载数据时点击界面造成假死现象。

如下图所示：

<div align="center"><img src="http://static.zybuluo.com/TangWill/9m7nxhj5fwr1y11xjq2n4r24/Screenshot_20200106-010743.jpg" alt="07" width="25%" height="25%" />   <img src="http://static.zybuluo.com/TangWill/d40omh25von8oe1de3wgj6wj/Screenshot_20200106-010721.jpg" alt="08" width="25%" height="25%" />  <img src="http://static.zybuluo.com/TangWill/4haweqqj85vrrewiedotx4y8/Screenshot_20200106-010732.jpg" alt="10" width="25%" height="25%" /></div>

### 3.3 主页
<div align="center"><img src="http://static.zybuluo.com/TangWill/rerhbumlz4a0t6jwaaaik33v/Screenshot_20200105-212510.jpg" alt="02" width="25%" height="25%" /></div>

+ 主页主要由四部分构成：
  + 顶端放置搜索栏，匹配字段对英文文章进行搜索。
  + 第二部分放置四个按键，用以跳转至不同功能。
  + 第三部分放置英文文章列表，此处使用RecycleView实现。点击文章跳转至文章阅读页面。
  + 底端放置导航栏
  
+ 导航栏中首页、签到、我的事实上是三个Fragment，三者在主Activity中切换显示。

  

### 3.4 签到页

<div align="center"><img src="http://static.zybuluo.com/TangWill/zitvk4pnbafsbo9xdj97j93h/Screenshot_20200105-170052.jpg" alt="03" width="25%" height="25%" /></div>



### 3.5 个人信息页面


<div align="center"><img src="http://static.zybuluo.com/TangWill/th4bniqii8ystg6ruf5ua22p/Screenshot_20200105-212520.jpg" alt="04" width="25%" height="25%" /></div>



### 3.6 背单词页面

<div align="center"><img src="http://tang5618.com/zip/word_recite.png" alt="05" width="25%" height="25%" /></div>

+ 底部按键用以选择用户记忆程度

  + ”认识“代表用户熟知，初次点击点击后该日不会重复出现该单词。

  + “模糊”代表用户记忆不牢固，初次点击后本单词将重复出现3次。

  + “不认识”即为字面意思，初次点击后单词将重复出现5次。

    

### 3.7 文章阅读页

<div align="center"><img src="http://tang5618.com/zip/article_main.jpg" alt="06" width="25%" height="25%" /></div>


+ 文章底部评论、点赞、收藏、调整字体功能及动画均已实现。



## 四、部分技术实现说明



### 4.1 某某功能

+ 某某功能之简介

```
public class SpUtil {

    static SharedPreferences prefs;

    public static void init(Context context) {
        prefs = PreferenceManager.getDefaultSharedPreferences(context);
    }

    /**
     * 获取登录状态
     * @param key
     * @return
     */
    public static boolean getBoolean(String key) {
        return prefs.getBoolean(key, false);
    }

    /**
     * 设置登录状态
     * @param key
     * @param data
     */
    public static void setBoolean(String key, boolean data) {
        prefs.edit().putBoolean(key, data).apply();
    }

}
```

