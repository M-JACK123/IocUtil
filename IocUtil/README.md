# IocUtil
一个使用ioc原理简化findviewbyid和点击事件的框架
使用方法
package com.cplus.myapplication;

import android.os.Bundle;
import android.support.design.widget.FloatingActionButton;
import android.support.design.widget.Snackbar;
import android.support.v7.app.AppCompatActivity;
import android.support.v7.widget.Toolbar;
import android.view.View;
import android.view.Menu;
import android.view.MenuItem;
import android.widget.TextView;
import android.widget.Toast;

@ContentView(R.layout.activity_main)
public class MainActivity extends AppCompatActivity {

    @ViewInject(R.id.tv_text1)
    private TextView mTextView;

    @OnClick({R.id.button})
    public void onClick(View view) {
        Toast.makeText(this, "按下", Toast.LENGTH_SHORT).show();
    }

    @OnLongClick({R.id.button})
    public boolean onLongClick(View view) {
        Toast.makeText(this, "长按", Toast.LENGTH_SHORT).show();
        return true;
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        ViewInjectUtils.inject(this);
        mTextView.setText("inject");
    }
}
