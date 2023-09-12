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
