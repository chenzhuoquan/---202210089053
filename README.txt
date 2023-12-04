://第一次修改
package Git;

import java.util.Scanner;

public class GitText {

 //加密第一步，将字符串的每个字符转化为ASCII值并进行加值操作
    public static char[] encryptFirst(char []nums){

        for(int i=0;i<nums.length;i++){
            int j=(int)nums[i];//每个字符转化为ASCII值
            int j1=j+i+1+3;//将转化之后的值加上在字符串中的位置和3
            if(j1>127){
                j1-=127;
            }
            nums[i]=(char)j1;
        }
        return nums;
    }

//解密的第一步，将字符串的每个字符转化为ASCII值并进行减值操作
    public static char[] encryptFirst1(char []nums){

        for(int i=0;i<nums.length;i++){
            int j=(int)nums[i];//每个字符转化为ASCII值
            int j1=j-i-1-3;//将转化之后的值加上在字符串中的位置和3
            if(j1<0){
                j1+=127;
            }
            nums[i]=(char)j1;
        }
        return nums;
    }
    //加密第二步，将字符数组中的首尾进行调换
    public static char[] encryptSecond(char[] nums2){
        char i=' ';
        int length=nums2.length;
        i=nums2[0];
        nums2[0]=nums2[length-1];
        nums2[length-1]=i;
        return nums2;
    }
    
    public static boolean judgeNum(char[]nums3){
        boolean flag=true;
        for(char i:nums3){
            if(!((int)i>=48&&(int)i<=57)){
                flag=false;
            }
        }
        return flag;
    }
    public static boolean judgeChar(char[]nums4){
        boolean flag=true;
        for(char i:nums4){
            if(!((int)i>=65&&(int)i<=122)){
                flag=false;
            }
        }
        return flag;
    }
    public static boolean judgeNum1(char[]nums4){
        for(char i:nums4){
            if(((int)i>=48&&(int)i<=57)){
                return true;
            }
        }
        return false;
    }
    public static boolean judgeChar1(char[]nums4){
        for(char i:nums4){
            if(((int)i>=65&&(int)i<=122)){
                return true;
            }
        }
        return false;
    }
    public static boolean judgeBChar(char[]nums4){
        for(char i:nums4){
            if(((int)i>=65&&(int)i<=90)){
                return true;
            }
        }
        return false;
    }
    public static boolean judgeSChar(char[]nums4){
        for(char i:nums4){
            if(((int)i>=97&&(int)i<=122)){
                return true;
            }
        }
        return false;

    }

   
 public static String Password(int length) {
        String password = RandomStringUtils.randomAlphanumeric(length);

        while (!isPassword(password)) {
            password = RandomStringUtils.randomAlphanumeric(length);
        }

        return password;
    }



private static boolean isPassword(String password) {
        String regular = "^(?=.*\\d)(?=.*[a-z])(?=.*[A-Z])[0-9a-zA-Z]+$";
        Pattern pattern = Pattern.compile(regular);
        Matcher matcher = pattern.matcher(password);
        return matcher.matches();
    }


    public static void menu(){
        System.out.println("===========================");
        System.out.println("欢迎来到好用的密码管理系统 ");
        System.out.println("===========================");
        System.out.println("         请选择操作:        ");
        System.out.println("  1.加密功能     2.解密功能  ");
        System.out.println("       3.判断密码强度        ");
        System.out.println("  4.密码生成     5.退出      ");
    }



     public static void  main(String[] args) {

        int input=0;
        do{
            menu();
            Scanner scanner=new Scanner(System.in);
            System.out.print("请输入");
            input=scanner.nextInt();
            switch (input){
                case 1: System.out.println("===========================");
                        System.out.println("    欢迎使用密码管理系统     ");
                        System.out.println("===========================");
                        System.out.print("请输入要加密的数字密码:");
                        Scanner scanner1=new Scanner(System.in);
                        String s = scanner1.nextLine();
                        char[] chars1 = encryptSecond(encryptFirst( s.toCharArray()));
                        String s2 = String.valueOf(chars1);
                        StringBuffer stringBuffer=new StringBuffer(s2);
                        String s3 = stringBuffer.reverse().toString();
                        System.out.println("加密后的结果是:"+s3);
                        break;


                case 2: System.out.println("===========================");
                        System.out.println("    欢迎使用密码管理系统     ");
                        System.out.println("===========================");
                        System.out.print("请输入要解密的数字密码:");
                        Scanner scanner2=new Scanner(System.in);
                        String s1 = scanner2.nextLine();
                        StringBuffer stringBuffer1=new StringBuffer(s1);
                        String s4 = stringBuffer1.reverse().toString();
                        char[] chars = encryptSecond(s4.toCharArray());
                        char[] chars2 = encryptFirst1(chars);
                        String s7 = String.valueOf(chars2);
                        System.out.println("解密后的结果是:"+s7);
                        break;

                case 3: System.out.println("===========================");
                        System.out.println("    欢迎使用密码管理系统     ");
                        System.out.println("===========================");
                        System.out.print("请输入要判断的数字密码:");
                        Scanner scanner3=new Scanner(System.in);
                        String s6 = scanner3.nextLine();
                        char[]s5=new char[s6.length()];
                        for (int i=0;i<s6.length();i++){
                            s5[i]=s6.charAt(i);
                        }
                        if(s5.length<8){
                            System.out.println("低强度:长度小于8");
                        }else if(judgeNum(s5)||judgeChar(s5)){
                            System.out.println("低强度:长度大于8并且只有一种字符类型");
                        }else if((judgeNum1(s5)&&judgeBChar(s5)&&judgeSChar(s5))){
                            System.out.println("高强度:至少有一个数字、一个小写字母、一个大写字母");
                        }
                        else if((judgeNum1(s5)&&judgeChar1(s5))){
                            System.out.println("中强度:有一个数字和一个字母");
                        }
                        break;

                case 4: System.out.println("===========================");
                        System.out.println("    欢迎使用密码管理系统     ");
                        System.out.println("===========================");
                        System.out.print("请输入要给定的密码长度:");
                        Scanner scanner4=new Scanner(System.in);
                        int i = scanner4.nextInt();
                        String password =Password(i);
                        System.out.println("给定的长度为:"+i+"并且生成之后的高强度密码为:"+password);


            }

        }while(input!=5);






    }

}
