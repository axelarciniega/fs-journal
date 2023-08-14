# JavaScript

script src : links the js to the html

Scripts are typically at the end of the body. Since they take the "longest to load"
 <!-- SECTION -->
 <!-- Primitive Data Type, when primitive are passed, they only move their value to a new separate source -->
 <!-- js uses floats for their numbers -->
 <!-- strings -->
 let jeremyLie = 6
 let greeting = "Hello"
<!-- booleans -->
 let boolean = true
 //truthy falsey, are not true or false literally, but can act as true or false for conditions
 let falseNumber = 0
 let trueNumber = -3 //literally any number other than 0

 let falseString = ''  // nothing between the quotes
let trueString = ' '   // any string with any character becomes true

let moreFalse = undefined
let anotherFalse = null

let moreTrue = []   //even if an array or object are empty, they are seen as true
let anotherTrue = {}


 <!-- **NOTE - strings can span multiple lines. Only backtick can move from line to line -->
 <!-- no values -->
 let noValue 
 let unknownValue = undefined   //writing this out is wack//

 let knownValue = null // I KNOW there is no value

<!-- SECTION Reference Data Types, when reference types are passed they share the same source -->
<!-- arrays, store data by position -->
let arr = ["Jack Sparrow","Black Beard","Luffy"]       arr[0] //Jack Sparrow
let nums = [1, 3, 6, 8]


<!-- object store data using KEY : VALUE pairs -->
let obj = {
    cat:"Georgie",
    dog:"Dipper",
    bird:"brins"
}                               obj.cat //Georgie




<!-- SECTION functions -->
<!-- Are blocks of code to store and run later -->

function sayHello(){
    console.log('Hello there')
}

//Parameters
//temporary variables accessible to only this function while it is executing
function addNumbers(3,2){
    console.log(x + y)
    return x + y //returns values
} //addnumber()         //5


onclick = "sayHello()"   

<!-- SECTION APP time -->

function clickButton(){
    console.log('clicked Button')
}

thingsClicked += 🏎️ 

let elm = document.getElementById('things-clicked') //things-clicked is the id in the row in html
elm.innerText = thingsClicked

