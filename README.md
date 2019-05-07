# JavaSnippets


# Basic


## Converting int to String and Strings to int
```java
String a = String.valueOf(2); //integer to numeric string
int i = Integer.parseInt(a);  //numeric string to an int
```


## Converting String to date in Java
```java
import java.text.DateFormat;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Locale;

public class Main {
    public static void main(String[] args) throws ParseException {
        /*
          Input string                            Pattern
        ------------------------------------    ----------------------------
        2001.07.04 AD at 12:08:56 PDT           yyyy.MM.dd G 'at' HH:mm:ss z
        Wed, Jul 4, '01                         EEE, MMM d, ''yy
        12:08 PM                                h:mm a
        12 o'clock PM, Pacific Daylight Time    hh 'o''clock' a, zzzz
        0:08 PM, PDT                            K:mm a, z
        02001.July.04 AD 12:08 PM               yyyyy.MMMM.dd GGG hh:mm aaa
        Wed, 4 Jul 2001 12:08:56 -0700          EEE, d MMM yyyy HH:mm:ss Z
        010704120856-0700                       yyMMddHHmmssZ
        2001-07-04T12:08:56.235-0700            yyyy-MM-dd'T'HH:mm:ss.SSSZ
        2001-07-04T12:08:56.235-07:00           yyyy-MM-dd'T'HH:mm:ss.SSSXXX
        2001-W27-3                              YYYY-'W'ww-u
        */
        String inputString = "January 2, 2010";
        String pattern = "MMMM d, yyyy";

        DateFormat format = new SimpleDateFormat(pattern, Locale.ENGLISH);
        Date date = format.parse(inputString);
        System.out.println(inputString); // Input
        System.out.println(date); // Sat Jan 02 00:00:00 GMT 2010

    }
}
```


# Hello World
```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```


# Lists


## List Operations
```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello, World. Lets Start");

        // Initialise list of String(s)
        List<String> list = new ArrayList<>();

        // Add String elements to list
        list.add("Johny");
        list.add("Steve");
        list.add("Barry");
        list.add("Harry");
        list.add("Barry");

        // We can't add Int to a List of String
        //list.add(1);

        // And the same goes for Double
        //list.add(1.55)

        // Get all list elements
        System.out.println(list);

        // Get the first list element
        String first_list_element = list.get(0);
        System.out.println("First element is: " + first_list_element);

        // Get the second list element
        String second_list_element = list.get(1);
        System.out.println("Second element is: " + second_list_element);

        // Check list size
        System.out.println("List size is: " + list.size());

        // Remove only the first occurrence of Object Barry
        System.out.println("\nRemoving the first occurrence of Barry");
        list.remove("Barry");
        System.out.println("List size is: " + list.size());

        // Remove element (now Johny) by its index (position) 0 = first
        System.out.println("\nRemoving element by index 0");
        System.out.println(list);
        list.remove(0);

        // Get whole list
        System.out.println(list);

        // Apply function toUpperCase to each List element
        list.replaceAll(String::toUpperCase);
        System.out.println(list);

        // Create a new list instance of lowered case elements
        List<String> lower_list = list.stream().map(String::toLowerCase).collect(Collectors.toList());
        System.out.println(lower_list);
    }
}
```


# Exceptions


## Try / Catch
```java
class Main{
    public static void main(String args[]){
        System.out.println("Hello, World. Lets Start");

        try{
            int a = 10;
            int b = a / 0;
        }
        catch(ArithmeticException e){
            System.out.println("Warning: ArithmeticException");
        }
        System.out.println("Out of try-catch block");
    }
}
```


## Throw Exception
```java
public class Main {
    public static void main(String[] args) {
        System.out.println(divide(4, 0));
        if (args.length > 1) {
            // Convert a string to an integer
            int arg0 = Integer.parseInt(args[0]);
            int arg1 = Integer.parseInt(args[1]);
            System.out.println(divide(arg0, arg1));
        }
    }
    private static int divide(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("You can\'t divide by zero!");
        } else {
            return a / b;
        }
    }
}
```


## Try / Catch / Finally / Else
```java
public class Main {
    public static void main(String[] args) {

        boolean success = true;

        // Try define a block of code to be tested for errors while it is being executed
        try {
            int[] myNumbers = {1, 2, 3};
            System.out.println(myNumbers[10]);
        }

        // Catch allows to define a block of code to be executed if an error occurs in the try block
        catch (Exception e) {
            System.out.println("Something went wrong.");
            success = false;
        }

        // Finally lets you execute code, after try...catch, regardless of the result
        finally {
            System.out.println("The 'try catch' is finished.");
        }

        if (success) {
            System.out.println("Succeeded");
        }
        
    }
}
```


## Print File Content
```java
    import java.nio.file.Files;
    import java.nio.file.Path;
    import java.nio.file.Paths;
    import java.util.Arrays;

    public class Main{
        public static void main(String args[]) throws Exception{

        Path filePath = Paths.get("file.txt");
        byte[] data = Files.readAllBytes(filePath);
        String Lines = new String(data);
        System.out.println(Lines);
        }
    }
```


## Scan file content
```java
import java.io.*;
import java.util.*;

public class Scan {
    public static void main(String[] args) throws FileNotFoundException {
        Scanner scan = new Scanner(new File("file.txt"));
        while (scan.hasNextLine() ) {
            System.out.println(scan.nextLine() );
        }
    }
}
```


## Factorial
```java
public class Factorial {
    public static void main(String[] args){
        // factorial(10);
        System.out.println(factorial(10));
        }

    public static int factorial(int number) {
        int result = 1;
        for (int factor = 2; factor <= number; factor++) {
            result *= factor;
        }
        return result;
    }
}
```


## Fibonacci
```java
public class Fibonacci {
    public static void main(String[] args){
        // fibonacci(10);
        System.out.println(fibonacci(10));
        }

    public static int fibonacci(int n) {
        if (n <= 1) return n;
        else return fibonacci(n-1) + fibonacci(n-2);
    }
}
```


## FizzBuzz
```java
public class FizzBuzz {
    public static void main(String[] args) {
        for (int i = 1; i <= 100; i++) {
            if (i % 15 == 0) {
                System.out.println("FizzBuzz");
            } else if (i % 3 == 0) {
                System.out.println("Fizz");
            } else if (i % 5 == 0) {
                System.out.println("Buzz");
            } else {
                System.out.println(String.valueOf(i));
            }
        }
    }
}
```


## HTTP Get
```java
import java.io.IOException;
import java.net.HttpURLConnection;
import java.net.URL;

public class HTTPget {
    public static void main(String[] args) throws IOException{

    URL oracle = new URL("http://www.oracle.com/");     
    // httpGet(oracle);
    System.out.println(httpGet(oracle));
    }

    public static int httpGet(URL address) throws IOException {
    HttpURLConnection con = (HttpURLConnection) address.openConnection();
    return con.getResponseCode();
    }
}
```


## Palindrome
```java
public class Palindrome {
    public static void main(String[] args) {
        // isPalindrome("DAAD");
        System.out.println(isPalindrome("DAAD"));
    }

    public static boolean isPalindrome(String s) {
        StringBuilder sb = new StringBuilder();
        for (char c : s.toCharArray()) {
            if (Character.isLetter(c)) {
                sb.append(c);
            }
        }
        String forward = sb.toString().toLowerCase();
        String backward = sb.reverse().toString().toLowerCase();
        return forward.equals(backward);
    }
}
```


## Reverse String
```java
public class ReverseString {
    public static void main(String[] args) {
        // reverseString("Hello World");
        System.out.println(reverseString("Hello World"));
}

    public static String reverseString(String s) {
        return new StringBuilder(s).reverse().toString();
    }
}
```


## Count days between dates
```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.concurrent.TimeUnit;


public class Main {

    public static void main(String[] args) {
        
        SimpleDateFormat myFormat = new SimpleDateFormat("dd MM yyyy");
        String inputString1 = "23 01 1997";
        String inputString2 = "27 04 1997";

        try {
            Date date1 = myFormat.parse(inputString1);
            Date date2 = myFormat.parse(inputString2);
            long diff = date2.getTime() - date1.getTime();
            System.out.println ("Days: " + TimeUnit.DAYS.convert(diff, TimeUnit.MILLISECONDS));
        } catch (ParseException e) {
            e.printStackTrace();
        }
    }
}
```