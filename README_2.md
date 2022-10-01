### Task №1(6kyu)
You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement the function which takes an array containing the names of people that like an item. It must return the display text as shown in the examples:

~~~
[]                                -->  "no one likes this"
["Peter"]                         -->  "Peter likes this"
["Jacob", "Alex"]                 -->  "Jacob and Alex like this"
["Max", "John", "Mark"]           -->  "Max, John and Mark like this"
["Alex", "Jacob", "Mark", "Max"]  -->  "Alex, Jacob and 2 others like this"
Note: For 4 or more names, the number in simply increases."and 2 others"
~~~

[Task_link](https://www.codewars.com/kata/5266876b8f4bf2da9b000362)

#### Solution

~~~ Java
public class Solution {
    public static String whoLikesIt(String... names) {
        int len = names.length;
        String result = "";
        if (len == 0) {
            result += "no one likes this";
        } else if (len == 1) {
            result += names[0] + " likes this";
        } else if (len == 2) {
            result += names[0] + " and " + names[1] + " like this";
        } else if (len == 3) {
            result += names[0] + ", " + names[1] + " and " + names[2] + " like this";
        } else if (len >= 4) {
            result += names[0] + ", " + names[1] + " and " + Integer.toString(len - 2) + " others like this";
        }
        return result;
    }
}
~~~

#### Fav Solution
~~~ Java
class Solution {
    public static String whoLikesIt(String... names) {
        switch (names.length) {
          case 0: return "no one likes this";
          case 1: return String.format("%s likes this", names[0]);
          case 2: return String.format("%s and %s like this", names[0], names[1]);
          case 3: return String.format("%s, %s and %s like this", names[0], names[1], names[2]);
          default: return String.format("%s, %s and %d others like this", names[0], names[1], names.length - 2);
        }
    }
}
~~~

### Task №2(7kyu)

Complete the function that accepts a string parameter, and reverses each word in the string. All spaces in the string should be retained.

[Task_link](https://www.codewars.com/kata/5259b20d6021e9e14c0010d4/java)

#### Solution

~~~ Java
public class Kata {
    public static String reverseWords(final String original) {
        String[] strArray = original.split(" ");
        String result = "";
        if (original.trim().length() == 0) {
            return original;
        }
        for (int i = 0; i < strArray.length; i++) {
            char[] s1 = strArray[i].toCharArray();
            for (int j = s1.length - 1; j >= 0; j--) {
                result = result + s1[j];
            }
            result = result + " ";
        }
        return result.substring(0, result.length() - 1);
    }
}
~~~

#### Fav Solution

~~~ Java
import java.lang.StringBuilder;

public class Kata
{
  public static String reverseWords(final String original)
  { 
    String[] array = original.split(" ");
    
    if(array.length == 0) 
        return original;
    
    
    int i = 0;
    for(String string : array){
        array[i] = new StringBuilder(string).reverse().toString();
        i++;
    }
    
    return String.join(" ",array);
  }
}
~~~


:)
