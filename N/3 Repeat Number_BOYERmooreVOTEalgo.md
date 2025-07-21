Problem Description

You're given a read-only array of N integers. Find out if any integer occurs more than N/3 times in the array in linear time and constant additional space.
If so, return the integer. If not, return -1.

If there are multiple solutions, return any one.

Note: Read-only array means that the input array should not be modified in the process of solving the problem


#bruteforce  tc o(n^2)
#array sort tc o(nlogn)

#optimised using BOYER MOORE MAJORITY ALGO

public class Solution {
    public int repeatedNumber(int[] A) {
        int n=A.length;
        //here there is a chance for 2 values to become more thean n/3 times
        if(n==1){
            return A[0];
        }
        // int maxcount=Integer.MIN_VALUE;
        //  int secMaxcount=Integer.MIN_VALUE;
        int fstPossibleValue=Integer.MIN_VALUE,fstCount=0;
        int scndPossibleValue=Integer.MAX_VALUE,scndCount=0;


        for(int i=0;i<n;i++){
            if(A[i]==fstPossibleValue){
                fstCount++;

            }else if(A[i]==scndPossibleValue){
                scndCount++;

            }else if(fstCount==0){
                fstPossibleValue=A[i];
                fstCount=1;
            }else if(scndCount==0){
                scndPossibleValue=A[i];
                scndCount=1;
            }
            else {
                scndCount--;
                fstCount--;
            }

        }
        int count1=0,count2=0;

        for(int k=0;k<n;k++){
            if(A[k]==fstPossibleValue){
                count1++;
            }
            if(A[k]==scndPossibleValue){
                count2++;
            }
        }
        if(count1>n/3)  return fstPossibleValue;
        else if(count2>n/3) return scndPossibleValue;
        else return -1;

    }
}
