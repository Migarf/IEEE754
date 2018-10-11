import java.util.Scanner;
import java.util.Locale;
import java.lang.Math;
public class faw {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner sc = new Scanner(System.in).useLocale(Locale.US);

		while (true) {
			float l = sc.nextFloat();
			System.out.println("Znak " + Znak(l));
			System.out.println("Expan " + Expan(l));
			System.out.println("Mantiss " + Mantiss(l));
			System.out.println("Number " + Znak(l) + Expan(l) + Mantiss(l));
			
		}	
	}
	public static String Expan(float g) {
		if (g == 0) {
			return "00000000";
		}
		else {
			String h = NoExpan(g);
			long b = h.length() - 1;
			long x = 127 + b;
			String s = NoExpan(x);
			int z = s.length();
			for (int i = 0; i < (8 - z); i++) {
				s = "0" + s;
			}
			
		    return s;
		}
	}
	public static String Znak(float v) {
	    String z;
	    if (v == 0) {
	    	if (v * (-0) == 0) {
	    		return "1";	    	
	    	}
	    	else {
	    		return "0";	    	
	    	}
	    }
	    else if (v < 0) {
			z = "1";
			return z;
		}
		else {
			z = "0";
			return z;
		}
	    
	}
	public static long abs(long i) {
		if (i < 0) {
			return (i * (-1));
		}
		else {
			return (i* 1);
		}
		
	}
	public static String Mantiss(float l) {
	    String h = NoExpan(l);
		int b = h.length();
		float f = l % 1;
		Integer n = 0;
		String k = h;
		for (int i = 0; i < (24 - b); i++) {
			f = f * 2;
			n = (int) abs((long)(f / 1));
			f = f % 1;
			k = k + n.toString().substring(0, 1);
			
		}
		
		return(k.substring(1, 24));
	}
	public static String NoExpan(float g) {
		String f;
		if (g % 2 != 0) {
			f = "1";
		}
		else {
			f = "0";
		}
		long j = 0;
		long c = (long) g;
		while (c != 0){
			c = abs(c / 2);
			j = abs(c % 2);
			String h = (String) f;
			f = h + String.valueOf(j);
		}
		StringBuffer d = new StringBuffer(f);
	    d.reverse();
	    
	    String v = new String(d);
	    int h = v.length();
	    return v.substring(1,  h);
	}
	
}

