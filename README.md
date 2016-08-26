# 快速检索(对View的自定义) 

1. 应用场景: 微信好友列表, 联系人通讯录, 应用管理, 文件管理
2. 功能实现:

   >  1. ViewDragHelper: Google2013年IO大会提出的,
   >   解决界面控件拖拽移动问题. (v4包下)
   >  2. mTouchSlop 最小敏感范围, 值越小, 越敏感

3. 实现逻辑:


   > 1.右边是自定义QuickIndexBar,它能获取触摸它的时候当前所触摸到的字母;
   
   > 绘制文本x坐标: width/2;
   
   > 绘制文本y坐标: 格子高度的一半 + 文本高度的一半 + position*格子高度
   
   > 计算触摸点对应的字母:根据触摸点的y坐标除以cellHeight,得到的值就是字母对应的索引;
   
   > 2.左边是listview，它根据当前触摸的字母，去自己列表找首字母和触摸字母相同的那个
   
   > item，然后让item放置到屏幕顶端(setSelection(position));
   
   > 3.需要用到获取汉字的拼音,借助类库pinyin4j.jar实现;
   
4. 实现效果：

![](/image/1.png)

![](/image/2.png)
