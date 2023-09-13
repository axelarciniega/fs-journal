# Vue


<!-- SECTION 9/11 -->

bcw create vue starter 

user: computed(() => AppState.user)
// Think of Computed as AppState.on and also as a GET

vt and then hit tab will open you a template 


<h1> Health: <span>{{health}}</span></h1>


in the AppState.js

account: {},
health: 100


in the appstate the objects are always plural but in for example the FoodItem the object will be singular



<!-- SECTION 9/12 -->

1. first created a model called movie.js
export class Movie{
    constructor(data){

    }
}


2. then created service called MovieService
 class MovieService{

 }

 export const movieService = new MovieService()


 3. on the home page below the setup
 <!-- NOTE Vue LifeCycle Hooks -->
onMounted() // when component is mounted to the dom
onUpdated() // When component data is updated
onUnmounted() // When component is 'unmounted' from the dom (removed)
 
In the setup(){}
onMounted(getMovies)

async function getMovies(){
    await 

}

return{
    getMovies
}

4. in the axios
export const movieApi = axios.create({
    baseUrl: 'url here',
    api_key: ''
})


5. in the movie service
 const res = await movieApi.get('discover/movie') //this will get the popular movies
 AppState.movies = res.data.results.map( moive => new Movie(movie))

 6. in the appstate
  movies : []

  7. in the homePage
  movies : computed(() => AppState.movies)

  8. Still in the homepage but in the template
  <div v-for="movie in movies" :key="movie.id">
  {{movie.title}}
  img class="" :src="movie.poster"
  </div>


  9. created a component called movieCard
    move in your information from the homepage so we can abstract
    in the script
    export default{
        props:{movie: {required: true} }, // this sets up the component to TAKE in data from a parent component
        setup(){
            return {}
        }
    }

    10. in the home page

    <div v-for="m in movies" key="m.id">
    <MovieCard :movie="m"/>
    </div>

    11. still in the home page
    created buttons which could change into different movies 

    in in the return
    async changePapge(number){
        await moviesService.changePage(number)
        
    }

12. in the movie service
async changePage(number){
    const res = await movieApi.get('discover/movie?page=${number}')
    AppState.movies = res.data.results.map()
    AppState.

}

13. in the appstate
pageNumber: 1

in the home page
pageNumber: computed()

14. in the Home page you can add a disabled so the user cant go to 0
:disabled="pageNumber <=1" 

15. created a movieModal.vue in the components


16. in the movie service
created an async getMovieById()

17. in the movie card we created a getMovieDetails

18. in the movie card
on the @click we add the data-bs for the module

19. created a component called searchBar
@submit.prevent="searchMovies"  //works exactly the same as window.event.preventDefault()

input v-model=""

in the setup 
const searchTerm = ref('')  //do not forget to return searchTerm

20. in the service
async searchMovies(){}


<!-- SECTION 9/13 -->

first he started filling out the env file

1. in the router created a path for cars


2. Then created a router-link in the home page
router-link :to="{name: 'Cars'}"

3. created a carPage 

4. created a button with a @click goToCarsPage 
    In the setup and return that is where the function for is going

5. Created a car model car.js

6. from there create a car service





7. In cars page 
setup(){
    onMounted(() => {
        getCars()
    })


    async function getCars(){
    }

    return{

    }
}

8. in the AppState
cars : []

9. Now in the cars page
return{
    cars: computed(() => AppState.cars)     //NOTE This is bringing the cars from the AppState
}

10. In car page but in the template
created a div with a v-for 

11. created a carCard.vue
all we did was grab the important data and imported it here to see if we can duplicate the cars on the page

//TODO DO NOT forget to bring the carCard component in the car page

export default{
    props: {car {type: Car, required: true} }
    setup(){

    }
}

12. In the car page 
<carCard :car="car"/> //NOTE : that is what data binds the components 

13. if the carCard works properly, we can now start making it look good 

14. created a router link in the CarCard 
Put the whole router link so if you click the car it takes you to a car detail page

15. created a carDetail page
//NOTE DO NOT forget about the router and making a path
in the router
path: '/cars/:carId',
name: ''

16. in the carCard
router-link :to{name: Car Details, params: {carId: car.id} }

17. in the carDetailsPage
export default{
    setup(){
        const route = useRoute()    //NOTE route is where you are in context of the app your url
        onMounted(() => {
            getCarById()

        })
    }

    async function getCarById(){
        const carId = route.params.carId
    }

    return{}
}

18. now go to the carService and bring the function getCarById(){}

19. In the AppState 
created a activeCar

20. Go back to the car Details page
in the return
we are calling the active car
//TODO DO not forget about bring the car to the template using these bad bois
{{activeCar}}  Just so we can see that it is working then we can start making it look pretty

on the section we added v-if so it can load if there is an active car

21. in the carsPage above our sections
we are going to put our form which is going to have our button so we can create a car

22. created a car form
in this form created a function createCar(){}
in the setup() = const make = ref('') //NOTE this only works for single inputs
make sure to have the v-model in the inputs Ex. carData.make
in the setup() = const carData = ref({ }) //TODO make sure to have it in the return

23. now in the car Service we are making a createCar
pop.toast('hello', 'success') this will pop up a message 



24. created a const router in the CarForm
in the create car we did a router.push //NOTE so once you create it, will auto take you to the detail page of car
router.push({name: 'Car details', params: {carId: newCar.Id} })


25. now focusing on deleting the cars
