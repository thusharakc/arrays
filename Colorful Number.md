Problem Description

Given a number A, find if it is COLORFUL number or not.

If number A is a COLORFUL number return 1 else, return 0.

What is a COLORFUL Number:

A number can be broken into different consecutive sequence of digits. 
The number 3245 can be broken into sequences like 3, 2, 4, 5, 32, 24, 45, 324, 245 and 3245. 
This number is a COLORFUL number, since the product of every consecutive sequence of digits is different



import java.util.Collections;
public class Solution {
    public int colorful(int A) {
        ArrayList<Integer> list=new ArrayList<Integer>();

        int dummy=A,rem=0;
        while(dummy>0){
            rem=dummy%10;
            dummy=dummy/10;
            list.add(rem);
        }
        Collections.reverse(list);  //this will contain all the digits in the number
        HashSet<Integer> hs=new HashSet<Integer>();
        int n=list.size();
        for(int i=0;i<n;i++){
            int prod=1;
            for(int j=i;j<n;j++){

               prod*= list.get(j);
               if(!hs.contains(prod)){
                   hs.add(prod);
               }else{
                   return 0;
               }

            }
        }
        return 1;
        
    }
}
