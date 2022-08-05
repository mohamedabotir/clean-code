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
- misleading if comment not informative enough or wrong comment
- mandated comment for every variable in function 

