# Appsavio Coding Standards

## Naming Conventions
- **Rule 1:** Use US-English for naming identifiers.

- **Rule 2:** Use Pascal and Camel casing for naming identifiers.
In Pascal casing, the first letter of each word in an identifier is capitalized. For example,
UserStory.
In Camel casing, only the first letter of the second, third, etc. word in a name is capitalized. for example, userStory.

| IDENTIFIER| CASE | EXAMPLE |
|--|--|--|
|Class |Pascal |Account|
|Enum type |Pascal |Severity|
|Enum values |Pascal |Severity.Error|
|Field |camel |listItem|
|Final/Const field |Pascal |MaximumCount|
|Static field |Pascal |RedValue|
|Interface |Pascal |Idisposable|
|Method in Apex,  Java |camel |toString|
|Method in C# |Pascal |ToString|
|Parameter |camel |typeName|
|Property |Pascal |BackColor|
|Trigger |Pascal |SendEmailOnNewAccount|


In Apex, primitive types such as String, Decimal are all classes. So they should be Pascal casing. 

**Rule 3**. Do not use Hungarian notation or add any other type of identification to identifiers. 

Hungarian notation means to put the variable type prior to its name. For example: strName,  intAge. 

**Rule 4**. Do not use an underscore in identifiers. 

Avoid using underscore "\_" in identifiers. It is deprecated in most companies. Exception 

In Apex, underscores exist in the name of every custom field and custom object as “\_\_c” or  “\_\_r”, and in a managed package. When you create a custom field/object,  

Remove the blank spaces in the name to avoid unnecessary underscores. In other words,  blank spaces could appear in the label, but not in the name. 

**Rule 5**. Name an identifier according to its meaning and not its type. Every Identifier should be meaningful. 

**Rule 6**. Use a noun or a noun phrase to name a class, field, or property.

Classes, fields, and properties should be noun phrases.  

The name for a Visualforce page can either be a noun or verb phrase. 

**Rule 7**. Use a verb or a verbal phrase to name a method or trigger. 

Methods and Triggers do actions, so they should be verbal phrases. 

**Rule 8**. Suffix exception classes with Exception. 

Classes derived from Exception are special. They should have the suffix Exception.  For example, DmlException, AcceptLeadException, EsclateCaseException. 

**Rule 9**. Suffix controller classes with Controller 

For example, AssignCaseToDealerController 

**Rule 10**. Suffix test classes with Test, test class name will be Class Name + Test 

For example, we have a controller named AssignCaseToDealerController, the test class name  is AssignCaseToDealerControllerTest 

**Rule 11**. Use a plural noun to name a collection 

For example,  
```java
Set<Id> accountIds = new Set<Id>(); 
```
## Comments

**Rule 1**. Each class/trigger shall contain a header block. 

The description should include useful information about what it is, why you created it, and any  known issues or dependencies: 
```java
/**
* @description : Description of the class
* @author : Author Name
* @created Date : CreatedDate
* @last modified on : LastModifiedDate
* @Test class: Name of Test class for this class
**/
```
You can download the VScode extension named **[Salesforce Documenter](https://marketplace.visualstudio.com/items?itemName=HugoOM.sfdx-autoheader)**

**Rule 2**. Use // for single line comments.  

Use // instead of /\* \*/ if the comments is a single line. 

**Rule 3**. Comments shall be written in US English 

**Rule 4**. Verbs in comments shall be of singular form in the third person. 

**Rule 5**. Write necessary comments, not redundant or noisy. 

For example, everybody knows that is a default constructor: 
```java
public class Whatever{

   //default constructor  
   Public Whatever(){ 

   }
} 
```

**Rule 6**. Separate class members and code sections with a blank line. Remove unnecessary blank lines. 

Blank lines are treated equally as comments. Use them to separate class members.  For example, each method should be separated by a blank line.  

If a method contains more than one operation, separate them with blank lines. Do remove unnecessary blank lines in your code. 

**Rule 7**. Remove the commented lines from production.  

For some reason, we need to comment some lines out when coding Please remember to remove them before deploying them to production. 

**Rule 8**. No need to comment if the code can explain itself. 

## Coding style

**Rule 1**, Put the opening brace “{“ to a new line. 

Java developers used to put the opening brace in the same line of the block definition, like: 
```java
public class Whatever{
   //not recommended  
}
```

This is not about right or wrong, but we make an agreement to put it to the next line, like:  

```java
public class Whatever
{ 
	//recommended  
} 
```
This rule applies to all kinds of code blocks, including class, method, property, if-else, while,  etc.

**Rule 2**, Use blank spaces properly 

Use blank spaces properly as betrayed in the following table: 

|EXPRESSION |BLACK SPACE |EXAMPLE|
| :- | :- | :- |
|Arithmetical operator |1 |b + c|
|Assignment |1 |a = b + c|
|Comparison |1 |a >= b + c|
|Semi-colon |0 |a = b + c;|
|if/while |1 |if (a == b + c)|
|for loop |1 |for (i = 0; i < 100; i++)|
|Unary operator |0|<p>!bool </p><p>-i</p>|
|Increment/Decrement |0|<p>i++ </p><p>--i</p>|
|Ternary operator |1 |(a == null) ? 0 : a|
|Function call |0 |sendEmail(email);|
|Subscript |0 |array[0]|
|Automatic property |1|<p>String Name { get;  </p><p>set; }</p>|


**Example:**  

```java
a = b + c; // right  

a=b+c; // wrong  

a = b + c ; // wrong  

a = (a == null) ? 0 : a; // right  

a = (a == null)?0:a; // wrong  

for (i = 0; i < 10; i++) // right  

for(i=0;i<10;i++) // wrong  

for (i = 0; i < 10; i ++) // wrong 

a = -- b; // wrong  

a = --c; // right  

a = - b; // wrong  

a = -b; // right  

public String Name{get;set;} // wrong  
public String Name { get; set; } // right 
```
 
**Rule 3**. SOQL and SOSL should be readable on the screen without much scrolling so make sure to separate lines in SOQL to make it more readable in a single glance.

**Rule 4**. All flow control primitives (if, else, while, for, do, switch) shall be followed by a block, even if it is empty. 

Example: 
```java
If () {}
```

**Rule 5**.  A Tab space should be of four spaces no more no less. Change your IDE settings to set the Tab spaces to Four.

##SOQL Rules
**Rule 1:** 
The SOQL keywords should be in UPPERCASE for example.

```java
[SELECT Id, Name FROM Account WHERE Website = 'Test'] //Recommended

[select Id, Name From Account where Website = 'Test'] 
//Not Recommended
```

**Rule 2:** 
It is recommended to have a single query on an Object in a Single piece of code. The developer should get the records to be used at once and store them in containers accordingly. 

**Rule 3:** 
The Query should contain a valid *Where clause* condition to minimize the records returned from the query. The more records Query returns the more time Apex transaction will take. Also, there's a limit of 50000 records returned per Query. So it's better to filter data as much as possible in the Query itself.

**Rule 4:** 
It is not recommended to store the Query resulted records in a list directly if there can be lots of records. It will impact the heap size and may terminate the transaction. A better way would be to use Query as the Value parameter of the forEach loop.

```java
//Not Recommend
List<Account> acctList = [SELECT Id FROM Account]; 
for( Account acct : acctList ){
	//Process here
}


//Recommend
for( Account acct : [SELECT Id FROM Account] ){
	//Process here
}
```

**Rule 5:** 
Avoid querying fields that are of no use for your logic. It will increase the Transaction time and Heap memory with unnecessary data.

**Rule 6:** 
Utilize child queries instead of Querying child records in another Query.

```java
//Not Recommend
List<Account> acctList = [ SELECT Id, Name FROM Account ];
List<Opportunity> oppList = [ SELECT Id, Name 
			      FROM Opportunity 
			      WHERE Account Id IN: acctList];		

//Recommend
List<Account> acctList = [ SELECT Id, Name
			 ( SELECT Id FROM Opportunities )
			   FROM Account ];
```

**Rule 7:** 
Maintain the spaces

```java

//Recommend
[ SELECT Id, Name FROM Account Where Id IN: keySet() ];

//Not Recommend
[SELECT Id,Name FROM Account Where Id IN:keyset()];

```

## Trigger Standards

**Rule 1:**
Keep the one Trigger per Object structure. Create a Trigger Handler class that further process the business logics.

**Rule 2:**
Keep Trigger clean. Keep as less logic as possible inside Trigger file and move all logic into TriggerHandler and Service classes.

**Rule 3:**
Trigger Name should follow Naming convention like:

> 'Trigger'+ObjectName<br/>
>  For Example TriggerOpportunity or TriggerAccount

**Rule 4:**
Trigger should have separate If sections for each session. For example

```java

if( Trigger.isBefore ){

	if( Trigger.isInsert ){
		//Call all Before Insert Methods here
	}

	if( Trigger.isUpdate ){
		//Call all Before Insert Methods here
	}

	if( Trigger.isDelete ){
		//Call all Before Insert Methods here
	}

}

if( Trigger.isAfter ){

	if( Trigger.isInsert ){
		//Call all After Insert Methods here
	}

	if( Trigger.isUpdate ){
		//Call all After Insert Methods here
	}

	if( Trigger.isDelete ){
		//Call all After Insert Methods here
	}

}


```
