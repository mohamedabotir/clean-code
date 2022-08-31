# clean-code

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

## Class
### class should be smaller how we measure it not as function we count physical line but by class responsability 
### Cohesion the more instance variable methods used the more class cohesion
### maintaining Cohesion if we have function own 4 variables and we want to extract method from it now we need to upgrade declaration level of this variable to instance level now we declare 4 instance varaiables to be used by few function this lead to decrease cohesion and as we see keep function small may lead to create new class to demonestrate such scenario and increase cohesion.  

### Organization for Change you should know any software in any time need to be modified so we should know how to apply OCP well to deal with modification because if we didn't put in consider class will need to update may be test will fail if we modify class or another depedant funcionality goes down because of this modification and also this violate ocp principal

