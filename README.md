# lichangyu2015.github.io
燕七技术博客
#include<iostream>
#include<algorithm>
#include<vector>
#include<cmath>
#include<map>
#include <sstream>
#include<list>
using namespace std;

class Solution {
public:
    private:
	int lo,maxLen;
public:
    string shortestPalindrome(string s) {
       int len = s.length();
    if (len < 2)
        return s;

    for (int i = 0; i < len-1; i++) {
        extendPalindrome(s, i, i);  //assume odd length, try to extend Palindrome as possible
        extendPalindrome(s, i, i+1); //assume even length.
    }
    string first=s.substr(0,lo-1),str=s.substr(lo, maxLen),tail=s.substr(lo+maxLen,s.length()-lo-maxLen+1);
    return reverse(tail)+first+str+reverse(first)+tail;
    
    }
    string reverse(string s)
    {
    	string res="";
    	for(int i=0;i<s.length();++i)
    		res=s[i]+res;
    	return res;
	}
    void extendPalindrome(string s, int j, int k) {
  	  while (j >= 0 && k < s.length() && s[j] == s[k]) {
        j--;
        k++;
    	}
  
    (maxLen < k - j - 1)?(maxLen = k - j - 1,lo=j+1):lo;
     }
};

int main()
{
	Solution s;	
	cout<<s.shortestPalindrome("aaaaaaaaa");
}
