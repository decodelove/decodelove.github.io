---
layout: post
title:  "Android动态设置Button样式"
date:   2021-12-04 16:53:49
categories: Android
tags: Android
---
 &nbsp;&nbsp;最近接到一个需求,动态设置Button中的样式,可以通过server端下发配置读取创建新的Button控件,分析了一下需求是可以实现的,搞起~

    在这里记录一下,如下

 ```java
@SuppressLint("WrongConstant")
public void addButton(View view) {
    //首先创建一个Button控件
    Button button = new Button(this);
    button.setText("我是新增Button");
    button.setTextColor(Color.parseColor("#FFFFFF"));

    //Button点击按下样式风格设置
    StateListDrawable stateListDrawable = new StateListDrawable();

    //按下展示
    GradientDrawable pressed = new GradientDrawable();
    pressed.setColor(Color.parseColor("#AAAAAA"));
    pressed.setCornerRadius(15f);//设置圆角
    pressed.setGradientType(GradientDrawable.RECTANGLE);//设置矩形
    stateListDrawable.addState(new int[]{android.R.attr.state_pressed},pressed);

    //正常展示
    GradientDrawable normal = new GradientDrawable();
    normal.setColor(Color.parseColor("#FF6200EE"));
    normal.setCornerRadius(15f);//设置圆角
    normal.setGradientType(GradientDrawable.RECTANGLE);//设置矩形
    stateListDrawable.addState(new int[]{},normal);

    button.setBackground(stateListDrawable);

    //点击事件
    button.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Toast.makeText(MainActivity.this,"我是新增的Button点击事件!",Toast.LENGTH_SHORT).show();
        }
    });

    //然后添加到父控件里
    mLinearLayout.addView(button);
}
 ```






















[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
