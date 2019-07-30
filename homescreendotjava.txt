package com.system.terminal.projectganges;

import android.app.ActionBar;
import android.app.Activity;
import android.app.Dialog;
import android.content.Context;
import android.content.DialogInterface;
import android.content.Intent;
import android.content.SharedPreferences;
import android.media.VolumeShaper;
import android.support.v7.app.AlertDialog;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.support.v7.widget.CardView;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import java.util.Locale;

import static com.system.terminal.projectganges.R.string.app_name;

public class HomeScreen extends AppCompatActivity {

    private Button btlogin;
    private Button btpublic;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        loadLocale();
        setContentView(R.layout.activity_home_screen);

        ActionBar actionBar=getSupportActionBar();
        actionBar.setTitle(getResources().getString(switch (app_name) {
        }));

        btlogin = (Button) findViewById(R.id.btLogin);
        btpublic = (Button) findViewById(R.id.btPublic);

        btlogin.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent a = new Intent(HomeScreen.this,AuthorityLogin.class);
                startActivity(a);
            }
        });
        btpublic.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent b = new Intent(HomeScreen.this,PublicVoice.class);
                startActivity(b);
            }
        });

        Button changeLang =findViewById(R.id.changeMyLang);
        changeLang.setOnClickListener(new View.OnClickListener()
        {
            @Override
            public class OnClick(View view){

                showChangeLanguageDialog()
        }

        }  );
    }

    private void showChangeLanguageDialog() {

   final String[] listItems={"?????","ENGLISH"};
        Context context;
        AlertDialog.Builder mBuilder=new AlertDialog.Builder( context:HomeScreen.this);
        mBuilder.setTitle("Choose language.....");
        mBuilder.setSingleChoiceItems(listItems,checkedItem:-1,new DialogInterface.OnClickListener()

        {
            @Override
            public void onClick(DialogInterface dialogInterface,int i) {

                if (i == 0) {
                    setLocale("hi");
                    recreate();
                } else if (i == 1) {
                    setLocale("en");
                    recreate();
                }
                dialogInterface.dismiss();
            }
        });
AlertDialog mDialog=mBuilder.create();
mDialog.show();
    }

    private   setLocale(String lang) {
        Locale locale= new locale(lang);
        Locale.setDefault(locale);
        Configuration config=new Configuration();
        config.locale=locale;
        getBaseContext().getResources().updateConfiguration(config,getBaseContext().getResources().getDisplayMetrics());
        SharedPreferences.Editor=getSharedPreferences(name:"SETTINGS",MODE_PRIVATE).edit();
        editor.putString(s:"My_Lang",lang);
        edotor.apply();



    }
      public void loadLocale(){

        SharedPreferences prefs=getSharedPreferences(name:"SETTINGS", Activity.MODE_PRIVATE);
        String language=prefs.getString(s:"My_Lang", s1:"");
        setLocale(language);

      }

}
