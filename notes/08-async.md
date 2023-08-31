# Async
<!-- SECTION 8/29 -->

when you do bcw create use mvc-auth

1. starts by creating all the files that we are going to need

2. then started working on the router, making a new path for the car page

3. goes to controller and start making a method
 async getCars(){
    try{
        await carsService.getCars()
    }catch(error){
        Pop.error(error.message)
    }
 }

 4. in the cars service
const sandboxApi = axios.create({
    baseURL: "url here"
    timeout: 8000
})

 async getCars(){
    const response = await _sandboxApi.get('api/cars')
    console.log(response.data)

 }


 5. in the car.js
 constructor(data){
    this.id = data.id
    this.make = data.make
    this.model = data.model
    <!-- this.creator = data.creator don't really need this one -->
    this.creatorId = data.creator.id
    this.creatorName = data.creator.name
 }

 6. straight to service 
 
async getCars(){
    const response = await _sandboxApi.get('api/cars')
    console.log(response.data)

    const mappedCars = response.data.map(dataObj=> new Car(dataObj))
    appstate.cars = mappedCars
 }

 7. straight to appstate

/**@type {import('./models/Car.js').Car[]} */
 cars = []

 make sure to put this in the service so it can be saved 

 8. go to carsController 
 function _drawCars


 this is going to happen in the service 
 createCar(formData){
    const res = await _sandboxApi.post('api/cars', formData)
    console.log(res.data)
 }


in env.js 

export const domain = 'put the one with domain here '


<!-- SECTION 8/30 -->
1. started off by creating a service file
 const dndapi = axios.create({
    baseURL:
    timeout: 5000
 })

 class DndSpellsService{
    async getSpells(){
        const res = await dndapi.get('spells')
        <!-- NOTE make sure you console log this bad boy -->
        console.log('GOT SPELLS', res.data)
    }
 }

 2. from there he made a controller 
 in the controller 
  
export class DndSpellsController{
    constructor(){

    }

    async getSpells(){
        try{
            await
        }
    }



}


3. created a model
in model 

export class Dnd{
    constructor(data){
        this.name = data.name
        this.description = data.description || data.desc.join('\n\n')       // \n means new line
        this.damage = data.damage ? data.damage.damage_type ? data.damage.damage_type.name : data.damage : 'n/a '
        etc
    }

}

4. went to appstate to create spell list 

5. in the service 

appstate.spellList = res.data.results


6. in controller 
made a _drawSpellList()

7. in the spell.js

static SpellListTemplate(spell){
    return `
        this is now where our template will go now   
    `
}

from here put in += Spell.SpellListTemplate(s) in the controller that draws the function


8. In the controller made a function
async getOneSpell(
)

9. go to the service and make that same one
async getOneSpell(index) //do not forget the index {
    const res = await dndapi.get(`spells/${index}) //this is coming from the api page, look at the url!
}

10. in the appstate 

/**@type{spell} */
activeSpell = null

11. go to the service and in the getOneSpell
 appstate.activeSpell


 12. go to the controller and make a function 
 _drawActiveSpell(){
    let activeSpell = appstate.activeSpell
    let activeContent = ''
    setHTML('active-spell', activeSpell.activeTemplate)
    
 }

 13. make a getter in the spell.js and DO NOT forget to adjust the router

 in static spellListTemplate
 add 
 get 
 
 activeTemplate

 14. create a new controller and new service for just the sandbox
 in the controller

 async saveSpell(){}

 15. in the sand service 
 saveSpell()



 <!-- SECTION 8/31-->

querys start with a question mark, then it goes into the parameter. then the last part will be the value        

const nasaApi = axios.create({
    baseURL: https://api.nasa.gov/plantetary/apod
})

this is one way to do it
await nasaApi.get('?api_key=blah')       //api key goes in the quotes

Another way to do it, this would be helpful for more parameters
params:{
    'api_key':''    //take the key and value and puts it together
}