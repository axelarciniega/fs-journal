# CSharp and SQL Fundamentals
01. What is the purpose of a `namespace`?

  The purpose of a namespace is to prevent any naming conflicts and it also improves code maintainability.

02. What is the difference between a `class` and an `interface`?

  The difference between a class and an interface is that the class is a blueprint for creating objects which defines the structure while in the other hand, interface is a contract that defines a set of methods and properties that a class implementing the interface must provide.

03. What is the method that returns an instance of a class, yet it has no return type?

  The method that returns an instance of a class but yet has no return type is the constructor.

05. In the Car example what is the access modifier of the `Start()` method?

  ```c#
  abstract class Car
  {
    public string Start()
    {

      return "Vroooom";

    }
  }
  ```

  In this example, the access modifier of the start() method is the public access modifier.

06. In the Car example what is `string` an indication of?

  In the example the string is the indication of the start method 

07. In the Car example what is `abstract` preventing?

  In this example abstract is preventing it so you can not create objects of the car class

08. In a SQL table, what is the difference between information in a row and information in a column?

  The difference between information in a row and a column is that the row contains a specific set of values, one for each column, while in the other hand the column contains values of the same data type.

09. Demonstrate the necessary SQL for creating a table called `characters` with the values `name, age, description` as strings, and an `int` id.

  CREATE TABLE characters(
    id INT AUTO_INCREMENT PRIMARY KEY.
    name VARCHAR(255),
    age int,
    description VARCHAR(255),
  )

10. In SQL how can you query more than a single table? Provide an example.

  SELECT make
  FROM cars
  JOIN trucks
