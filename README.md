# sms_verification_code
###  要实现的功能

> Android 应用发送验证码倒计时效果和自动获取验证码并填充到输入框



### 1 书写布局

#### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/activity_main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context="com.cheng.smsverificationcode.MainActivity">

    <!--手机快速注册-->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@android:color/holo_red_light"
        android:gravity="center"
        android:paddingBottom="10dp"
        android:paddingTop="10dp"
        android:text="手机快速注册"
        android:textColor="@android:color/white"
        android:textSize="22sp" />

    <!--手机 hint-->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:layout_marginLeft="15dp"
        android:layout_marginRight="15dp"
        android:layout_marginTop="20dp"
        android:background="@drawable/update_password_item_bg_top"
        android:gravity="center_vertical"
        android:orientation="horizontal">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:paddingLeft="3dp"
            android:text="手\t机:"
            android:textSize="16sp" />

        <!--
        android:inputType="number"  限定输入类型为 数字
        android:maxLength="11"  输入的数字的最大长度是 11
        -->
        <EditText
            android:id="@+id/edit_phone_user"
            android:layout_width="1px"
            android:layout_height="match_parent"
            android:layout_marginLeft="3dp"
            android:layout_weight="3"
            android:background="@android:color/white"
            android:hint="请输入您的手机号码"
            android:inputType="number"
            android:maxLength="11"
            android:singleLine="true"
            android:textColor="#555555"
            android:textSize="16sp" />
    </LinearLayout>
    <!--密码、中间、按钮（控制输入时显示/隐藏密码） -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:layout_marginLeft="15dp"
        android:layout_marginRight="15dp"
        android:layout_marginTop="20dp"
        android:background="@drawable/update_password_item_bg_middle"
        android:gravity="center_vertical"
        android:orientation="horizontal">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:paddingLeft="3dp"
            android:text="密\t码:"
            android:textSize="16sp" />

        <EditText
            android:id="@+id/edit_phone_pwd"
            android:layout_width="1px"
            android:layout_height="match_parent"
            android:layout_marginLeft="3dp"
            android:layout_weight="3"
            android:background="@android:color/white"
            android:hint="6-20位字符，不能使用空格"
            android:inputType="textPassword"
            android:maxLength="20"
            android:paddingLeft="5dp"
            android:singleLine="true"
            android:textColor="#555555"
            android:textSize="16sp" />
        <!--按钮（控制输入时显示/隐藏密码）-->
        <Button
            android:id="@+id/btn_register_show_password"
            android:layout_width="45dp"
            android:layout_height="30dp"
            android:layout_marginRight="3dp"
            android:background="@drawable/selector_btn_verification_code"
            android:text="显示"
            android:textSize="14sp" />

    </LinearLayout>
    <!--验证码-->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:layout_marginLeft="15dp"
        android:layout_marginRight="15dp"
        android:layout_marginTop="20dp"
        android:background="@drawable/update_password_item_bg_bottom"
        android:gravity="center_vertical"
        android:orientation="horizontal">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:paddingLeft="3dp"
            android:text="验证码:"
            android:textSize="16sp" />

        <EditText
            android:layout_width="1px"
            android:layout_height="match_parent"
            android:layout_marginLeft="3dp"
            android:layout_weight="3"
            android:background="@android:color/white"
            android:hint="请输入验证码"
            android:inputType="number"
            android:maxLength="11"
            android:singleLine="true"
            android:textColor="#555555"
            android:textSize="16sp" />
        <Button
            android:singleLine="true"
            android:id="@+id/btn_verification_code"
            android:layout_width="90dp"
            android:layout_height="35dp"
            android:layout_marginRight="3dp"
            android:background="@drawable/selector_btn_verification_code"
            android:text="获取验证码"
            android:textSize="14sp" />
    </LinearLayout>


    <!--可以勾选的协议-->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_gravity="center_vertical"
        android:layout_marginTop="10dp"
        android:orientation="horizontal">

        <CheckBox
            android:id="@+id/register_chkphone_enoughAge"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginLeft="15dp"
            android:checked="true"
            android:text="我已经年满18岁并同意"
            android:textColor="#555555"
            android:textSize="12sp" />


        <TextView
            android:id="@+id/register_txt_treaty"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="《用户注册协议》"
            android:textColor="#ff0055ff"
            android:textSize="12sp" />
    </LinearLayout>

    <!--注册-->
    <Button
        android:id="@+id/register_phone"
        android:layout_width="match_parent"
        android:layout_height="45dp"
        android:layout_marginLeft="15dp"
        android:layout_marginRight="15dp"
        android:layout_marginTop="10dp"
        android:background="@android:color/holo_red_dark"
        android:text="注\t册"
        android:textColor="#ffffff"
        android:textSize="22sp" />
    <!--免手机注册-->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:gravity="center_horizontal|bottom"
        android:orientation="horizontal">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginBottom="20dp"
            android:text="免手机注册"
            android:textSize="16sp" />
    </LinearLayout>

</LinearLayout>
```



#### drawable/selector_btn_verification_code.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@drawable/yanzhengma_pressed" android:state_selected="true" />
    <item android:drawable="@drawable/yanzhengma_pressed" android:state_pressed="true" />
    <item android:drawable="@drawable/yanzhengma_pressed" android:state_focused="true" />
    <item android:drawable="@drawable/yanzhengma_normal" />
</selector>
```

