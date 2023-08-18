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



<!-- ANCHOR 8/15 -->

<!-- NOTE const, creates a variable that is immutable (cannot be changed) -->
const areas = ['🏎️','🌑','✨','🚘']

const animals = [
{
    name: 'Oslo',
    emoji: ':)',
    favoriteFoods: ['Banana','Peanuts'],
    currentArea: "spain"
},

{
     name: 'steve',
    emoji: '🏎️',
    favoriteFoods: ['sushi','fish'],
    currentArea: "France"
},

{
     name: 'Manny',
    emoji: '😎',
    favoriteFoods: ['socks','meat'],
    currentArea: "Brazil"
}


]


for(let i = 0; i < animals.length; i++){
    let animal = animals[i]
    console.log(animal.name, animal.emoji)
}

animals.forEach()

animals.forEach(() => {
    console.log('DoiNg stuff')      //logs DoiNg stuff 5 times
})


animals.forEach((Animal) => {
    console.log(animal.name, animal.favoriteFoods)
})


areas.forEach((area) => {
    console.log(area)
   let inArea = animals.filter((animal) => animal.currentArea == area)  //filter creates and array of elements that match the condition
   let animalEmojis = inArea.map((animal) => animalEmoji)   //Map creates an array of transformed results specified
   document.getElementById('area').innerText = animalEmojis.join(', ')      //join turns elements in the array into a string
})

function party(){  
    animals.forEach(animal => {
        let newArea = area[o]
        animal.currentArea = newArea

    })
}


function drawAnimals() {
    areas.forEach((area) => {
    console.log(area)
   let inArea = animals.filter((animal) => animal.currentArea == area)  //filter creates and array of elements that match the condition
   let animalEmojis = inArea.map((animal) => animalEmoji)   
   document.getElementById('area').innerText = animalEmojis.join(', ')      
})
drawAnimals()
}

       //Invoke the function you want to run on load at the bottom




       let inLocation = people.filter(peep => peep.location == '🏛️')
console.log('in location', inLocation)


<!-- ANCHOR 8/16 -->

let cartElem = document.getElementById('cart')
let totalelm = document.getElementById)

    function buyCaprese(){
        //Find the sandwich I want to buy... find the caprese
        //increase how many sandwiches I have... increase the quantity
        //add the sandwich to the cart...update the DOM
        <!-- NOTE heres the story for this function -->
        <!-- Look at all the sandwiches , and find the one sandwich => where it's name == 'caprese' -->

    let caprese = sandwiches.find(sandwich => sandwich.name == 'caprese')
    caprese.quantity++
        console.log('Buying Caprese', caprese)
    cartElem.innerHTML = ``
    }   

let template = ''



    function drawCard(){                Put this funtion in buyCaprese() at the very bottom
        //look at all the sandwiches
        //do i have one of these sandwiches?? check if the quantity is greater than 0 

        sandwiches.forEach(sandwich = > {
            if(sandwich.quantity > 0) {
                template  += `  `
            }


        })
    cartElem.innerHTML = template
    }



    function buySandwich(sandwichName){
       let foundSandwich = sandwiches.find(sandwich => sandwich.name == sandwichName)
       foundSandwich.quantity++
       drawCart()
    }


let total = 0

    function drawTotal(){       //put this  in the bottom of the drawCart()
        <!-- TODO look at all the sandwiches -->
        <!-- TODO While looking at the sandos, check if they are in the cart... is the quantity > 0 -->
        <!-- TODO If it is, how many do i have * how much do they cost... multiply quantity and price -->
        <!-- TODO add the multiplied value to a total -->
        <!-- TODO update the DOM -->

    

        sandwiches.forEach(sandwich => {
            if(sandwich.quantity > 0) {
             total += sandwich.quantity * sandwich.price
            }
        })
        totalElm.innerText = total.tostring()
    }


function removeSandwich(sandwichName){
    let foundSandwich = sandwiches.find(sandwich => sandwich.name == sandwichName)
    foundSandwich.quantity--

    drawCart()
}



<!-- ANCHOR 8/17  -->

 function decreaseOsloHunger(){
    let oslo = animals.find(animal => animal.name == 'oslo')
    oslo.hunger--

    if(oslo.hunger = 0) oslo.hunger = 0
    console.log(oslo)
 }


function feedOslo(){
    let oslo = animals.find(animal => animal.name == 'oslo')
    oslo.hunger++ 
    if(oslo.hunger >= 100) oslo.hunger = 100
}



1000 miliseconds = 1 second  

 setInterval(decreaseOsloHunger,1000)



