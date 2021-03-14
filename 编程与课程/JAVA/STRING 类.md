常用方法

```java
String str="abc";
String str2=new String("def")
String str3="abc"+"defgh"

System.out.println(str10==str11);//判断两个字符串是否相等，相等的话输出true
//字符串比较
System.out.println(str1,equals(str2));
/* 2.boolean equals(Object anobject)
{
    return true;
   
}*/

```



```java
String s1="core Java";
String s2="Core Java";
System.out.println(s1.charAt(3));//提取下标为三的字符 从零开始
System.out.println(s1.length());//字符串长度
System.out.println(s1.equals(s2));//比较两个字符串
System.out.println(s1.indexOf("java"))//字符串中是否包含java
String s1="how are you";
String s= s1.replace('','&');  //将S1中的空格替换为&
System.out.println("result is: "+s);
System.out.println(s1.startWith('how'));//是否以how开头
System.out.println(s1.endWith('you'));//是否以end开头
s=s1.substring(4);//从下标4开始提取
System.out.println（s）;//
s=s1.substring(4,7);//提取字符串，下标为【4，7）
S=S1.toLowerCase();//字符串转小写
s=s1.toUpperCase();//字符串转大写
String s2 ="  how old are you  ";
s = s2.trim(); //去除首尾的空格


```

### 数组的拷贝

```java
//数组的拷贝
String[] s1={"aa",'bb',"cc","dd","ee"};
String[] s2=new String[10];
System.arraycopy(s1,2,s2,6,3);//从第几个数组拷贝到第几个数值，拷贝多大长度
System.arraycopy(src,srcPos,dest ,destPos,length);
for(int i;i<s1.length();i++)
{
    printf（i+"... "+s1[i]);
    
}
//从数值中删除一个元素

//删除指定位置的数组值
public static String[] removeArrayElement(String[] s,int index)//index从1开始

{
    
    System.arraycopy(s,index,s,index-1,s.length-index);
    s[s.length-1]=null;
    return s;
}
//指定位置进行数组扩容
	String s1=["aa",'bb','cc'];
	String s2=new String[s1.length+10];//括充
	
	
String[] public static ArraySpaceAdd(String[] s,String[] add   )
{
    if(add[0].equals('+'))
    { 
      String s2= new String[s2.length+add];
    }
}
//实现字符数组的扩容
public static	String[]  ArraySpaceAdd(String[] s,char op ,int num  )
	{
	    if(op=='+')
	    { 
	      String[] s2= new String[s.length+num];
          System.arraycopy(s,0,s2,0,s.length);
	      return s2;
	    }
	    if(op=='*')
        {
          String[] s3=new String[s.length*num];
          System.arraycopy(s,0,s3,0,s.length);
          return s3;
        }
    	
	return s;
	}
	
```

### Arrays工具类

```
int[] a={100.20.30.5.150.80.200}
System.out.println(Arrays.toString（a）);//打印数组内容
Arrays.sort(a);//对数组a进行排序 从小到大排序 用二分法进行的排序
System.out.println(Arrays.binarySearch（a，30）);//查找，找到后返回索引


```

### 二位数组

```
int a=new int[][];
```

