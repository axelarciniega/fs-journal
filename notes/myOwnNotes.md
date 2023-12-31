<!-- SECTION 9/18 -->

template we are using is express-vue

1. getting the env file filled out

In the server side
2. created a model called album.

export const AlbumsSchema = new Schema({
    title: {type: String, required: true, maxLength: 100},
    category: {type: String, enum: ['animals', 'pugs'] required: true, lowercase: true}  //NOTE this will lower case it when you use it
    creatorId: {type: schema.types.ObjectId, ref: 'Account', required: true}
},{timestamps: true, toJSON{virtuals: true} }) //NOTE options for this particular schema

AlbumsSchema.virtual('creator', {
    localField: 'creatorId',
    foreignField: '_id'
})


3. created a albums controller and service
in the album controller 
writing all the information we need 
.use(Auth0Provider.getAuthorizedUserInfo)

made a createAlbum in the controller

4. in the album service and DO NOT forget about the dbcontext
creating the async createAlbum
await album.populate('creator')

//NOTE in the post man if you go to the main folder and go to the variables, and paste token into both auth's'

5. in the album controller, created a getAlbums and put it above the use AUTH
populate('creator') //NOTE put this so we can pass the tests

6. created a get in the album controller called getAlbumById

7. created a delete in album controller called archiveAlbum

still in the server 
8. created a model called picture


9. created a controller call pictureController
constructor(){
    super('api/pictures')
    this.router
    .use
    .post('', this.createPicture)
}

10. now in the albums controller we created a getPicturesinAlbum
.get('')

11. In the picture service we add await albumsService.getAlbumById(albumId)


MOVING to the client side for now

1. started in the homePage

create a model

2. created a getAlbums


3. in the home page we added the filter in the return albums:

then created
const filterBy = ('')
@click="filterBy = 'animals'""

//TODO make sure to return filterBy


<!-- SECTION 9/19 -->

1. Created a modal wrapper in the component section

2. created a <slot>s 

3. brought in the props
Props: {id: {type: String, required: true} showButton }

4. put the modalWrapper in the navBar
    Use template # to bring them in 

5. Created an albumForm component

6. bring in the Album form in into #body 

7. in the album form
created albumData and put the v-model inside the forms
adding id's will help with on making the form better


8. added a select inside in the coverimage 
<select v-model="albumData.category" id="">
<option value="animals"> animals</option>
</select>

9. created a function resetFrom in albumForm.vue

10. created a function in the return called createAlbum in albumForm
//TODO don't forget about the service

//NOTE 'upshift' will put it on the top unlike 'push' will put the info to the bottom

11. Added sort()
inside the albumService on the server side, inside the getAlbum

12. in the return
user: computed(() = AppState.)

13. now in the albumCard we are adding a routerLink
created an albumDetails page and also added a path inside the router 

14. in the albums detail page 
created an onMounted(()=> {

})
async function getAlbumById(){}
async funtion getpicturesByAlbumById(){}

//TODO update the appstate with activeAlbum and activeAlbumPictures


15. created a picture model 
//NOTE mapping is for array of things


16. in the album details page we computed albums and pictures in the return

17. Added the modalWrapper in the details page  

18. created a picture form 
created a pictureData = ref({})
make sure to add the form into the modal wrapper
made an async createPicture

19. created a picture service 

He committed for the client side 



no we will go onto the server side 

1. created a collaborator model 


2. we created a collaborator controller and service 


3. in the collaborator controller 
we add the .use
and created a .post('', this.createCollaborator)

do not forget the service on that bad boi

4. now in the albums controller we added a 
.get('', this.getCollaboratorOnAlbum)

5. now in the account controller we created a get
.get('/collaborators', this.getCollaborationsByAccount)

this one goes into the collaborator service 

6. now we go into the collaborator controller and create a delete
.delete('/collaboratorId', this.removeCollaborator)

this one goes into the collaborator service

7. now in the album.js we created a 
AlbumSchema.virtual('memberCount', {
    localField: '_id',
    foreignField: 'albumId',
    ref: 'Collaborator'
    count: true
})


9. now in the album service
we are going to bring in memberCount

10. in the collaborator service
in the getCollaborationByAccount
.populate({path: 'album', populate: {path: 'creator memberCount'} })

commited for the server side 



now we are going into the client side once again 

1. Adding the member count into the album card

2. now in the Home page we are creating async getMyCollaboratorsf
which is going into the accountService

3. now in the authService we are going to insert
accountService.getMyCollaborations 

4. In the AppState created 
myCollaborations

5. created a new collaborator model

6. in the home page 
in the return
add for the myCollaborations

7. in the album card
in the props we add 
|| object


8. in the album details page
created a getCollaborationByAlbumById
and this will go into the albumsService
in the appstate we created an activeAlbumCollaborators

9. in the collaborator model we fixed the this.album
this.album = data.album

10. back to the album detail page
created stub collab button 
in the return we create a createCollab
made a collaborationService

we also created a
let collabData = {albumId: route.params.albumId}


in the return we add 'isCollaborator: computed'
added a v-if with the @cick="createCollab"
and also created a v-else to remove collab 

11. created a removeCollab in the return 

add a disable so the user will not be able to click on it multiple times




<!-- STUB 10/4 -->

Post Man Test

created a new collection

created a variable called endpoint

then created a new folder called cars

from there created a post/ create car

make sure to login and get the token 

UNDER test-
const res = pm.response
const body = res.json


pm.test('Request was a good one', ()=> {
const goodOne = res.code == 200
pm.expect(goodOne).to.be.true('was not a good one')
})}


pm.test('Car was created as expected', () => {
    pm.expect(body.make).to.be.eql('toya', make of the car was so strong)
})

pm.expect(body.creatorId).to.not.be.undefined
pm.expect(body.creator).to.be.an.instanceOf(object, 'it was not an object')


going over getting car by id

const res = pm.response
const car = res.json()
const createCar = pm.variables.get('new Car')

pm.test('got the right car', ()=> {
    pm.expect(car.id).to.be.eql
    (carId here, 'you got the wrong car')
})


let carData = {
    make, model and all that would go in here
    "make": "chevy"
}

let config = {
    url:  `${pm.variables.get('endpoint')}/api/cars`
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
        Authorization: 'Bearer' + pm.variablels.get
        ('auth')
    },
    body: JSON.stringify({
        model: 'raw',
        ...carData

    })
}

pm.sendRequest(config, (error, response) => )
    const newCar = response.json()
    console.log('its a new car')

    pm.variables.set('newCar' , newCar)
    pm.variables.set('carId' , newCarId)


    <!-- STUB 10/5 -->
Vue tour

1. open up terminal and make sure we are cd in client 
npm install vue3-tour

go to main.js
import 'vue3Tour' from 'vue3-tour'
import 'vue3-tour/dist/vue3-tour.css'
.use(Vue3Tour)

2. In the home page in the template
making a 
<v-tour>

</v-tour>

in the return section
steps: [
    {
    target: '#v-step-0'
    header: {title: 'HEY HEY'},
    content: 'here is our super cool thing',
    actions: {next: '<button>Hey</button>'},
    params: {placement:  'top'}
    },
    {
        target: '#vue-step-1',
        header: title: 'view an album'

    }
]


tourCallBacks: {
    onFinish: (()=> {
        router.push({name: 'Album Details', params: {{albumId: AppState.albums[0].id }} })
    })
}

back to v-tour
<v-tour name='v-tour' :steps="steps" :callbacks="tourCallBacks">

</v-tour>

3. selecting a section within the template  we are going to add an add or a class
id="v-step-0"

5. inside the script tag
lowest point
mounted: function(){
    this.$tours['myTour'].start()
}

6. threw another id on another section
id="vue-step-1"

7. making a new component called tour.vue
in the new component 

<v-tour :setps="steps"  :callBacks="tourCallBacks">

</v-tour>

props: {
    steps: {type: Array, required: true},
    callBacks: {type: Object}
}

below return but still in the script tag
mounted:function(){
    this.$tours['myTour'].start
}


you can use this component on a different page 


now in the backend
8. in the acoount model
needsTour: {type: Boolean, default: true}

9. write down a .put('', this.updateAccount) in account controller 


going back to front end
10. account service in the front end 
async editAccount

11. make a tourCallBacks in the page with the component and make sure to call in our props

12. update the front end model
needTour

13. in the edit account make to sure update it to the Appstate

<tour v-if="account.needsTour"></tour>

make sure to update the first one we did

on the home page below the onFinish
onSkip: (async () => {
    await accountService.editAccount({needsTour: false})
})


14. in the account service
in the sanitizeBody
add
needsTour: body.needsTour
15. 





<!-- STUB 10/6 -->
SOCKETS

in the env file switch it true
after this check the console to see if it worked

new tab called ws which stands for web socket, green is messages we are sending and red is the messages that the server is sending

1. In the home page
we are adding a button
<button @click="testSocket"></button>

now in the return

testSocket(){
    socketService.emit('SOCKET_TEST') //NOTE chekc the service to see what goes in the quotes in the .on('')
}


2. in the service
this.socket.emit('IS_TESTED', 'anything here ', )

3. om socketService
.on(USER_LOGGED_IN,  this.onUserLogin)

onUserLogin(payload){
Pop.toast(payload.name + "logged in")
}
4. 
















