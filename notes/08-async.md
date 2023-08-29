# Async


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