https://leetcode.com/problems/letter-combinations-of-a-phone-number/#/description

17 Letter Combinations of a Phone Number

> Given a digit string, return all possible letter combinations that the number could represent.
> 
> A mapping of digit to letters (just like on the telephone buttons) is given below.
> 
> ![image](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)
> 
> Input: Digit string "23"

> Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].


**题意**

以下代码暂时没有弄懂， 以后再说吧


**JAVA**


```
    public List<String> letterCombinations(String digits){
        LinkedList<String> res = new LinkedList<>();
        String[] map = new String[]{"0","1","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
        if (digits==null ||digits.length() ==0){
            return res;
        }
        res.add("");
        for (int i =0;i<digits.length();i++){
            int x = Character.getNumericValue(digits.charAt(i));
            while (res.peek().length() ==i){
                String t =res.remove();
                for (char s :map[x].toCharArray())
                    res.add(t + s);
            }
        }
        return res;
    }
```
