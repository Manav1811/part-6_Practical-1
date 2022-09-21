# part-6_Practical-1

package part6;
import java.util.*;
	class MyThread implements Runnable {
	    private Practical_1 sync;
	    private String s;

	    public MyThread(Practical_1 sync, String s) {
	        this.sync = sync;
	        this.s = s;
	    }

	    public static void pause(long time) {
	        try {Thread.sleep(time); }
	        catch (InterruptedException e) {Thread.currentThread().interrupt();}
	    }
	    public void run() {
	        synchronized (sync) 
	        {
	         sync.print(s);
	        }
	    }
	}

	public class Practical_1 {

	    public void print(String s) {
	        System.out.println(s);
	        MyThread.pause(200);
	    }

	    public static void main(String[] args) {
	    	Practical_1 sync = new Practical_1();
	    	 System.out.println("This is created by 21CE063_Manav Luhar");
	        MyThread st1 = new MyThread(sync, "Hello");
	        MyThread st2 = new MyThread(sync, "World");

	        Thread t1 = new Thread(st1);
	        Thread t2 = new Thread(st2);

	        t1.start();
	        t2.start();
	       
	    }
	
	}

