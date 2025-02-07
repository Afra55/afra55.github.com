---
layout: post
title:  "属性动画"
date:   2016-2-22 11:26
categories: Android
comments: true
description: 属性动画
---

* content
{:toc}

# 对 Object 的属性 xxx 进行动画的条件

1. object 必须提供 setXxx 和 getXxx 方法。
2. object 的 setXxx 方法对 属性 xxx 的改变需要有明确的视图变化，比如变宽或变高。

# 针对动画不生效的解决方法

## 给对象加上 get 和 set 方法

   一般情况下只能对自定义view进行这个操作。

## 使用帮助类间接提供 get 和 set 方法

示例仅面向宽的动画，更多属性动画仿照即可。5s内让view的宽度增加到500px。

### 图形帮助类

	public class ViewHelper {

	    private View view;
	
	    public ViewHelper(View view) {
	        this.view = view;
	    }
	
	    public int getWidth() {
	        return view.getLayoutParams().width;
	    }
	
	    public void setWidth(int width) {
	        view.getLayoutParams().width = width;
	        view.requestLayout();
	    }

	}

### 使用方法

	public void use(View view) {
        ViewHelper viewHelper = new ViewHelper(view);
        ObjectAnimator.ofInt(viewHelper, "width", 500).setDuration(5000).start();
    }

## 使用 ValueAnimator

	public void use(final View view) {
        ValueAnimator valueAnimator = ValueAnimator.ofInt(1, 100);
        valueAnimator.addUpdateListener(new ValueAnimator.AnimatorUpdateListener() {
            private IntEvaluator intEvaluator = new IntEvaluator();
            @Override
            public void onAnimationUpdate(ValueAnimator animation) {
                
                /* 当前动画的进度，在1-100之间*/
                int currentValue = (int) animation.getAnimatedValue();

                /* 当前动画进度占整个动画的比例 */
                float fraction = animation.getAnimatedFraction();
                view.getLayoutParams().width = intEvaluator.evaluate(fraction, view.getWidth(), 500);
            }
        });
		valueAnimator.setDuration(5000).start();
    }

# 注意事项

1. OOM问题：避免使用帧动画；
2. 内存泄漏：无限循环的属性动画需要有停止操作；
3. 兼容性：3.0以下的动画有兼容问题。
4. View动画：View动画只是对View的影响做动画，并不能真正改变view的状态，所以有时候会出现View动画结束后View无法隐藏的现象（setVisibility（View.Gone）失效），此时调用view.clearAnimation即可。
5. 使用dp，不能使用px。
6. 动画过程中，建议开启硬件加速。