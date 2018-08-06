# FlowLayout的一个Demo

## 在activity_main中添加布局

```java
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context=".MainActivity">

    <com.nex3z.flowlayout.FlowLayout
        android:id="@+id/flow"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:flChildSpacing="auto"
        app:flChildSpacingForLastRow="align"
        app:flRowSpacing="8dp"/>
</LinearLayout>
```

## 在MainActivity中调用

```java
public class MainActivity extends AppCompatActivity {

    com.nex3z.flowlayout.FlowLayout  flowLayout;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        flowLayout = (FlowLayout)findViewById(R.id.flow);
        for (int i = 0; i < 37; i++) {
            CheckBox checkBox = new CheckBox(this);
            if(i%7==0){
                checkBox.setText("那");
            }else if(i%7==1){
                checkBox.setText("是一");
            }else if(i%7==2){
                checkBox.setText("条神奇");
            }else if(i%7==3){
                checkBox.setText("的天路喂");
            }else if(i%7==4){
                checkBox.setText("带我们走向");
            }else if(i%7==5){
                checkBox.setText("人间天堂,青棵");
            }else{
                checkBox.setText("酒酥油茶,会更加香甜");
            }
            checkBox.setTag(i);
            checkBox.setButtonDrawable(new ColorDrawable());
            checkBox.setBackgroundResource(R.drawable.bg_shape_green);
            checkBox.setTextColor(getResources().getColorStateList(R.color.selector_text_color));
            checkBox.setPadding(18, 10, 18, 10);
            checkBox.setChecked(false);

            LinearLayout.LayoutParams params = new LinearLayout.LayoutParams(LinearLayout.LayoutParams.WRAP_CONTENT, LinearLayout.LayoutParams.WRAP_CONTENT);
            params.setMargins(10, 10, 10, 10);
            checkBox.setLayoutParams(params);

            checkBox.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
                @Override
                public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
                    if (isChecked) {
                        Toast.makeText(MainActivity.this,"选中第"+(int)buttonView.getTag()+"个",Toast.LENGTH_SHORT).show();
                    } else {
                        Toast.makeText(MainActivity.this,"删除第"+(int)buttonView.getTag()+"个",Toast.LENGTH_SHORT).show();
                    }
                }
            });
            flowLayout.addView(checkBox);
        }
    }
}
```

![](http://images.wxyass.com/wxyass/images/20180806171459.png)

