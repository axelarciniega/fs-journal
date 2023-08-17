# Intro to JavaScript
01. Which keywords are used to declare a variable in JavaScript?

    > The keywords that are used to declare a variable in java are var, let, and const.

02. What is the definition of a function?

    > A function is a subprogram designed to perform a particular task.

03. What are the `SOLID` principles?

    > The solid principles are single responsibility, open/closed, liskov substitution, interface segregation, and dependency inversion.

04. Given this array: How could you remove the `pineapple`?

    ```js
    let fruit = ['apple', 'banana', 'pineapple', 'orange', 'strawberry']
    ```

    > To remove pineapple, you can use the splice() method in this case.

05. Given these two objects: How could you add each to the others friends arrays?

    ```js
    let you = {
        name: "You",
        hair: true,
        friends: []
    }
    let them = {
        name: "Them",
        hair: false,
        friends: []
    }
    ```

    > To add each to these arrays, you can use the push method.

06. Give an example of a JavaScript `Conditional`:

    > let time = 11;

    if(time >= 12){
        console.log("Good morning")
    }

07. What is the main difference between `parameters` and `arguments`?

    > The difference between parameters and arguments is that parameters are used when defining a function. Arguments are the values the function receives from each parameter when the function is executed.

08. Instead of writing everything to the console, what is a better way to debug your code?

    > A more helpful way to debug our code is using Break Points.

09. What is the difference between a `primitive` value and a `reference` value?

    > The difference between primitive and reference values are that primitive values are stored in memory locations when you assign it to a variable. Reference values are stored in the location where the data is stored.

10. Demonstrate a loop that prints the numbers between -100 and 100?

    > for(let i = -100; i <= 100; i++){
        console.log(i)
    }
