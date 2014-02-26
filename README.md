WECARTOON_PROGRAM
=================

/*its a program of applet using java ie core java its a kind of animation its just like a car racing game using applet in java 
*/
import java.awt.*;
import java.util.*;
import java.applet.*;
/*
 <APPLET CODE="Animation.JAVA" WIDTH=400 HEIGHT=300>
 </APPLET>
*/
//The basic applet class.The applet shows 4 cars crossing each other at a square.
public class Animation extends Applet implements Runnable
{
 Thread t;
 //4 variables used to vary the car's positions.
 int x1=0,x2=380,y1=50,y2=250;
 public void start()
 {
  if(t==null)
  {
   t=new Thread(this,"New Thread");//New side Thread created on start of applet.
   t.start();
  }
 }
 public void stop()
 {
  if(t!=null)
  {
   t=null;//On stop of applet the created thread is destroyed.
  }
 }
 //Implementation of method run() of Runnable interface.
 public void run()
 {
  Thread t1=Thread.currentThread();
  while(t==t1)
  {
   repaint();
   try
   {
    Thread.sleep(100);
   }
   catch(Exception e)
   {   }
  }
 }
 public void paint(Graphics g)
 {
  setBackground(Color.cyan);
  g.setColor(Color.BLACK);
  x1=(x1+16)%400;
  x2=x2-16;
  y1=(y1+12)%300;
  y2=y2-12;
  if(y2<0)
   y2=288;
  if(x2<0)
   x2=384;
  //Draw the roads using 2 filled rectangles using black color.
  g.fillRect(0,130,400,40);
  g.fillRect(180,0,40,305);
  //Draw the white colored lines.
  g.setColor(Color.white);
  for(int i=0;i<20;i++)
  {
   if(i!=9 && i!=10)
    g.drawLine(i*20,150,i*20+10,150);
  }
  for(int j=0;j<15;j++)
  {
   if(j!=7 && j!=8)
    g.drawLine(200,j*20,200,j*20+10);
  }
  //Draw 4 colored cars using filled round rectangles.
  g.setColor(Color.red);
  g.fillRoundRect(x2,152,20,8,2,2);
  g.fillRoundRect(x1,140,20,8,2,2);
  g.fillRoundRect(190,y1,8,20,2,2);
  g.fillRoundRect(202,y2,8,20,2,2);
 }
}
