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

