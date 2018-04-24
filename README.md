# JavaSnippets

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

#### Converting int to String and Strings to int
    String a = String.valueOf(2); //integer to numeric string
    int i = Integer.parseInt(a);  //numeric string to an int

#### Converting String to date in Java
    java.util.Date = java.text.DateFormat.getDateInstance().parse(date String);
