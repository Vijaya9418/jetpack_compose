# jetpack_compose

![jetpack_compose](https://github.com/Vijaya9418/jetpack_compose/assets/56352158/cb8031e7-aa21-4679-bcfb-8b770c1c4ef8)



**What is Jetpack Compose?**

It is an Android's recommended morden toolkit for creating native UI, accelerating UI components. It is a new way of writing UI directly in code.

for example:- If you want to show the list of names in a UI for that if we are using the xml then we will have to go to a lot of process such as, creating a recycler view, adapter and xml file and a lot of code in java file, but if we will use jetpack compose we can do the same thing in seven lines of code.

**Why Compose?**

1. One language for everything, including UI.
2. It proposes a declarative approach. It means the activity does not depend on the xml.<br>
   
   Imperative approach:-
   
   <img width="600" alt="Screenshot 2023-07-01 at 10 11 56 PM" src="https://github.com/Vijaya9418/jetpack_compose/assets/56352158/baff0467-6cdb-4da7-b361-dfe29210bc27">

   Which means, if we want to set any text then we will have to depend on xml to tell that I want to set this text or this layout to the UI, which results in activity depending on xml to do the changes in UI stuff.


    Declarative approach:-

  <img width="191" alt="Screenshot 2023-07-01 at 10 12 09 PM" src="https://github.com/Vijaya9418/jetpack_compose/assets/56352158/b812af4a-bb83-418c-8d6a-52030feb4a92">

   but now with the help of jetpack compose we dont have to depend on any xml to update something on UI as it follows. So an activity contains the list of compose functions which has some states, so if this state changes the whole compose layout rebuilds/ reconstructs.<br>

3. It fixes whats broken and also updates old API's.<br>


**Why is it called compose?**

old Android UI System follows the inheritance approach.

<img width="769" alt="Screenshot 2023-07-01 at 11 01 03 PM" src="https://github.com/Vijaya9418/jetpack_compose/assets/56352158/dbe3fdc9-53b5-4ae2-aaa5-4c704f89554a">

which means in above example a view is a parent of textview and textview is a parent of editText, and view is a grand parent of editText. but in old UI approach their is no system that the same editText can inherit from both textview and view, becuase it doesn't support multiple inheritance.

new Android UI System follows composition approach.

<img width="639" alt="Screenshot 2023-07-01 at 11 04 57 PM" src="https://github.com/Vijaya9418/jetpack_compose/assets/56352158/df06c093-0250-432d-88bf-aa76ef5a3bec">

In this approach, a composable can have child composable, which means, blue comosable methods are the child of green composables and they can have their child composables. So if you want to have child you can create as many composable methods as you want.

**difference between inheritance and composable functions?**

**inheritance:-** It is ** is a relationship** which means a parent can have only one child and a child can have only one parent which is a relationship.

Ex:- editText ------> textView ------> View

**Composable:-** It is **has a relationship** which means a parent can have as many chidlren as they want.

Ex:- Composable function{(Composable function)(Composable function)}










   


  
