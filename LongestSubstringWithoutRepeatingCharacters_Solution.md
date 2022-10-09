# Problem
https://leetcode.com/problems/longest-substring-without-repeating-characters/
# Solution
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        
        HashMap<Character, Integer> letterFrequencies =  new HashMap<Character, Integer>();
        int windowEnd = 0;
        int currentLength = 0;
        int maxLength = 0;
        
        for (int windowStart = 0; windowEnd < s.length(); windowEnd++){
            char rightChar = s.charAt(windowEnd);
            
            if (letterFrequencies.containsKey(rightChar)){
                letterFrequencies.put(rightChar, letterFrequencies.get(rightChar) + 1);

                while (letterFrequencies.get(rightChar) > 1){
                    
                    char leftChar = s.charAt(windowStart);   
                    letterFrequencies.put(leftChar, letterFrequencies.get(leftChar) - 1);
                    
                    if (letterFrequencies.get(leftChar) <= 0){
                        letterFrequencies.remove(leftChar);
                    }
                    
                    windowStart++;
                }
                
            } else {
                letterFrequencies.put(rightChar, 1);
            }
            
            currentLength = (windowEnd - windowStart) + 1;
            maxLength = Math.max(currentLength, maxLength);
        }
        
        return maxLength;
    }
}


    
// "abcabcbb" -> "abc" -> 3
// "bbbbb" -> "b" -> 1
// "pwwkew"" -> "wke" -> 3
// "pwwabcdfdkew"
    
    
// iterate thru the str
    
    // if rightChar is two times on letters
    
        // while leftChar is on letters
        // increment windowStart
    
    // else put rightChar on letters
    
    
    // currentLength = (windowEnd - windowStart) + 1
    // maxLength = max(currentLength, maxLength)
```
