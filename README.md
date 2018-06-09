# CanvasDemo
Youtube Android project by Simplilearn

CanvasDemo.java

package com.example.david.canvasdemo;

import android.app.ActionBar;
import android.content.Context;
import android.graphics.Bitmap;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.MotionEvent;
import android.view.SoundEffectConstants;
import android.view.View;
import android.view.ViewGroup;






   
   
   
   
   
   private Bitmap bitmap;
    private float x;
    private float y;

class CanvasDemo extends AppCompatActivity implements View.OnTouchListener {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_canvas_demo);

       
        MyCanvas myCanvas = new MyCanvas(this);

     
        ViewGroup.LayoutParams layoutParams = new ViewGroup.LayoutParams(ViewGroup.LayoutParams.FILL_PARENT, ViewGroup.LayoutParams.FILL_PARENT);
        addContentView(myCanvas, layoutParams); 
   
        myCanvas.setOnTouchListener(this);
       
        myCanvas.setDrawingCacheEnabled(true);
      
        bitmap = myCanvas.getDrawingCache();

    }


    @Override
    public boolean onTouch(View v, MotionEvent event) {

      
            x = event.getX();   
            y = event.getY();

            bitmap = v.getDrawingCache();
            v.invalidate();
            return true;
    }

 
    private class MyCanvas extends View{
        public MyCanvas(Context context){   
            super(context);

        }

     
        @Override
        public void draw(Canvas canvas) {
            super.draw(canvas);

            Paint paint = new Paint();    
            paint.setColor(Color.YELLOW);
            paint.setStrokeWidth(50);

         
            if(bitmap != null){
                bitmap.setPixel((int)x,(int)y, Color.BLUE); 
             
                canvas.drawBitmap(bitmap, x, y, paint);
            }
        }
    }

}
