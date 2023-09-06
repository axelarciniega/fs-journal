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



 <!-- SECTION 9/6 -->
 in the env, you can put your data base in the connection string`

 can comment out in the utils/start up line between 22 and 26 then run the server to make sure it is successful

DO NOT forget about your dbContext, will help with mongoose  

 1. start of with making exhibit.js
 making the schema

 2. made her exhibit controller and service 

 3. in the controller set up the constructor with the super
 constructor(){
    supero('api/exhibits')
    this.router
        .post('', this.createExhibit)
 }

4. in the controller started by creating a async createExhibit

5. In the service start with a createExhibit

6. now pull up postMan with the local host, click new and then collection then name it same as project
then before you start, go to body, set raw and then json

7. after creating and sending them over from the post man 

8. start creating a get in the controller and the service 
.get('',this.getExhibits)


9. in the post man 
/api/exhibits?biome=tropical

10. in the controller 
getExhibits
made a const query then pass it to the service and insert it in the find()


11. now started making animals, created a model controller and service 

12.In the model we can start by starting to put information about our animals like their names and age etc
exhibitId: {type:Schema.type.ObjectId, ref:'Exhibit', required: true}       //ref is comimg from the dbContext

13. create an Animals in the dbContext for mongoose model

14. in the animal controller start by creating a post
constructor(){
    super('api/animals')
    this.router
        .post('', this.createAnimal)
}

in the postman the format for sending information 
{
    "name": "Oslo",
    "emoji": "",
    "age": 11
    }

    15. then start creating a get 
    you can also do request.query which should work as well

    16. from the value.js we are going to copy the timestamps and insert it in the Animal.js... then we place right after the last curly bracket--
    then we created
    AnimalSchema.virtual('exhibit',{
        LocalField: 'exhibitId', 
        ref: 'Exhibit'
        foreignField: '_id',
        justOne: true
    })


    17. in the animal service and in the getAnimals
    await animals.populate('exhibit')       // but this DID NOT work 

<!-- NOTE ................................................⬇️correct syntax but in this case we do not need it -->
    after the query you can do .populate('exhibit', 'biome emoji) //ignore the biome and emoji

    18. in the create animal
    we also add 
    awit newAniaml.populate('exhibit')

    19. in the exhibit controller we are creating a get('/:exhibitId/animals', this.getAnimalsByExhibitId)


    20. created getAninmalsByExhibitId()


