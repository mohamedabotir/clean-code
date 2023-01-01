# clean-code
## chapter 2
meaningful names
### use intention revealing names 
example 
int d; // elapsed time in days
The name d reveals nothing. It does not evoke a sense of elapsed time, nor of days. We
should choose a name that specifies what is being measured and the unit of that measurement:
int elapsedTimeInDays;
### avoid disinformation 
Programmers must avoid leaving false clues that obscure the meaning of code
Do not refer to a grouping of accounts as an accountList If the container holding the
accounts is not actually a List it may lead to false conclusions. So accountGroup or
bunchOfAccounts or just plain accounts would be better.
### use pronounceable names
example 
class DtaRcrd102 {
private Date genymdhms;
private Date modymdhms;
private final String pszqint = "102";
/* ... */
};
to
class Customer {
private Date generationTimestamp;
private Date modificationTimestamp;;
private final String recordId = "102";
/* ... */
};
### use searchable names 
The length of a name should correspond to the size of its scope
### avoid encoding
### hungarian notation 
avoid it experssion:variablenameVariableType example:phoneString
### member prefixes
### interface and implementation
avoid name your interface as IShapFactory and class ShapeFactory use rather ShapeFactory for interface and ShapeFactoryImpl as class better because you want to let reader know type only when use ShapeFactory interface
### avoid mental mapping
Readers shouldn’t have to mentally translate your names into other names they already
know. This problem generally arises from a choice to use neither problem domain terms
nor solution domain terms.
### Class 
Classes and objects should have noun or noun phrase names like Customer, WikiPage,
Account, and AddressParser. Avoid words like Manager, Processor, Data, or Info in the name
of a class. A class name should not be a verb.

### function
Methods should have verb or verb phrase names like postPayment, deletePage, or save.
Accessors, mutators, and predicates should be named for their value and prefixed with get,
set, and is according to the javabean standard.4
string name = employee.getName();
customer.setName("mike");
if (paycheck.isPosted())...
When constructors are overloaded, use static factory methods with names that
describe the arguments. For example,
Complex fulcrumPoint = Complex.FromRealNumber(23.0);
is generally better than
Complex fulcrumPoint = new Complex(23.0);
Consider enforcing their use by making the corresponding constructors private.
### don't be cute
If names are too clever, they will be
memorable only to people who share the
author’s sense of humor
### pick one word per concept
Pick one word for one abstract concept and stick with it. For instance, it’s confusing to
have fetch, retrieve, and get as equivalent methods of different classes
### don't pun
Avoid using the same word for two purposes. Using the same term for two different ideas
is essentially a pun.
### Add Meaningful Context 
If you follow the “one word per concept” rule, you could end up with many classes
that have, for example, an add method. As long as the parameter lists and return values of
the various add methods are semantically equivalent, all is well.
However one might decide to use the word add for “consistency” when he or she is not
in fact adding in the same sense. Let’s say we have many classes where add will create a
new value by adding or concatenating two existing values. Now let’s say we are writing a
new class that has a method that puts its single parameter into a collection. Should we call
this method add? It might seem consistent because we have so many other add methods,
but in this case, the semantics are different, so we should use a name like insert or append
instead. To call the new method add would be a pun.
### use solution domain names
example JobQueue,ShapeFactory ,etc.
### use problem domain names
When there is no “programmer-eese” for what you’re doing, use the name from the problem domain. At least the programmer who maintains your code can ask a domain expert
what it means.
## chapter 3

- shorter function the better
- do one thing
- it's content should be in the same abstraction level
- long descriptive naming is better than short meaningless or long comment
- don't use switch case use rather than abstract factory to didn't violate SRP
- function arguments type monatic , dyadic , triads
- command query separation  function should do some thing or return some thing no other thing
- prefer return exception than error code because any exception derived from exception class so any class can deal with it without redeploy class

## chapter 4

### good comment

- comment is evil but in some time we need it
- some time we need to write comment to display our intent
- clarification in writing comment to show return type of function or type of argument and so on this for external api or library can't edit there name remember naming is better for comment
- write comment for warning consequence if you has function is not thread safe you may need to comment it as it's thread not safe
- to do you may has function but didn't implement yet you can comment it as
// TODO and the Reason of function 
- comment may use to amplify the importance

### bad comment

- mumbling not important code
- redundant when comment is greater than body best use comment in interface or abstract class
- misleading if comment not informative enough or wrong statement in comment
- mandated comment for every variable in function
- journal comments example when edit in module you write when edit and why and every edit in module write it
- noise comment They restate the obvious and provide no new information ex:write comment to describe constructor

### some best

- closing brace comment comment in end of long function but the better is use shorter function
- attribution by line comment to who write this code the best way source control system
- commenting out code unused code don't do that !
- non local information don't use information out of current source context

## chapter 5

### Vertical

#### Vertical Openess

  make vertical space between individual piece of code example between two imports or between every function

#### Vertical Density

  you needn't to add comment between every variables example if you has two variables has relationship you shouldn't break it by comment or space

#### Vertical Distance

  any two component depends on each other or there is some links should be near with each other

#### Variable Declaration

  declare variable near of it's use example if you will use varaiable in loop declare it before loop directly

#### Dependent Function

  if function call another function  so the called function must be behind caller function  or has the same name scheme should be near of each other

## Horizontal

### limit   must be at most 120 charachters

### Indentation

## chapter 7

### use unchecked exception

### provide context with exception log

### in terms of class needs example rather catch varity exception you can wrap this class lead to exception and handle it inside warpper class like put handler inside model

### define the normal flow

### if exception lead to specific change in business logic then you should make special case from such object like make PersonNull case from Person and so on

### don't return null

### don't pass null

## Boundaries Chapter 8

### use thired party library

   Example Sensor s = (Sensor)sensors.get(sensorId ) this is bad design because cast returned item inside client code the best encapuslate it inside Sensor type
     public class Sensors {
private Map sensors = new HashMap();
public Sensor getById(String id) {
return (Sensor) sensors.get(id);
}
//snip
}

## Chapter 9

### Three Law Of TDD

- First Law You may not write production code until you have written a failing unit test.
- Second Law You may not write more of a unit test than is sufficient to fail, and not compiling is failing
- Third Law You may not write more production code than is sufficient to pass the currently failing test

### Keeping Tests Clean

 if you write test than nothing this is bad approach as this will be overhead in production when you decide to change production code this will make test code goes fail and you may ignore make production code more cleaner as you afraid of test code fails.

most important in clean test readability.

### One Assert Per Test

### Single Concept Per Test

### Clean Test F.I.R.S.T

- Fast Tests should be fast. They should run quickly. When tests run slow, you won’t want to run them frequently.

- Independent Tests should not depend on each other. One test should not set up the conditions for the next test.

- Repeatable Tests should be repeatable in any environment. You should be able to run the
tests in the production environment

- Self-Validating The tests should have a boolean output. Either they pass or fail. You
should not have to read through a log file to tell whether the tests pass.
- Timely The tests need to be written in a timely fashion. Unit tests should be written just
before the production code that makes them pass. If you write tests after the production
code, then you may find the production code to be hard to test.

## chapter 10 class
### class should be smaller how we measure it not as function we count physical line but by class responsability 
### Cohesion the more instance variable methods used the more class cohesion
### maintaining Cohesion if we have function own 4 variables and we want to extract method from it now we need to upgrade declaration level of this variable to instance level now we declare 4 instance varaiables to be used by few function this lead to decrease cohesion and as we see keep function small may lead to create new class to demonestrate such scenario and increase cohesion.  

### Organization for Change you should know any software in any time need to be modified so we should know how to apply OCP well to deal with modification because if we didn't put in consider class will need to update may be test will fail if we modify class or another depedant funcionality goes down because of this modification and also this violate ocp principal

## Chapter 12
Kent Becks Rules
- Runs All Tests
- Contains no Duplication
-  Express intent of programmer 
- Minimizes number of classes and methods
you may need to use template method 
to shrink big methods do multiple task as it elemenate duplication
## Chapter 13
concurrency decouple what get done from when get done 

#### "Decoupling what from when can dramatically improve both the throughput and structures of an application. From a structural point of view the application looks like many little collaborating computers rather than one big main loop. This can make the system easier to understand and offers some powerful ways to separate concerns.
(Page 209). "
### Concurrency defense Priniciples
- Single Responsibility Principle
concurrent system is enough complex so you should make each module express it self only
(Page 212). 
- Limit scope Of Data 
protect shared data in critical section of your code 
- Copies of Data A good way to avoid shared data is to avoid sharing the data in the first place. In some situations it is possible to copy objects and treat them as read-only. In other cases it might be possible to copy objects, collect results from multiple threads in these copies and then merge the results in a single thread.
(Page 212). 
- make your thread independant as possible
![image](https://user-images.githubusercontent.com/52336027/205496334-4b02aa6c-64df-4a6f-8f53-f6e3aca74966.png)
popular problem 
- producer consumer
https://learn.microsoft.com/en-us/dotnet/standard/parallel-programming/how-to-implement-a-producer-consumer-dataflow-pattern
- readers - writers
- dining philosophers

### Shut-down
Recommendation: Think about shut-down early and get it working early. It’s going to take longer than you expect. Review existing algorithms because this is probably harder than you think.
(Page 217). 
### Testing
Recommendation: Write tests that have the potential to expose problems and then run them frequently, with different programatic configurations and system configurations and load. If tests ever fail, track down the failure. Don’t ignore a failure just because the tests pass on a subsequent run. That is a whole lot to take into consideration.
Here are a few more fine-grained recommendations:

• Treat spurious failures as candidate threading issues. 

• Get your nonthreaded code working first.

(Page 217). 

• Make your threaded code pluggable
Write the concurrency-supporting code such that it can be run in several configurations

(Page 218). 

• Make your threaded code tunable. 


• Run with more threads than processors. 

• Run on different platforms. 

• Instrument your code to try and force failures.
It is normal for flaws in concurrent code to hide. Simple tests often don’t expose them. Indeed, they often hide during normal processing. They might show up once every few hours, or days, or weeks!
There are two options for code instrumentation: 

• Hand-coded

• Automated
 
(Page 219). 

(Page 218). 

## chapter 14
you will know how to clean code when write bad code and try clean it

## chapter 15
And so we have satisfied the Boy Scout Rule. We have left this module a bit cleaner than we found it. Not that it wasn’t clean already. The authors had done an excellent job with it. But no module is immune from improvement, and each of us has the responsibility to leave the code a little better than we found it.

(Page 296). 

## chapter 17
### comment
- inappropriate information : information shouldn't be related to developemtn
- obsolote comment : comment became so old so we need to replace it 
- redundent comment : describe some thing describe it self 
- poor written comment : write comment carefully and with correct grammer 
- commented out code : code which one day being comment and every one say one day programmer should need it ,this day will never come !
### environment
- build requires more than one step ?! should be able to build project by using one command only
- test requires more than one step ?! you should be able to run all test cases by hit one command 
### functions
- too many arguments : should have small number of arguments one ,two ,three ,greater than this you should ask question
- output argumen : user expect to insert input not affect or change state of object by using input
- flag argument : this may lead to make function do multiple thing and this shouldln't be
- dead function : function never used this is wastful so you should delete it
### General
- G1:multiple language in one source file : source file must contain one and only one language
- G2:obvious behavior unimplemented : if you expect some thing in code reasonably and didn't find it you will lost others trust
- G3:Incorrect Behavior at the Boundaries : programmer say function should work but this can behave incorrect in some cases and other boundary
- G4:Overriden Safties : turning of failing tests and tell your self you will get them to pass later
- G5:Eliminating Duplication one the most important rule in software design and some people called that dry principal and you can eliminate dublication by using switch case or patterns such as template method or strategy pattern
- G6: Code at Wrong level of abstraction we should seperate higher level abstraction from low level
- G7: Base Class Depending on Their Derivatives
- G8: Too many information with may small interface can you do many with little better than interface with unused or unrelated funcion may implement 
- G9: Dead code code doesn't executed or in if condition can't happen ever
- G10: vertical separation variables and function should declare near to where  it used 
- G11: inconsistancy if you write your code as a pattern like ProcessAdd you can write another like ProcessMultiplication
- G12: Clutter constructor never use and variables aren't used and comment that add no information ,function never called
- G13: artificial coupling don't couple two module didn't has the same direct purpose anothr example say we have global variable we shouldn't include it within general purpose class so we enforce more classes to use it
- G14: feature envy when we use object of other class to manipulate the data within object so we should separate this method 
### example 

public class HourlyPayCalculator { 
public Money calculateWeeklyPay(HourlyEmployee e) {
int tenthRate = e.getTenthRate().getPennies();
int tenthsWorked = e.getTenthsWorked();
int straightTime = Math.min(400, tenthsWorked); 
int overTime = Math.max(0, tenthsWorked - straightTime);
int straightPay = straightTime * tenthRate;
int overtimePay = (int)Math.round(overTime*tenthRate*1.5);
return new Money(straightPay + overtimePay); } }
(Page 324). 
### solution 
public class HourlyPayCalculator {
public Money calculateWeeklyPay(HourlyEmployee e) { 
int tenthRate = e.getTenthRate().getPennies();
int tenthsWorked = e.getTenthsWorked();
int straightTime = Math.min(400, tenthsWorked);
int overTime = Math.max(0, tenthsWorked - straightTime);
int straightPay = straightTime * tenthRate;
int overtimePay = (int)Math.round(overTime*tenthRate*1.5);
return new Money(straightPay + overtimePay);
} }
(Page 324). 
