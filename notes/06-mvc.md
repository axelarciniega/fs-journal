# MVC
<!-- SECTION 8/21 -->

bcw create 

started by creating a file in the models called character.js

class Character{
    name

    role

    health

    maxHealth

    constructor(newName, newRole, newHealth){
        console.log('Building a character')

    <!-- NOTE THIS IS A CONTEXT FOR A CLASS INSTANCE TO LOOK ITSELF -->
        this.name = newName 
        this.role = newRole
        this.health = newHealth
    }

    greeting(){
    console.log('Hello, My name is', this.name)
    }

}


<!-- SECTION 8/22 -->
1. started off by making a file the model which then created a class with constructor then went to the appstate
2. created a file in the controller, from there he exported class with a constructor
3.  Put the controller in the router
4. went to controller.js and created a draw list (DO NOT forget to update dom with the draw function)
5. created get ComputeRarityStyle in his gachamon.js   
6. went to his controller and created a select function called selectGachamon
7. went back to his gachamon set an onclick on his button (onclick = "app.GachamonsController.selectGachamon('${this.name}')")
8. went to services and created a file and did 'classService{}' on the bottom of that he created an 'export const gachamonsService = new GachamonsService()'
9. then went to his controller put 'gachamonsService.selectGachmon(name)'
10. in AppState he created an active
11. went to services app.state 



created an empty array for the onces he collect in his appstate, also did 
his draw function is in his controller 

in service create a function to save the collected ones

loadState is in the appstate in the init() function- this is too keep that ones that were collect still loaded on the page

<!-- SECTION  8/23-->
1. this is in car.js
 export class Car{
    constructor(data){
        this.make = data.make
        this.name = data.year
        this.imgUrl = data.imgUrl
        this.model = data.model
        this.price = data.price
        this.listingDate = new Date()
    }
 }

 2. straight to appstate to make cars
 cars = [
    new car({
        make:'BMW',
        model: '335i'
        year: 1973,
        imgUrl: 'url here'
        price: 50000,
    })

 ]

 3. made a new controller 
 export class CarsController{
    constructor(){
        console.log('we got cars' appstate.cars)
    }
 }

 4. make a new path in the router
 {
    path: '#/cars'
    controller: carsController,
    view: ``
 }

 5. straight to html to make an anchor which the anchor is using the path for the car controller

 6. in carsController 
 //it is right above the export class CarsController
 function _drawCars(){
    let cars = appstate.cars
    let content = ''
    cars.forEach(car => content += car.CardTemplate)
 }

 <!-- load _drawCars in the constructor of carsController! -->
7. in the router lets work on the view of #/cars
view: /*html/`
    section id ='cars'

`

8. it can be helpful hard coding on the index.html

9. in car.js 
get cardTemplate(){
    return `
    put html that you hard coded here
    `
}


10. in carController which is in constructor
createCar(){
    window.event.preventDefault()    //prevents the page from being refreshed when clicking submit
    
    <!-- REVIEW this is the manual way to do it -->
    <!-- const form = window.event.target
    const formData = {
        make: form.make.value
        model:form.model.value
        year:
        imgUrl: -->


        const fromData = getFormData(formEvent)
    if(formData.isNew == 'on'){
        formData.isNew = true // did this part later on
    }
        carsService.createCar(formData)
    }
}

11. created a service file
class carsService{
    let newCar = new Car(formData)
    appState.cars.push(newCar)
    console.log(formData)
    appState.on('cars') //NOTE emits change from appstate.cars so that our listener can catch the page 
}

export const carsService = new carsService()

12. creating function in carsService 
function _saveCars() {
    saveState('cars', AppState.cars)
}

put this function right in the class carsService


13. in appstate
cars = loadState('cars', [car])
14. this in the car.js we just added it in above this.make
this.id = generateId()

15. adding a remove button in the card template (dont forget the onclick)
16. in the controller
async deleteCar(carId){
    if( await pop.confirm)('are you sure'){
    console.log('deleting')
    carsService.deleteCar(carId)

    }
}

17. in carsService(carId){
    let found car =appstate.cars.find(car => car.id ==carId) //NOTE this will be important step later 
    console.log('found')
    appstate.cars.filter(car=>car.id != carId)
}

18. invoke _saveCars in deleteCar so that when you delete its made sure its deleted from local storage