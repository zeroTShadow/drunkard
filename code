# drunkard
general coding practice
import java.util.*;
import java.io.*;
public class drunkard
{
  static int store[]=new int[1001];
  public static void main(String arg[])
  {
    Scanner sc=new Scanner(System.in);
    while(sc.hasNext())
    {
      String first=sc.next();
      int m,n;
      long seed;
      if(first.equals("W"))
      {
        m=sc.nextInt();
        seed=sc.nextLong();
        walk(m,seed);
      }
      else
      {
        m=sc.nextInt();
        n=sc.nextInt();
        seed=sc.nextLong();
        histogram(m,n,seed);
      }
    }
  }
  public static long setup(int m,long seed, boolean first)
  {
    store[0]=0;
    for(int i=1;i<=m;i++)
    {
      if(!first)
        seed=(seed*16807)%2147483647;
      first = false;
      if(seed%2==1)
        store[i]=store[i-1]+1;
      else
        store[i]=store[i-1]-1;
    }
    return seed;
  }
  static void walk(int m,long seed)
  {
    System.out.println("W "+m+" "+seed);
    seed=setup(m,seed,true);
    for(int i=0;i<=m;i++)
    {
      for(int j=0;j<store[i]+35;j++)
        System.out.print(" ");
      System.out.println("*");
    }
  }
  static void histogram(int m,int n,long seed)
  {
    System.out.println("H "+m+" "+n+" "+seed);
    int positionHistogram[]=new int[m*2+1];
    for(int k=1;k<=n;k++)
    {
      if(k==1)
        seed=setup(m,seed,true);
      else
        seed=setup(m,seed,false);
      positionHistogram[store[m]+m]++;
    }
    for(int i=-m;i<=m;i+=2)
      System.out.printf("% 15d % 14d % 14.1f\n",i,positionHistogram[i+m],(2*n*Math.exp(-Math.pow(i,2)/(2*m))/Math.sqrt(2*Math.PI*m)));
  }
}
