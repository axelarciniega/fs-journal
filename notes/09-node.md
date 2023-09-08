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

 can comment out in the start up line between 22 and 26 then run the server to make sure it is successful

DO NOT forget about your dbContext, will help with mongoose  

 1. start of with making exhibit.js
 making the schema

 2. made her exhibit controller and service 

 3. in the controller set up the constructor with the super
 constructor(){
    super('api/exhibits')
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

    21. in the exhibit controller we are creating a put('/:exhibitId', this.editExhibit)

    22. in the exhibit service we are throwing a null check
    if(!originalExhibit) throw new Error('unable to find exhibit at ${exhibitId}')



    <!-- SECTION 9/7 -->

    bcw create= use the express-mvc

    click 'open workspace' to get both projects

    Put your domain, audience and Id in the Env, and DO not forget the connection string
    ALSO in your client env we need these domain etc

    After starting our server and logging in, we should have the token, user info and account


    1. started off by deleting value which is just there as an example in the server

this is all in the server side
    2.then created a bird model = schema
    -after the curly bracket
    {timestamps: true, toJSON:{virtuals:true}}


    3. then started to create a controller and service
    did a createBird 
    DO NOT forget about await newBird.populate('reporter')  //reporter is coming from the model!

<!-- ANCHOR in the preview copy the access token then go to post man, authorization, bearer token, and then paste the token -->


    4. created this in the birder controller
    .use((request, response, next) => {
        logger.log('middle ware')
        request
        next()
    })

        .use(Auth0Provider.getAuthorizedUserInfo)


    5. in the createBird()
    body.reporterId = req.userInfo.id 

    6. now we are creating a getBird() in the bird controller
    If you move the get(''this.getBird) above the use(auth0) you can get the request without logging in.


    7. created get('/bitdId', this.getBirdByid) in the bird controller



/
    8. start creating birdWatcher controller, service and model

    9. in the birdwatcher model 
    new Schema ({
        accountId: {type: Schema.Types.ObjectId, required true, ref: 'Account'},
    })

/
    10. in the BirdWatcher controller we created a post
    before our POST we do our .use(Ath0)
    and we are doing a createBirdWatcher

    11. in our birdwatcher service DO NOT forget to - await populate both!
    await watcher.populate('profile', '-email')  OR
    await watcher.populate('bird profile', 'name picture')


/
    12. now in the 'bird controller' we are creating a get
    .get('/birdId/birdWatchers', getBirdwatchers)


    13. in the birdWatcher controller we are creating a delete 
    .delete('/:birdWatcherId', this.removeBirdWatcher)


    <!-- TODO run 'npm i' after cloning a project down -->

<!-- ANCHOR -->
NOW starting the client side/front end
14. started of by creating a birdsController, birds service and model
started writing a getBirds function

15. after making sure we got some birds on the log we can start building our model

16. going to appstate now to store some birds with an empty array 

17.


