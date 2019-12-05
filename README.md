    # ScreenOrientationJava

    package com.redudantdev8.screenorientationjava;

    import androidx.annotation.NonNull;
    import androidx.appcompat.app.AppCompatActivity;

    import android.app.Activity;
    import android.content.res.Configuration;
    import android.os.Bundle;
    import android.os.PersistableBundle;
    import android.util.Log;
    import android.view.View;
    import android.widget.Button;
    import android.widget.EditText;
    import android.widget.TextView;
    import android.widget.Toast;

    public class MainActivity extends Activity {

      private static final String TAG = "MainActivity";

      private TextView tv_Message;
      private EditText et_Name;
      private Button btn_Submit;

      private final String KEY_NAME = "massage";
      private final String KEY_BTN = "brn_text";

      @Override
      protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        tv_Message = (TextView) findViewById(R.id.tvMessage);
        et_Name = (EditText) findViewById(R.id.etName);
        btn_Submit = (Button) findViewById(R.id.btnSubmit);

        btn_Submit.setOnClickListener(new View.OnClickListener() {
          @Override
          public void onClick(View view) {

            tv_Message.setText("Welcome " + et_Name.getText().toString());
            btn_Submit.setText("LOGOUT");
          }
        });
      }

      //start lifecycle Screen orientation
      /*untuk melakukan orientasi di anjurkan menggunakan mthod onSaveInstanceState dan onRestoreInstanceState*/
    //	@Override
    //	protected void onRestoreInstanceState(@NonNull Bundle savedInstanceState) {
    //		super.onRestoreInstanceState(savedInstanceState);
    //		Log.i(TAG, "onRestoreInstanceState: ");
    //
    //		if (savedInstanceState != null) {
    //			tv_Message.setText(savedInstanceState.getString(KEY_BTN));
    //			btn_Submit.setText(savedInstanceState.getString(KEY_NAME));
    //		}
    //	}
    //
    //	@Override
    //	public void onSaveInstanceState(@NonNull Bundle outState, @NonNull PersistableBundle outPersistentState) {
    //		super.onSaveInstanceState(outState, outPersistentState);
    //		Log.i(TAG, "onSaveInstanceState: ");
    //
    //		outState.putString(KEY_NAME, tv_Message.getText().toString());
    //		outState.putString(KEY_BTN, tv_Message.getText().toString());
    //	}

      @Override
      protected void onRestart() {
        super.onRestart();
        Log.i(TAG, "onRestart: ");
      }

      @Override
      protected void onStart() {
        super.onStart();
        Log.i(TAG, "onStart: ");
      }

      @Override
      protected void onResume() {
        super.onResume();
        Log.i(TAG, "onResume: ");
      }

      @Override
      protected void onPause() {
        super.onPause();
        Log.i(TAG, "onPause: ");
      }

      @Override
      protected void onStop() {
        super.onStop();
        Log.i(TAG, "onStop: ");
      }

      @Override
      protected void onDestroy() {
        super.onDestroy();
        Log.i(TAG, "onDestroy: ");
      }
      //end lifecycle

      /*kita bisa menggunakan screen orientasi menggunakan method onConfigurationChanged
      dengan menambahkan kode dibawah ini pada manifest
      <activity android:name=".MainActivity"
          android:configChanges="orientation|screenSize">
      * akan tetapi tidak di sarankan bahkan melenceng dari aturan*/
      @Override
      public void onConfigurationChanged(@NonNull Configuration newConfig) {
        super.onConfigurationChanged(newConfig);
        Log.i(TAG, "onConfigurationChanged: ");

        if (newConfig.orientation == Configuration.ORIENTATION_PORTRAIT) {

          Toast.makeText(this, "portrait", Toast.LENGTH_SHORT).show();

        } else if (newConfig.orientation == Configuration.ORIENTATION_LANDSCAPE) {

          Toast.makeText(this, "landscap", Toast.LENGTH_SHORT).show();

        }
      }
    }
