# Maximum number of balloons
https://leetcode.com/problems/maximum-number-of-balloons

Given a string text, you want to use the characters of text to form as many instances of the word "balloon" as possible.

You can use each character in text at most once. Return the maximum number of instances that can be formed.

 
```
Example 1:
Input: text = "nlaebolko"
Output: 1

Example 2:
Input: text = "loonbalxballpoon"
Output: 2


Example 3:
Input: text = "leetcode"
Output: 0
``` 

**Constraints:**

1. 1 <= text.length <= 10^4

2. text consists of lower case English letters only.

# Implementation 1 

```java
class Solution {
    public int maxNumberOfBalloons(String text) {
        String target = "balloon";
        if(text == null || text.length() < target.length())
            return 0;
        
        String string = "";
        int i = 0, match = 0;
        int index = text.indexOf(target.charAt(i));
        while(index != -1) {
            string += Character.toString(target.charAt(i++));
            text = text.substring(0, index) + text.substring(index+1);
            if(string.equals(target)) {
                   string = "";
                   match++; 
                   i = 0; 
            }
            index = text.indexOf(target.charAt(i));
        }
       return match; 
    }
}
```
