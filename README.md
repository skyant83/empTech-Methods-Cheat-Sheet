# EmpTech Methods Info Sheet
### by Bad

 

## Defining Methods
### Methods
 * Also known as functions
 * Can be considered as _separate programs_
 * Can't work unless called/activated
 * Methods can mix and match
 * Example of a Method:
```csharp
class Program{

	static void Main(string[] args){
		
		Console.WriteLine("I am a Method");
		Console.WriteLine("I am called Main!");
		Console.WriteLine("Since I am Main, I am the first thing that runs.");
		Console.WriteLine("Because I go first, people also call me the Base Method.");
	}
}
```
>Notes:
>1.  that the *class Program* part is not considered a part of the method itself
>2.  the Main Program is the only one that can run on it's own.

-------------------------------------------------------------------
### Creating A New Class File (i.e. new .cs)
<a href="http://www.youtube.com/watch?feature=player_embedded&v=sUeO9Hmv-H0
" target="_blank"><img src="http://img.youtube.com/vi/sUeO9Hmv-H0/0.jpg" 
alt="Creating Methods" width="480" height="360" border="10" /></a>
> Click this video
-------------------------------------------------------------------
### Calling Methods 
**Lets Say I Have Two Separate Methods**

Method 1 (Base Method)
```csharp
class Program{

	static void Main(string[] args){
		Console.WriteLine("Hi, I'm the Base");
		//This just pauses the program for x milliseconds
		System.Threading.Thread.Sleep(5000);
		
	}
}
```
Method 2 
```csharp
//note you can call the class section anything you want
class Method2{
	//same goes for the Method Name 
	public void Callable_Method(){
		//this is just a placeholder, you can put any command here
		Console.WriteLine("I'm the Second Method");
	}
}
```

**Currently, running the First Method won't activate or do anything to the second Method**

**To Change that  we need to instantiate *(connect)* the second program.**

**It's as simple as adding 1 line to  the Base Method**

Method 1 (Base Method)
```csharp
class Program{

	static void Main(string[] args){		
		Console.WriteLine("Hi, I'm the Base");
		//This just pauses the program for x milliseconds
		System.Threading.Thread.Sleep(5000);

		//instantiating the 2nd Method
		//Class_Name psudo = new Class_Name();
		//Class_Name psudo = new(); *also works 
		Method2 m2 = new Method2;
		
		
	}
}
```

**As simple as it may be, running this won't do anything**

**All this does is connect it. We haven't actually told it do do anything yet**

**Lets make it run the specific method;** 
```csharp
public void Callable_Method(){
...
}
```
Method 1 (Base Method)
```csharp
class Program{

	static void Main(string[] args){		
		Console.WriteLine("Hi, I'm the Base");
		//This just pauses the program for x milliseconds
		System.Threading.Thread.Sleep(5000);

		//instantiating the 2nd Method 
		Method2 m2 = new Method2;
		
		//Calling/Activating the Method itself
		m2.Callable_Method();
		//dont forget this ---> ()
	}
}
```
**The Output will look something like this:**
```
Hi, I'm the Base 
//pauses for 5 seconds
I'm the Second Method
```
-------------------------------------------------------------------
### Parameter Methods
* Parameter Methods are regular methods that have *parameters* added in the () section of the Method_Name
* Used so that information can be sent from one method to the parameter method for it to do *its own*  set of commands
Example
```csharp
class Method3{
 
	public void Callable_Method(/* parameters go here */){
		//commands relating to the parameters go here
	}
}
```

**To put it in simpler terms, the parameters can set as variable that only this specific method can use**

**Lets add parameters to the method above**
```csharp
class Method3{
 
	public void Parameter_Method(int x){
		int sum = 0;
		//just a random equation to show the use of parameters
		sum = x + 3;
		Console.WriteLine(sum);
	}
}
```
**Instantiating it in the Base Method:**
```csharp
class Program{

	static void Main(string[] args){		
		Console.WriteLine("Hi, I'm the Base");
		//This just pauses the program for x milliseconds
		System.Threading.Thread.Sleep(5000);

		//instantiating the 2nd Method 
		Method2 m2 = new Method2;
		m2.Callable_Method();

		//instantiating the 3rd Method
		Method3 m3 = new Method3();
		
		//now we must give information for the parameter method to work with
		//since the parameter is an integer variable, we must give it an integer
		Console.Write("Write a number: ");
		int sendNumber = int.Parse(Console.ReadLine());
		m3.Parameter_Method(sendnumber);
		
		//this should send the number you type to the method
		//it should add 3 to it
		//then Write the sum
	}
}
```
**The Output will look something like this:**
```
Hi, I'm the Base 
//pauses for 5 seconds
I'm the Second Method
Write a number: 5       //number I chose 
8                       //the sum
```
-------------------------------------------------------------------
### Return Methods
**Before talking about Return Methods, we need to discuss Return Types**

**Return Types:**
* these are the types of Methods that can be created i.e.
	* string ---> returns a string
	* int ---> returns a integer
	* double ---> returns a double
	* bool ---> returns true or false
	* void ---> does not need to return anything

Examples
```csharp
public string StringReturn()

public int IntegerReturn()

public double DoubleReturn()

public bool BoolReturn()

public void NoReturn()
```
**Methods with these return types *(except the void return type)* must return a value or piece of information**

**Functions similar to WriteLine() won't work here since it can't return non-variables**
>to return something is to send something back to from where it was called.

For example
```csharp
public string StringReturn(){
	//has to return a string since thats it's return type
	return "Put any string here";
}
```
Alternatively you can do this
```csharp
public string StringReturn(){
	string sendback = "Put any string here";
	return sendback;
}
```
they are essentially the same

-------------------------------------------------------------------
### Applying both in One Method
**Let's say that I want to make a program that has parameters, computations and return values**

**Something similar to a Calculator. An addition calculator would do fine as an example**

**Let's start with the Addition Method with a Integer return type**
```csharp
class CalledProgram{
	//this time we'll use 2 parameters
	public int Addition(int x, int y){
		int sum = x + y;
		return sum;
}
```
**Next the Base Method**
```csharp
class Program{

	static void Main(string[] args){		
		Console.WriteLine("Addition Calculator");
		//This just pauses the program for x milliseconds
		System.Threading.Thread.Sleep(2000);

		int a, b;
		Console.Write("Input the first number: ");
		a = int.Parse(Console.ReadLine());
		
		//the '\n' just means that it will make a new line before writing the "Input the Second....." part
		Console.Write('\n' + "Input the second number: ");
		b = int.Parse(Console.ReadLine());

		//instantiating the Int Addition Method Method 
		CalledProgram cp = new CalledProgram;
		
		//Since there is no WriteLine() funtion within the method itself, we can imbed the activation of Addition in a Console.WriteLine in the Base Method
		Console.WriteLine(cp.Addition(a, b));
	}
}
```
**The Output will look something like this:**
```
Addition Calculator 
//pauses for 2 seconds
Input the first number: 5       //number I chose 
Input the second number: 7      //the second number I chose
12								//the sum
```
