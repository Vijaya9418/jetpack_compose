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

**inheritance:-** It is ** is a relationship** which means a parent can have only one child and a child can have only one parent which is a relationship.It is an old UI system.

Ex:- editText ------> textView ------> View

**Composable:-** composition It is **has a relationship** which means a parent can have as many chidlren as they want. It is a new UI system

Ex:- Composable function{(Composable function)(Composable function)}


//this is a class<br>
public class Person constructor(public val age: Int){

//this is a method

      public talk(){
      val message:String
      message = "This is a basics of kotlin $age"
      println(message)
      }
      
}

fun main(args:Array<String>){

val inputPerson: Person = Person(10)

inputPerson.talk()

}



**Inheritance in kotlin:-**


package com.example.jetpack_ui_basics

//this is a class<br>
//by default classes and methods are public and final in kotlin which means we cannot inherit or override those classes and methods.<br>
// if we want to inherit the class and override the method we can use open keyword in front of them which will allow the inheritance and overriding.<br>

public open class Person constructor(public val age: Int){

//this is a method

    public open fun talk(){
        val message:String = "This is a person class $age"
        println(message)
    }

}

public final class Teacher constructor(age:Int): Person(age){

    override fun talk(){
        val message:String = "This is a teacher class $age"
        println(message)
    }
    fun tech(){
        println("I teach")
    }

}

fun main(args: Array<String>){

    //if we have declared any variable with val which means it cannot be modified once declared
    //bucket can only be filled once.
    
    val inputPerson: Person = Person(10)

    inputPerson.talk()

    //if we have declared any variable with var which means it can be modified 
    //bucket can be filled again and again
    
    var teacher = Teacher(20)
    teacher.talk()
    teacher.tech()

    teacher = Teacher(40)
    teacher.talk()
}


**Jetpack compose is built on composables:-**

Composable functions are the basic building blocks for declaring any UI components.



class MainActivity : ComponentActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        /* why setContent does not have any paranthesis?
        * because if we will go inside the setContent it has two parameters one is parent where its default value is already defined
        * and second parameter is composable function which states that a function inside another function.
        * so there is a rule in kotlin that if you are passing a function as a parameter and it is a last parameter so instead of using paranthesis we can directly use the curly braces.
        */

        setContent {
            Jetpack_UI_basicsTheme {
                // A surface container using the 'background' color from the theme
                Surface(modifier = Modifier.fillMaxSize(), color = MaterialTheme.colorScheme.background) {

                    //we can also pass the compsables directly here instead of greetings we can pass Text composable directly here

                   // GreetingText("Android")
                    GreetingButton()
                }
            }
        }
    }
}

/*
it is a composable function which we created for setContent as it requires composable function
we define this @Composable to any function or lambda to indicate that it can be used as a part of composition
 */

@Composable

/*
composable function name always starts with capital letter, because they are not standalone functions
 they are viewed as widgets, components of the UI
 */

fun GreetingText(name: String, modifier: Modifier = Modifier) {

    //this is also a composable function which we can add inside the composable function
    //which means we can have composable functions inside functions

    Text(
            text = " Hello $name!",
            modifier = modifier
    )
}


@Composable
fun GreetingButton(){

     Button(onClick = { println("This is a button") }, modifier = Modifier
         .width(180.dp)
         .height(80.dp)) {
         GreetingText(name = "button")
         
     }
}

/*
Preview is used to display your UI in the right panel of your android studio which you have made through composable
 So If we want to show any peview then we have to use a preview annotation , we should have a composable function
 and inside that we should have the composable function similar to the function which we have used inside set content
 */

@Preview(showBackground = true)
@Composable
fun GreetingPreview() {

    Jetpack_UI_basicsTheme {
       // GreetingText("Android")

        GreetingButton()
    }
}


**Core UI Elements of compose:-**

surface composable -------> wrap content of composable -------> align composable -------> row,column,box composables ------>layouts with row and columns -----> extract composables for reuse ------> arrangements for rows and columns ------> combine and nest rows with columns.



**Adding surface composables to the screen:-**

jetpack follows declarative approach, which means it does not depend on any other files to update the UI. 

In this data flows from top to bottom. Screen --> NewsFeed --> Story Widget.

for example:- If user is interacting with the UI and giving some input, then it will first go to the screen, then newsfeed and then inside hidden files story widgets.


![data declarative appraoch](https://github.com/Vijaya9418/jetpack_compose/assets/56352158/f6252703-6361-4ebf-8061-d21b5d0424ad)


And In case of events it flows from bottom to top. Screen <-- NewsFeed <-- Story Widget.

for example:- onclick call back then it has to go through with the story widgets and then news feed widget and then to the screen composable.

![declarative apprach](https://github.com/Vijaya9418/jetpack_compose/assets/56352158/150665c7-3ad9-4363-8780-43be5a11e3c3)


Jetpack compose is based on dynamic concept, which means it can have different outputs if the given input values has changed.

**Recomposition:-**

It is a very imp topic because recomposition allows the whole UI to be rebuilt and the states to be changed. In the Imperitive approach we had some view, widgets to change their values but in jetpack compose we have recomposition, so whatever we will pass to the activity setcontent method, the parent composable will be rebuild, and then their child.So if the input will change then output will change.

**State:-**

State in jetpack compose is the heart of UI construction it allows us to update the UI . It is a part of recomposition.In order to trigger the recomposition we should have state.
It is any value that can change over time.

Our dataflow is unidirectional:-
Event<br>
Update state<br>
Display state<br>

![state in jetpack compose](https://github.com/Vijaya9418/jetpack_compose/assets/56352158/856d6e73-49d4-4e58-be62-cca746c98df2)

to update the list we can use the state which is mutableStateListOf which will update the list on button ckick<br>.
Now we dont want to lose the updated list so we will use remmber which is a special block which will allow the state will be remmembered over recomposition.




ViewModel:-

It is a class that is responsible for preparing and managing the state of UI for Fragments and Activities.

![ViewModel in jetpack compose](https://github.com/Vijaya9418/jetpack_compose/assets/56352158/49881e00-3459-4b54-bd2d-b8b76d78d58f)


LiveData:-

It is a lifecycle-aware observables data holder. which means it holds some data(lists,mutable lists) but is more reactive of nature, it react to the changes.

for example:- we have fragments and activities and we are using live data, so live data will observe the value and will notify the activities or fragments thgat their is a change, so they will continuesly gets the update whenever their is a change.


![live data](https://github.com/Vijaya9418/jetpack_compose/assets/56352158/eeaa2e4e-2b56-4aac-97af-a5eaaba85c62)


**LazyColumn:-**

It is similar to the recycler view which helps you to display the column in the form of a list and recyle or reuse its item, which saves its memory.

Lets suppose we have a list of items and if we are using list view it will load all those 100 items and which will not be fast and it will take lot of memory, but if we will use lazy column then it will load only those items which is visiblw in the UI and then if we want to load another items we can scroll it and it will load.

It is helpful in dynamic loading of data.

Composable screen:-

Composable screens are lightweight UI just like the fragments, which we can add in a single activity and have multiple composable screen.

Navigation component:-

https://github.com/Vijaya9418/Navigation-in-android

**what is remember and state function in jetpack compose?**

    we use remember function to retain and manage the state within composable function, this is useful when you want to store and manage some local state within the composable it will remember the state for example you have a mutable state of list - vijaya and gaurav and a textfield in which we are adding the value Geet now for the time it will be get addedand visible to your screen but when the recomposition will takes place then that data will be lost that geet field will not be get added it will reset to its initial value


    a state is any value that can change over time, so if want to add any new value in the list of item
     we will use mutablestateof, when the values changes the recomposition will happen and Ui will be updated

    val rememberedMeals: MutableState<List<MealsResponse>> = remember {
        mutableStateOf(emptyList<MealsResponse>())
    }




















   


  
