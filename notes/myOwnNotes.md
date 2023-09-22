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

















