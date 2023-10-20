# CSharp

dotnet new console -0 csharpDemo

var x = 10; //NOTE is an integer 

int y = 10; //NOTE Best practice and int can only be whole numbers

float z = 4.5f; 

double a = 5.55;

decimal b = 6.80912m; //NOTE m stands for money 



string greeting = "hello"; //NOTE use only double quotes
string h = "h";
char g = 'g';



bool ok = true;
bool no = false;



Array<int> = new Array<int>[3]{1,2,3}

List<string> cars = new List<string>(){"Iron Man", "George"};
cats.Add("Gopher");
cats.Add("Bean");
Console.WriteLine(cats.Count);
string catsToRemove = cats.find(c => c == "Bean")
cats.Remove(catsToRemove);


Dictionary<string, int> codeWorksCats = new Dictionary<string, int>();
codeWorksCats.Add("Sam", 7);

Dictionary<List <string>, string> actualCats = new Dictionary<List <string>, string>();
actualCats.Add(cats, "jeremy's babies")
actualCats.Remove(cats)




class Cat{
    string Name;

    string Color;

    int Age;

    public Cat( string name, int age, string color)
    {
        Age = age;
        Name = name;
        Color = color;
    }
}

List<Cat> catsTheMovie = new List<Cat>();


//STUB 
bcw create
dotnet-auth

comment out 32 in the startup.cs???
added this to the startup, the order does the matter 

services.AddScoped<CatsRepository>();  
services.AddScoped<CatsService>();



1. created a model called Cat.cs

namespace catRoundUp;

public class Cat {
    public int Id {get; set;}
    public string Name {get; set;} //NOTE this means that ths could be used by anybody 
    public string Color {get; set;}
    public int Age {get; set;}
    public bool Feisty {get; private set;} //NOTE this works like a read only

    public Cat(int id, string name, string color, int age, bool feisty){
        Id = id;
        Name = name;
        Color = color;
        Age = age;
        Feisty = feisty;
    }

}

https://localhost:7045

//NOTE to get the return in controller
https://localhost:7045/api/cats/test

add config server dotnet 5+




2. created a CatsController.cs



[ApiController]
[route("api/cats")]

private readonly CatsService catService;
public CatsController (CatsService cs){
    _catsService = cs;
}

public class CatsController : ControllerBase{
    //NOTE 
    [httpGet"test"]
    public string GetTest(){
       return "Hey it worked";
    }


    [HttpGet]
    public ActionResult<List<Cat>> GetCats(){ 
        try{
            List<Cat> cats = _catsService.getCats();
            return Ok(cats);
        }
        catch(Exception e){
            return BadRequest(e.message);
        }
    }


    [HttpGet("{catId}")]
    public ActionResult<Cat> GetOneCatById(int catId){
        try{
            Cat cat = _catsService.GetOneCatById(catId);
        }
        catch(){

        }
    }

}


3. creating a CatsService


    namespace catRoundUp.Service
    

    public class CatsService {
        private readonly CatsRepository _repo;

    public CatsService(CatsRepository repo){
        _repo = repo
    }

    internal List<Cat> GetCats(){
        List<Cat> cats = _repo.GetAllCats();
        return cats;
    }

    internal Cat GetOneCatById(int catId){
        Cat cat = _repo.GetOneCatById(catId)
        if(cat == null) throw new Exception($"NO CAT {catId}");
        return cat;
    }

    }

    4. creating a CatsRepository
    namespace catRoundUp.Repositories
    public class CatsRepository{
        private List<Cat> _FakeDb;

       public CatsRepository(){
        _FakeDb = new List<cat>();
        _FakeDb.Add(new Cat(1, "George, "Orange, 5, false));
       } 
       
    internal List<Cat>GetAllCats{
        return _FakeDb
    }

    }

    void is for when you have no return //NOTE 



<!-- STUB 10/10 -->

in the dbsetup.sql

//NOTE when you change something  in the table drop it and execute it again 
CREATE TABLE hotdogs(

    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(500),
    imgUrl VARCHAR(500),
    bun VARCHAR(500), 
    dig VARCHAR(500),
    hasKetchup BOOLEAN, 
    hasMustard BOOLEAN,
    description VARCHAR(1000),
    expirationDate DATETIME DEFAULT CURRENT_TIMESTAMP,
    price DOUBLE, 
);


INSERT INTO hotdogs
(name, imgUrl, bun, dog, hasKetchup, hasMustard, description, price)
VALUES
('Huge Dog', 'https://unsplash', 'Huge Toasted Whole Wheat', 'Kosher Veggie', true, false, 'Hugeee', 45); 
('Danger Dog', 'https://unsplash', 'Extra spicey jalapeno', 'Extra spicey chorizo', false, false, 'This one is danger', 55); 

SELECT * FROM hotdogs; //NOTE star is asking for all the data or columns that exist
SELECT name, price FROM hotdogs FROM hotdogs WHERE `hasKetchup` = true;  AND price < 50
SELECT name WHERE description LIKE = '%chorizo%' //NOTE anything can come before after with the percent
SELECT name FROM hotdogs ORDER BY price
SELECT * FROM hotdogs WHERE id = 1 

SELECT 
name,
price
FROM hotdogs
Where price < 30
ORDER BY price 

<!-- MySQL TUTORIAL to help with errors -->

DELETE FROM hotdogs; //NOTE deletes all of them 
DELETE FROM hotdogs WHERE id = 3
DELETE FROM hotdogs ORDER BY price DESC LIMIT 1;

UPDATE hotdogs
SET price = 20 
WHERE id = 1;

UPDATE hotdogs
SET price = price /2
WHERE price > 5;

<!-- STUB start of gregList -->

CREATE TABLE cars(
    id INT AUTO_INCREMENT PRIMARY KEY,
    make ENUM('toya', 'bww', 'goblin-car') NOT NULL COMMENT "these are cool",
    model VARCHAR(255) NOT NULL,
    imgUrl VARCHAR(500) DEFAULT 'https://unsplash',
    price INT NOT NULL,
    year INT NOT NULL,
    description VARCHAR(1000),
    isNew BOOLEAN DEFAULT false
)default charset utf8mb4 COMMENT '';

INSERT INTO cars
(make, model, year, price, isNew)
VALUES
('toya', 'yoda', 1998, 4000, false);
INSERT INTO cars
(make, model, year, price, isNew)
VALUES
('sub', 'wrx', 2011, 2000, true);

SELECT * FROM cars; 


fill out the appsettings.Development.JSON
server=SG-CodeWorks-7891-mysql-master.servers.mongodirector.com;database=codeworking;port=3306;user id=sgroot;password=Ee24jLbm1XDfkW-f;

creating car model 
namespace server.Models
public class Car
{
    prop int Id {get; set;}
    public string Make
    public string Model
    public int? year 
    public int price  
}

creating a new car controller right click it
[ApiController]
[Route("api/[controller]")]

public class CarsController : ControllerBase
{
private readonly CarsService carsService;

public CarsController(CarsService carsService)

    [HttpGet]
    public ActionResult


}


creating a car service right into class

public class CarsService{
    private readonly CarsRepository _repo







}


DO NOT to add the scopes in the startup.cs

creating a car repository 

public class CarsRepository
{
    private readonly IDbConnection _db;

    Public CarsRepository(IDbConnection db){
        _db = db;
    }

internal List<Cat> GetAllCars()
{
    string sql = "SELECT * FROM cars;";
    List<Car> cars = _db.Query<Car>(sql).ToList();
    return cars; 
}
}


<!-- STUB 10/11 -->
in the appsettings.Development.json
DO NOT forget to fill out and in the client side 
the auth will be same from mongo
baseurl: https://localhost:7045

1. going into the dbsetup.sql

CREATE TABLE IF NOT EXISTS albums(
    id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
    category VARCHAR(100) NOT NULL,
    title VARCHAR(225) NOT NULL,
    ccoverImg VARCHAR(500) NOT NULL,
    archived TINYINT DEFAULT 0,
    creatorId VARCHAR (255) NOT NULL,
    FOREIGN KEY (creatorId) REFERENCES accounts(id) ON DELETE CASCADE
)

INSET INTO albums(category, title, coverImg, creatorId)
VALUES
('sport','Ping Pong Tournament','https://images.unsplash', '(creatorId here)')



SELECT * from albums JOIN accounts;

SELECT * FROM albums alb JOIN accounts act ON act.id = alb.creatorId 



//NOTE if you see NEAR in error typically look at the line before


2. created a album model

type in prop and it will start a template 

3. created a album repository first

4. created a album service 

5. created a album controller 

//NOTE after you created these you should fill in your startup

6. in the controller

[HttpGet]
public ActionResult<List<Album>> Get()
{}

7. now in the service
internal List<Album> get()
{}

8. now in the repository
internal List<Album> get()
{
    string sql = @"
    
    ;";
    //NOTE @ lets you use multiple lines
}

9. fixing the model so it can bring the account information =
public Account Creator (get; set;)

10. back to the repository 
adding to the Get


11. back to the controller 
[HttpPost]


12. now in the service
internal Album Create(Album albumData)
{}

13. now in the repository 
internal Album Create(Album albumData)
{}


14. back to the controller
private readonly Auth0Provider _auth0;
ctrl . and click add parameters to add to constructor

Add in task before action result and async before the task 

Account userinfo = await_auth0.GetUserInfoAsync<Account>(HttpContext);
albumData.CreatorId = userInfo.Id;

15. back to the repository 
updating the Create

16. Now in the controller 
above the HttPost 
[Authorize]

next
[HttpGet("{ablumId}")]

17. now in the 22service
bringing it in

18. in the repository now 
bringing in the get by id

19. back in the controller 
[Authorize]
[HttpDelete("{albumId}")]

20. Now going into the service to add the delete

21. now in the repository 
_repo.Edit(album;)  //NOTE this makes sure that the database is also changes


<!-- STUB 10/12 -->
started in the dbsetup.sql
1. creating a new table 
CREATE TABLE pictures()
added 
ONE DELETE CASCADE //NOTE this allow you to delete without errors

created a 
INSERT INTO pictures(imgUrl, creatorId, albumId)
VALUES("https://", "actual creatorId", "actual albumId")

2. creating a picture model 

3. creating all the files that we are going to need, pictures repository, picture service, and picture controller 

4. in the controller we are creating a post request
[Authorize]
[HttpPost]

5. pushed it in the service and the repository 

6. now in the ALBUM controller 
//NOTE by looking at the end point on postman you can see where we need to insert it 
[HttpGet("{albumId}/pictures")]

bring the picture service so we can call it in the picture service 

7. now in the picture service we are bringing it in

8. Now in the picture repository we bring it in 

9. back to the dbsetup.sql
CREATE TABLE IF NOT EXISTS collaborators()

creating a
INSERT INTO collaborators()

10. creating a collaborator model 

11. creating files that we need, collaborators repository, collaborators service and collaborators controller

12. now in the collaborator controller we are creating a post

[Authorize]
[HttpPost]

13. bringing it in the collaborators service

14. bringing it in the repository


15. Going into the account model !

public class AccountCollaboratorViewModel : Account
{
    public int CollaboratorId {get; set;}
}

16. Going into our albums controller 
[HttpGet("{albumId}/collaborators")]
public ActionResult<list<AccountCollaboratorViewModel>> GetCollabsByAccount()
{}

//NOTE add in your collab service

17. now entering the collab service


18. now entering the collab repository


19. in the collaborator model 
public class AlbumCollaboratorViewModel : Album
{
    public in CollaboratorId {get; set;}
    public string AccountId {get; set;}
}

20. Now going into the account controller 
[Authorize]
[HttpGet("collaborators")]

//NOTE make sure to add in your collab service

21. heading over to the collaborators service to bring it in

22. now going into the collaborator repository 


23. in the collaborator controller 
[Authorize]
[HttpDelete("{collabId}")]

24. bring it in the collaborator service 

25. bring it in the collaborator repository 


<!-- STUB 10/16 -->


<script setup>
    //NOTE bringing in setup allows you to take the setup and return out in vue.
</script>

good reference for a modal is vueflix 



