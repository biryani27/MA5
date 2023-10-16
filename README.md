# MA5

MAINACTVITY.java

package com.example.lab5;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
public class MainActivity extends AppCompatActivity {
    EditText lname,fname,uname,pwd,cpwd,mail,msg;
    Button reg;
    boolean flag;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        fname=(EditText)findViewById(R.id.fname);
        lname=(EditText)findViewById(R.id.lname);
        uname=(EditText)findViewById(R.id.uname);
        pwd=(EditText)findViewById(R.id.pwd);
        cpwd=(EditText)findViewById(R.id.cpwd);
        mail=(EditText)findViewById(R.id.mail);
        reg=(Button)findViewById(R.id.breg);
        reg.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                flag=true;
                if (fname.getText().toString().length() == 0) {
                    fname.setError("Fname not entered by the user"); fname.requestFocus();
                    flag=false;
                }
                if (lname.getText().toString().length() == 0) {
                    lname.setError("Lname not entered by the user");
                    lname.requestFocus();
                    flag=false;
                }
                if (uname.getText().toString().length() == 0) { uname.setError("User name notentered by the user");
                        uname.requestFocus();
                    flag=false;
                }
                if (mail.getText().toString().length() == 0) {
                    pwd.setError("Emailid not entered");
                    pwd.requestFocus();
                    flag=false;
                }
                if (pwd.getText().toString().length() < 8) {
                    pwd.setError("password should be atleast 8 characters");
                    pwd.requestFocus();
                    flag=false;
                }
                if (!pwd.getText().toString().equals(cpwd.getText().toString())) {
                    cpwd.setError("Re-entered password do not match");
                    cpwd.requestFocus();
                    flag=false;
                }
                if(flag==true) {
                    Intent i = new Intent(getApplicationContext(),second.class);
                }
            }
        });
        Bundle b = new Bundle();
        b.putString("namef", fname.getText().toString());
        b.putString("namel", lname.getText().toString());
        Intent i = null;
        i.putExtras(b);
        startActivity(i);
    }
}

second.java

package com.example.lab5;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.TextView;
public class second extends AppCompatActivity { TextView t;
    String fname, lname,msg;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);
        t=(TextView)findViewById(R.id.msg2);
        Bundle b =getIntent().getExtras(); fname=b.getString("namef");
        lname=b.getString("namel"); msg="Welcome" + fname + " " + lname;
        t.setText(msg);
    }
}

ACtivity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<TableLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:background="#E6DDA6" tools:context=".MainActivity">
    <TableRow>
        <TextView android:text="Registration Form"
            android:layout_width="match_parent" android:textAllCaps="true"
            android:layout_height="60dp">
        </TextView>
    </TableRow>
    <TableRow>
        <TextView
            android:text="Enter Firstname" android:layout_width="wrap_content"
            android:layout_height="60dp">
        </TextView>
        <EditText android:id="@+id/fname" android:singleLine="true"
            android:layout_width="wrap_content" android:layout_height="60dp">
        </EditText>
    </TableRow>
    <TableRow>
        <TextView
            android:text="Enter Lastname"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </TextView>
        <EditText android:id="@+id/lname"
            android:layout_width="wrap_content" android:layout_height="60dp">
        </EditText>
    </TableRow>
    <TableRow>
        <TextView
            android:text="Enter Username"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </TextView>
        <EditText android:id="@+id/uname"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </EditText>
    </TableRow>
    <TableRow>
        <TextView
            android:text="Enter Password"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </TextView>
        <EditText android:id="@+id/pwd"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </EditText>
    </TableRow>
    <TableRow>
        <TextView
            android:text="Re-Enter Password"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </TextView>
        <EditText android:id="@+id/cpwd"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </EditText>
    </TableRow>
    <TableRow>
        <TextView
            android:text="Enter Emailid"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </TextView>
        <EditText android:id="@+id/mail"
            android:layout_width="wrap_content"
            android:layout_height="60dp">
        </EditText>
    </TableRow>
    <TableRow>
        <Button
            android:id="@+id/breg"
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:text="Register"></Button>
    </TableRow>
</TableLayout>

activity_second.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/msg2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Welcome"
        android:textSize="24sp"
        android:layout_gravity="center"/>

</LinearLayout>

