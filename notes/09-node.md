# Node

<!-- SECTION 9/5 -->
bcw create node server auth0, express server

localhost:3000 /api/cats ?

1. created a controller called cats

2. in the controller 
export class CatsController extends BaseController{
     constructor(){
        super('api/cats')
        this.router
        .get('', this.getCats)

    <!-- NOTE Request, is an object representing the incoming request from user -->
    <!-- NOTE Response, is an object for you to manipulate and use to send responses the requestor -->
    <!-- NOTE Next, is how we kick people back into the server -->
        getCats(request, response, next){
            console.log('they getting cats')
            logger.log('request')   //logger log elevates the console to layer that reaches you debug console
            response.send('you got cats')
        }
     }
}

//make sure to click the little refresh button


3. created a cat service
in service, you would still export it the same as mvc
<!-- NOTE this is a fake data base as an example -->
 const fakeDb = {
    cats : [
        {name: 'Scout', age: 305}
    ]
 }


put this in the .env
reaplace the password with the actual user password with this = nm8vdZ6bDh3ptHX6

 mongodb+srv://axelarciniega12:<password>@cluster0.ydbahtm.mongodb.net/?retryWrites=true&w=majority

 1. created a car controller and service 

 2.in the controller 
 export class CarsController extends BaseController{
    constructor(){
        super('api/cars')
        this.router
        .post('',this.createCar)





        async createCar(request, response, next)
        try{
            logger.log

            request.send('')
        }
        catch{}
    }
 }

3. created a car model 
in the model 
export const carSchema = new Schema(
    {
        make: {type: String, required: true, minLength: 3, maxLength: 15},
        year: Number,
        price: {type: Number, required: true, min: 1, max: 100000,}
    }
)



4. in Dbcontext
car= mongoose.model('car', carSchema)




5 in car controller 
await cars.service 


in the car service
create(carData){
    const car = await dbcontext.Cars.create(carData)
    return car  
}


6. in the car controller start making getCar

7. in the service 
getCars(){
                                        find returns documents and FINDS all
    const cars = await dbContext.Cars.find()
    return cars 
}

8. in the car controller again created a delete

9. in the service 
removeCar(carId){
    await dbContext.Cars.findByIdAndRemove(carId) //not the best solution but works 

    const carToRemove = await dbContext.Cars.findById(carId)
    if(!carToRemove){
        throw new BadRequest('No car at: '+ carId)
        await carToRemove.remove()
        return `removed the ${carToRemove}. She a goner` 
    }
}







 use helpful tool https://www.postman.com

