# clean-code
chapter 3
- shorter function the better 
- do one thing
- it's content should be in the same abstraction level
- long descriptive naming is better than short meaningless or long comment
- don't use switch case use rather than abstract factory to didn't violate SRP
- function arguments type monatic , dyadic , triads
- command query separation  function should do some thing or return some thing no other thing
- prefer return exception than error code because any exception derived from exception class so any class can deal with it without redeploy class 

# chapter 4
## good comment
- comment is evil but in some time we need it
- some time we need to write comment to display our intent
- clarification in writing comment to show return type of function or type of argument and so on this for external api or library can't edit there name remember naming is better for comment
- write comment for warning consequence if you has function is not thread safe you may need to comment it as it's thread not safe
- to do you may has function but didn't implement yet you can comment it as 
// TODO and the reason
- comment may use to amplify the importance 
## bad comment
- mumbling not important code
- redundant when comment is greater than body best use comment in interface or abstract class
- misleading if comment not informative enough or wrong statement in comment
- mandated comment for every variable in function 
- journal comments example when edit in module you write when edit and why and every edit in module write it 
- noise comment They restate the obvious and provide no new information ex:write comment to describe constructor

## some best 
- closing brace comment comment in end of long function but the better is use shorter function
- attribution by line comment to who write this code the best way source control system 
- commenting out code unused code don't do that !
- non local information don't use information out of current source context



# chapter 5
 ## Vertical
 ### Vertical Openess
  make vertical space between individual piece of code example between two imports or between every function
 ### Vertical Density
  you needn't to add comment between every variables example if you has two variables has relationship you shouldn't break it by comment or space
 ### Vertical Distance
  any two component depends on each other or there is some links should be near with each other
 ### Variable Declaration
  declare variable near of it's use example if you will use varaiable in loop declare it before loop directly
 ### Dependent Function
  if function call another function  so the called function must be behind caller function  or has the same name scheme should be near of each other
 # Horizontal
   ### limit   must be at most 120 charachters
 #ِِ Indentation
# chapter 7
## use unchecked exception
## provide context with exception log
## in terms of class needs example rather catch varity exception you can wrap this class lead to exception and handle it inside warpper class like put handler inside model
## define the normal flow
## if exception lead to specific change in business logic then you should make special case from such object like make PersonNull case from Person and so on .
## don't return null 
## don't pass null

# Boundaries
 ## use thired party library
   Example Sensor s = (Sensor)sensors.get(sensorId ) this is bad design because cast returned item inside client code the best encapuslate it inside Sensor type
     public class Sensors {
private Map sensors = new HashMap();
public Sensor getById(String id) {
return (Sensor) sensors.get(id);
}
//snip
}
