# JavaSnippets

#### Hello World
    public class HelloWorld {
        public static void main(String[] args) {
            System.out.println("Hello World");
        }
    }


#### If / Else
    if ( a > b ){
       out.println( a );
       }
    else{
       out.println( b );
       }
   
#### If / Else : is x in range low .. high?
    if ( low <= x && x <= high ){
       out.println( "in range" );
       }
    else{
       out.println( "out of range" );
       }

#### Switch / Case
    switch ( n ){
       case 1: out.println( "one" );
          break;
       case 2: out.println( "two" );
          break;
       default: out.println( "something else" );
       }// end switch (n)
       
#### For Loop
##### When you know the maximum number of times to iterate in advance.
    for ( int i=0; i<n; i++ ){
       out.println( i );
       }

#### F O R to step through each char of a String, left to right
// Avoids recomputing s.length. Avoids defining n outside the loop.
// Note you must use a comma before n, not a semicolon.
// You may not say int n= or final int n=.
    for ( int i=0,n=s.length(); i<n; i++ )
       {
       out.println( s.charAt( i ) );
       }

#### Reverse For Loop  
##### to countdown
    for ( int i=n-1; i>=0; i-- ){
       out.println( i );
       }

#### Reverse For Loop to step through each char of a String, right to left
    for ( int i=s.length()-1; i>=0; i-- ){
       out.println( s.charAt( i ) );
       }

#### Double For
    for ( int i=0, j=0; i<n; i++,j++ ){
       out.println( i );
       }

// A R R A Y - S P A N N I N G   F O R
String[] stuff = new String[ 10 ];
for ( int i=0; i<n; i++ )
   {
   String s = stuff[i];
   out.println( s );
   }

// F O R : E A C H   A R R A Y - S P A N N I N G   F O R   Java 1.5+
// works when stuff is an array, ArrayList or Collection,
String[] stuff = new String[ 10 ];
...
for ( String s : stuff )  // note String not int!!
   {
   out.println( s );
   s = somethingElse; // Watch out! This has no effect on the stuff[] array!!
   }

// F O R : E A C H   E N U M - S P A N N I N G   F O R   Java 1.5+
// Example iterating over all possibilities.
// Print out a list of all possible breeds of Dog
enum Breed { DALMATIAN, LABRADOR, DACHSHUND }
...
for ( Breed dog : Breed.values() )
   {
   out.println( dog );
   }

// E N U M E R A T I O N
// (nothing to do with enum)
// (largely replaced by Iterator)
Enumeration<String> e  = xxx.getEnumeration();
while ( e.hasMoreElements() )
   {
   String key = e.nextElement();
   out.println( key );
   }

// I T E R A T O R
// Note; after hasNext()
for ( Iterator iter = list.iterator(); iter.hasNext(); )
   {
   String key = (String)iter.next();
   out.println( key );
   }

// I T E R A T O R : alternate when you already have the Iterator
Iterator someFiles = getFilesToProcess();
while ( someFiles.hasNext() )
   {
   File f = (File)someFiles.next();
   ...
   }

// I T E R A T O R - R E M O V E :  efficiently removing elements from a List (ArrayList, LinkedList etc.)
// or Collection.
// You can't remove elements with a for:each.
// This works faster than a get/remove.
// This approach avoids the effects of the List renumbering as you go which can cause you to
// inadvertently skip elements or run off the end.
for ( Iterator<Item> iter = items.iterator(); iter.hasNext(); )
   {
   Item item = iter.next();
   if ( item.isUnwanted() )
       {
       // remove from underlying Collection
       iter.remove();
       }
    }

// F O R : E A C H   I T E R A B L E : Java 1.5+
// myFiles is a refererence to a container class that implements Iterable,
// namely has an iterator() method to enumerate the
// elements of the collection.
// All Collections such as ArrayList, TreeSet,
// HashMap, PriorityQueue... all implement Iterable.
// Note what you use in the for:each
// is not the result of myFiles.iterator() but myFiles itself.
// Note for, not while
for ( File f : myFiles )
   {
   if ( f.isDirectory() ) ...
   }

// F O R : E A C H   I T E R A B L E  W I T H   E L L I P S I S (...): Java 1.5+

void myMethod( String... animals )
   {
   for ( String animal : animals )
      {
      out.println( animal );
      }
   }
...
// calling myMethod defined above
myMethod( "tiger", "lion", "hippopotamus" );
myMethod( "tiger" );
myMethod( );

String[] someStringArray = getValues();
myMethod( someStringArray );

// W H I L E  (loop possibly zero times)
// Used when you don't know in advance how many times max you will loop.
while ( moreData() )
   {
   readIt();
   }

// D O / W H I L E  (loop at least once, aka repeat)
// Used when you don't know in advance how many times max you will loop.
do
   {
   readIt();

   if ( done() )
      {
      break;
      }

   if ( bypassThisOne() )
      {
      continue;
      }

   processIt();

   } while ( moreData() );

// create the array to iterate over in line.
for ( String encoding : new String[] { "IBM437", "UTF-8", "ISO-8859-1" } )
    {
    out.println( encoding );
    }
// -30-


#### Try/Catch/Throw
    public class Test extends StandardTest{
       public static void main (String [] args){
          try{
             dangerMethod();
             }
          catch ( StrangeException e )     // in JDK 1.7+ you can catch multiple exceptions, e.g. catch (IOException|SQLException ex){
             out.println( "oops" + e.getMessage() );
             }
          } // end main

       void dangerMethod() throws StrangeException{
          if ( unexpected() ) throw new StrangeException ( "oh oh" );
       } // end dangerMethod
       } // end class Test


#### Converting int to String and Strings to int
    String a = String.valueOf(2); //integer to numeric string
    int i = Integer.parseInt(a);  //numeric string to an int

#### Converting String to date in Java
    java.util.Date = java.text.DateFormat.getDateInstance().parse(date String);
or

    SimpleDateFormat format = new SimpleDateFormat( "dd.MM.yyyy" );
    Date date = format.parse( myString );
    
#### Converting Java util.Date to sql.Date
    java.util.Date utilDate = new java.util.Date();
    java.sql.Date sqlDate = new java.sql.Date(utilDate.getTime());
    
    
    
#### Scan file content
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
    
    
#### Factorial
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

    
    
    
    
    
    
    
    
#### Fibonacci
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

#### FizzBuzz
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

#### HTTP Get
	import java.io.IOException;
	import java.net.HttpURLConnection;
	import java.net.URL;

	public class Test {

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

#### Palindrome
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
    
#### Reverse String
    public class ReverseString {
        public static void main(String[] args) {
			// reverseString("Hello World");
		    System.out.println(reverseString("Hello World"));
    }

    public static String reverseString(String s) {
        return new StringBuilder(s).reverse().toString();
    	}
	}

    
