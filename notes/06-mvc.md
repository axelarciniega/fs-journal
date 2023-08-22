# MVC
<!-- SECTION 8/21 -->

bcw create 

started by creating a file in the models called character.js

class Character{
    name

    role

    health

    maxHealth

    constructor(newName, newRole, newHealth){
        console.log('Building a character')

    <!-- NOTE THIS IS A CONTEXT FOR A CLASS INSTANCE TO LOOK ITSELF -->
        this.name = newName 
        this.role = newRole
        this.health = newHealth
    }

    greeting(){
    console.log('Hello, My name is', this.name)
    }

}