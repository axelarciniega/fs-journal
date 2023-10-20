# A bit more CSharp and SQL
1. What does ***inheritance*** accomplish for us in C#?

  What inheritance accomplishes for us in c# is code reusability, method overriding, extensibility, abstraction and polymorphism.

2. How does ***member inheritance*** work in C#? Does a `Class` inherit all members of the base `Class`?

  In c# member inheritance allows a derived class to inherit the members like fields, properties, methods and events of its base class. A class does inherit all members unless they have a private access modifier.

3. How does ***accessibility*** affect inheritance?
Accessability affects inheritance because it determines whether a member of a base class is visible and accessible in derived classes. The accessibility modifiers in C# include public, protected, internal, protected internal, and private

4. What is the difference between a `PRIMARY KEY` and a `FOREIGN KEY`

  The difference between a primary key and foreign key is that the, primary key is a constraint that is used to identify each record or row in a database table, while in the other hand, foreign key establishes a link or relationship between two tables.

5. What is an ***alias***?

  An alias is a term to represent a different or shorter name for a longer or more complex entity.

6. Demonstrate how you would query a join statement that would get all of a doctors patients from the following collections:

  ```SQL
  CREATE TABLE doctors (
    id INT NOT NULL AUTO_INCREMENT,
    -- CODE OMITTED
    PRIMARY KEY (id)
  )

  CREATE TABLE patients (
    id INT NOT NULL AUTO_INCREMENT,
    -- CODE OMITTED
    PRIMARY KEY (id)
  )

  CREATE TABLE patient_doctors (
    id INT NOT NULL AUTO_INCREMENT,
    doctorId INT NOT NULL,
    patientId INT NOT NULL,

    FOREIGN KEY (doctorId)
      REFERENCES doctors(id),
    FOREIGN KEY (patientId)
      REFERENCES patients(id),
  )

  ```

 SELECT 
 *
FROM patients
JOIN doctors
