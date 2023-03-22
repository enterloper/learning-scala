# learning-scala
A place for me to store notes as I figure out Scala

Scala Notes
Features of Scala
* Type Inference
    * Deduction of the data types based on the context in which an object has been written is default behavior. Scala can infer types without them being explicitly stated.
* Immutability
    * Variables in Scala are immutable by default. This helps in concurrency control managing simultaneous (concurrent) operations so they avoid conflicts with each other.
* Lazy Computation
    * Scala only evaluates an expression when required, this feature increases performance through the reduction of compile time.
* Case Classes & Pattern Matching
    * Case classes are regular classes with the added feature of being immutable. This is especially helpful in modeling immutable data. Furthermore case classes are useful for pattern matching (checking a value against a pattern and deconstructing it into its constituent parts).
* String Interpolation
    * String interpolation methods allow developers to embed variables directly inside a string literal allowing for the creation of strings through data.
* Higher-Order Functions
    * Functions which take other functions as arguments. These functions can return functions as well as simple data types.
* Traits
    * Traits are a collection of abstract and non-abstract methods. While classes and objects can only inherit from a single class, those same classes and objects can inherit from multiple traits.

Variables in Scala
Declaring a variable
   keyword variableName: DataType = Initial Value
   val answerToLifeUniverseEverything: Int = 42
       In the code above, we are declaring a variable with the name answerToLifeUniverseEverything. answerToLifeUniverseEverything can store data of type Int and is assigned an initial value of 42.
       It is an immutable variable because we chose the keyword val.

   Choosing the "Right" keyword:      Variables of type val are immutable variables; once they are initialized, they can never be reassigned.
     Variables of type var are mutable and thus can be reassigned throughout their lifetime as long as they are valid (match the DataType)

	val bookTitle: String = "Lord of the Rings: The Fellowship of the Ring"
	val bookAuthor: String = "J. R. R. Tolkien"
	val bookNoOfPages: Int = 423

Printing in Scala

Printing Methods in Scala (print, println, printf)

“print” is the simplest method for displaying output in Scala.
	print("Hello world!")
	print(answerToLifeUniverseEverything)
        print(“Now you know!”)
       // output => “Hello world!42Now you know!”

“println” is used when displaying each specific output on separate lines. In other words, with each println statemtent, the output is automatically displayed on the next line.
	print("Hello world!")
	print(answerToLifeUniverseEverything)
        print(“Now you know!”)

	//output:
	 “Hello world!”
	 “42”
	 “Now you know!”

“printf” is used for formatting text. It can be used to append different data types to text that is to be printed.
	println("Number = %d", 123)
	printf("Number = %d", 123)
	// output:        (Number = %d, 123)
       (Number = 123)


Immutable Variables
Immutable variables are basically like constants; once they are assigned a value, that value can never change. To declare an immutable variable, we use the val keyword. In Scala, the general rule is to use the val field unless there’s a good reason not to.

val message: String = “Hello World!”

println(message) // “Hello World!”


Mutable Variables
To declare a mutable variable, we use the var keyword. 

var message: String = "Hello World"
message = "Hello neighbor”

// Driver Code
println(message) // “Hello neighbor”


Scala Type Hierarchy
In a type hierarchy, the more generic types are at the top and as you go lower in the hierarchy, the types get more specific, i.e., have more requirements. Each type has a requirement of its own along with the requirements of all the types above it in the hierarchy.

Any
At the top of the type hierarchy in Scala, is the type “Any”, this super-type defines certain universal methods such as equals, hashCode, and toString.
￼
Any has two subclasses AnyVal and AnyRef.  There are nine main value types supported in Scala:
* Double
* Float
* Long
* Int
* Short
* Byte
* Char
* Unit
* Boolean

AnyRef represents reference types. Any type that is not a value type is a reference type, including types defined by users not predefined in Scala.

For a value type, the information it provides is the value itself. For a reference type, the information it provides is a reference to some object, i.e., the memory address of an object.

An analogy would be your house. Your house would be the value type, while the reference type would be your house’s physical address.  Any on display: var anyInAction: Any = "A String" //String
println(anyInAction)

anyInAction = 5 //Int
println(anyInAction)

anyInAction = '☺' //Char
println(anyInAction)

anyInAction = 1.985 //Float
println(anyInAction)

anyInAction = true //Boolean
println(anyInAction)


Using Value Types

val myDoubleVariable: Double = 2.75
val myFloatVariable: Float = 2.75f
val myLongVariable: Long = 275000000000L
val myIntVariable: Int = 275
val myShortVariable: Short = 1
val myByteVariable: Byte = 0xa
val myCharVariable: Char = '☺'
val myUnitVariable: Unit = ()
val myBooleanVariable: Boolean = true

(Unit is analogous to void in other programming languages)

Type Casting
Type casting is an approach which allows changing the data type of a variable or an expression from one to another.
One thing to remember is that not every data type can be converted to a data type of choice
￼
The elements more or less remain the same and the value is simply altered with respect to the new data type.

Long -> Float
val oldType: Long = 926371285
val newType: Float = oldType
println(oldType) // => 926371285
println(newType) // => 9.2637126E8

Consider the variable oldType of type Long, if that value needs to be as type Float, , a new variable newType can be created of type Float and be assigned the value of oldType. Type casting ensures the value is altered according to the data type.

Alternatively, attempting to convert a variable of type Float to a type Long will result in a runtime error: type mismatch. This is because newType is of type Float and newOldType is being converted to Long which breaks the type casting flowchart viewed above.  val oldType: Long = 926371285
val newType: Float = oldType
val newOldType: Long = newType

println(oldType)
println(newType)
println(newOldType)

main.scala:3: error: type mismatch;
 found   : Float
 required: Long
val newOldType: Long = newType

Char -> Int
Every character has a Decimal [ASCII](https://www.asciitable.com/) value. In the following example the character A is converted to its respective ASCII value of 65.

val oldType: Char = 'A'
val newType: Int = oldType

println(oldType) // -> A
println(newType) // -> 65


Strings and Other Literals

￼

Reviewing the data type hierarchy above, it can be observed that type String does not fall under type AnyVal. So what is type String? The answer is literals.

Literals
A literal is defined as taking anything in its most usual and basic sense. Mapping this onto computer programming, literals are fixed values appearing directly as is in the source code. For example, “Hello World”, 5, and ‘A’ are all considered literals.

String Literals
String Literals are a combination of characters surrounded by double quotation marks. The syntax for declaring a variable of type String is the same as declaring a variable of any basic value type.
val stringLiteral: String = “Hello”

Integer Literals
Integer literal dare used with he value types Long, Int, Short, and Byte. They can be created in two forms: decimal and hexadecimal. Decimal number have a base 10 while hexadecimal have a base of 16. The way an integer literal begins indicates the base of the number. If the number begins with 0x or 0X, it is considered a hexadecimal and may contain the number from 0 to 0 as well as upper or lowercase letters from A to F. Numbers that do not start with a 0x or 0X are decimal by default.

val hex: Int = 0x0F5
val dec: Int = 245

val hex1: Long = 0x0A3DE5L //The L at the end is for Long
val dec1: Long = 671205L

println(hex)
println(dec)
println(hex1)
println(dec1)

Note: One thing to remember is that Scala will always print an integer literal as decimal regardless of how it is declared.

Floating-Point Literals
Floating-point literals are used with Double and Float. Additionally they are made up of decimal digits and have the option of adding exponents using either an e or E followed by the exponent.

val floatLiteral: Float = 1.2345F // The F at the end is for Float
val somethingBigger: Double = 1.2345e1
val evenBigger: Double = 1.2345e4

println(floatLiteral)
println(somethingBigger)
println(evenBigger)

Character Literals

Character literals are used with Char and are made up of a single Unicode character surrounded by single quotation marks.
val charLiteral: Char = 'A'
val smile: Char = '☺'

// Driver Code
println(charLiteral)
println(smile)

Escape sequences, as shown in the table below, also represent character literals.
Literal	Meaning
\n	linefeed
\b	backspace
\t	tab
\f	form feed
\r	carriage return
\"	double quote
\’	single quote
\\	backslash

Examples: println("separate\nlines")     //using \n to end the line
println("tab\tbetween\twords") //using \t to insert a tab
println('\\')                  //using \\ to print a backslash
println('\'')                  //using \' to print a single quotation mark
println('\"')

Boolean Literals
Boolean literals are used with Boolean. They are of two types: true and false.

val theTruth: Boolean = true
val aLie: Boolean = false

// Driver Code
println(theTruth)
println(aLie)

Type Inference
Type inference is Scala’s ability to infer types when not specified by the user.


val bookTitle: String = "Lord of the Rings: The Fellowship of the Ring"
val bookAuthor: String = "J. R. R. Tolkien"
val bookNoOfPages: Int = 423

println(bookTitle)
println(bookAuthor)
println(bookNoOfPages)

In the example above, the following syntax is used: keyword variableName: DataType = Initial Value
Scala’s type inference feature allows us to declare a variable without explicitly mentioning the data type.
This is why Scala’s variable declaration enforces the data type to be mentioned after the variable name; for easy removal. This results in the following syntax:

val bookTitle = "Lord of the Rings: The Fellowship of the Ring"
val bookAuthor = "J. R. R. Tolkien"
val bookNoOfPages = 423

println(bookTitle)
println(bookAuthor)
println(bookNoOfPages)

So how do we know if bookTitle is indeed of type String? By using variableName.isInstanceOf[String] or variableName.getClass operators. Alternatively we can produce an error which will report the data type of the variable.

example: val bookTitle = "Lord of the Rings: The Fellowship of the Ring"
val testInteger: Int = bookTitle

error: type mismatch
found: String
required: Int


Functions/Operators in Scala
Functions in Scala can be divided into two broad categories: Built-In Functions and User-Defined Functions
User-Defined Functions  are created by users.
Built-In Functions also known as methods are predefined by Scala and part of any respective libraries consumed by the user. Ie: `println`, `print`, `printf`

Calling a Function
There are two ways to invoke or call a function, here’s the syntax for each:  objectName.methodName(arguments)
objectName methodName arguments

Operators are symbols that perform operations used for modifying or manipulating data. Scala provides the following five types of operators:
* Arithmetic Operators
* Relational Operators
* Logical Operators
* Bitwise Operators
* Assignment Operators

Operators usually follow an infix notation. The infix notation is where the operator is situated between two operands. Operands are the data objects that the operator is performing an operation on.
￼
After the operator has performed its specific operation, the output is the result of the operation.

NOTE: In Scala operators are not special language syntax; any method can be an operator. What makes a method an operator is how you use it. When we wrote string1.indexOf('W') in the previous lesson, indexOf was not an operator. But when we wrote string1 indexOf 'W', indexOf was an operator, because we’re using it in operator notation.

NOTE: The infix notation is a much simpler syntax and is the conventional way of using operators.

1+1 -> 1.+(1)

val infix = 1+1
val ordinary = 1.+(1)

println("Using infix notation: "  + infix)
println("Using ordinary method call: " + ordinary)



