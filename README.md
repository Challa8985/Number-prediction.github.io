# Number-prediction.github.io
Number prediction application for the users
package com.example.numberpredictor

import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val predictButton: Button = findViewById(R.id.btn_predict)
        val userInput: TextView = findViewById(R.id.input_number)
        val resultText: TextView = findViewById(R.id.result_text)

        predictButton.setOnClickListener {
            val userNumber = userInput.text.toString().toIntOrNull()

            if (userNumber == null || userNumber !in 0..9) {
                Toast.makeText(this, "Enter a number between 0 and 9", Toast.LENGTH_SHORT).show()
                return@setOnClickListener
            }

            val randomNumber = (0..9).random()
            if (userNumber == randomNumber) {
                resultText.text = "Correct! The number was $randomNumber."
            } else {
                resultText.text = "Wrong! The number was $randomNumber."
            }
        }
    }
}
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/input_number"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter a number (0-9)"
        android:inputType="number" />

    <Button
        android:id="@+id/btn_predict"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Predict" />

    <TextView
        android:id="@+id/result_text"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text=""
        android:textSize="18sp"
        android:paddingTop="16dp" />
</LinearLayout>
