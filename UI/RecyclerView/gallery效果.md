##### 如何实现类似画廊效果，即滑动到中间的item突出显示，并且盖住两边的item，大致效果如下：
![效果图](https://github.com/wenjiangit/AndroidNotes/tree/master/UI/source/gallery.gif)

###### 实现方案
1. 重写`RecyclerView.LayoutManger`实现自定义布局，并根据距离中间的距离实现缩放效果。
参考[Android Carousel LayoutManager for RecyclerView](https://github.com/Azoft/CarouselLayoutManager)

###### 遇见问题

> 当某个`item`滑动中间时，需要更新相关ui元素，在调用`adapter`的`notifyDataSetChanged`时会造成界面滑动的不流畅。

###### 如何优化？


```
  mAdapter.notifyItemRangeChanged(0, mAdapter.getItemCount());
   //清除RecyclerView item的默认动画
  ((SimpleItemAnimator)mRecycler.getItemAnimator()).setSupportsChangeAnimations(false);
```
###### 原因分析
- `notifyDataSetChanged`


> this event does not specify what about the data set has changed, forcing
any observers to assume that all existing items and structure may no longer be valid.
LayoutManagers will be forced to fully rebind and relayout all visible views.


官方说明当调用这个方法时会重新绑定数据并且刷新布局。因此当中间`item`还未到达正中间时调用此方法会重新`layout`，导致界面不流畅。


- `notifyItemRangeChanged`

> This is an item change event, not a structural change event. It indicates that
         any reflection of the data in the given position range is out of date and should
         be updated. The items in the given range retain the same identity.

调用这个方法同样能达到刷新数据的作用，但不会重新布局，同时需要清除`item`变更自带的动画效果。


---
##### 替代方案

[FancyCoverFlow](https://github.com/davidschreiber/FancyCoverFlow)

可以通过设置相关参数达到更细致的显示效果，未仔细研究。