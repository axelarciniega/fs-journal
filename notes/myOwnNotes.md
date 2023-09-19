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










