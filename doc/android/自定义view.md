在Android开发中，很多时候SDK提供的view并不能很好的满足我们的需求，这个时候我们就需要对view进行改造了，这就是自定义view。
自定义view的类型
1.组合控件
对现有的控件进行组合使用
2.继承现有的控件
继承现有的UI控件，如TextView,Button这些控件
3.继承view进行自定义
1）自定义属性
2）选择和设置构造方法
public class MyCustomView extends View {
    /**
     * 第一个构造函数
     */
    public MyCustomView(Context context) {
        this(context, null);
    }

    /**
     * 第二个构造函数
     */
    public MyCustomView(Context context, AttributeSet attrs) {
        this(context, attrs, 0);
    }

    /**
     * 第三个构造函数
     */
    public MyCustomView(Context context, AttributeSet attrs, int defStyle) {
        super(context, attrs, defStyle);
        // TODO:获取自定义属性
    }

    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
    }
}

3）重写onMeasure方法
4）重写onDraw方法
5）重写onLayout方法
6）重写其它事件方法（滑动监听）








