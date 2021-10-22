# Block of Code
### This is what I did for my midterm in IT 2040 (hopefully I can post it here lol)
Person.cs
``` cs
using System;

namespace MidtermProject
{
    public class Person
        {//standard stuff here nothing too special
            private string firstName;
            private string lastName;
            private string id;
            public Category Category;

            
    //constructor
            public Person(string firstName, string lastName, string id, Category Category)
            {
                this.firstName = firstName;
                this.lastName = lastName;
                this.id = id;
                this.Category = Category;

            }
            public string getFirstName(){//Method for returning the person's first name
                return firstName;
            }
            public string getLastName(){//Method for returning the person's last name
                return lastName;
            }
            public string getId(){//Method for returning the person's id
                return id;
            }
            public Category getCategory(){//Method for returning what category they are in
                return Category;
            }
            public void setFirstName(string new_first_name){//method for returning the new first
                this.firstName = new_first_name;
            }
            public void setLastName(string new_last_name){//Method for returning the new last name
                this.lastName = new_last_name;
            }
            public void getPersonInfo()//This method prints the person's info
            {
                Console.WriteLine($"Name: {getFirstName()} {getLastName()}\nID: {getId()}; Type: {getCategory()}");
            }
        }
}
```

Category.cs
``` cs
using System;
namespace MidtermProject
{
    public enum Category//This is where the enum for Category is
    {
        student, faculty, staff
    }
}
```
Student.cs
``` cs
using System;
namespace MidtermProject
{
    public enum StudentClass{
        freshmen, sophmore, junior, senior
    }
     class Student: Person
        {
            public string major;//had to add these two lines or else it would just keep failing to compile
            public int creditHours;
//constructor
            public Student(string firstName, string lastName, string id, string major, int creditHours) : base(firstName, lastName, id, Category.student)
{//This allows this subclass to access the methods in the Person class
                this.major = major;
                this.creditHours = creditHours;
}
            public int getCreditHours()//Return the credit hours
            {
                return this.creditHours;
            }
            public StudentClass getStudentClass() //returns the enum of what class the student is in
            {
                if(creditHours <= 29){
                    return StudentClass.freshmen;
                }else if(creditHours <= 59){
                    return StudentClass.sophmore;
                }else if (creditHours <= 89){
                    return StudentClass.junior;
                }else {
                    return StudentClass.senior;
                }
            }
            public void updateCreditHours(int hours) //updates the credit hours
            {
                this.creditHours += hours;
            }
            
        }
}
```
Professor.cs
``` cs
using System;
namespace MidtermProject
{
     class Professor: Person
        {
            public string department;//Like with student.cs I had to add this or else it would crash
            public string researchArea;
            public Professor(string firstName, string lastName, string id, string department, string researchArea) : base(firstName, lastName, id, Category.faculty)
{//This allows this subclass to access the methods in the Person class
                this.department = department;
                this.researchArea = researchArea;
}

            public string getDepartment() //returns the department the prof is in
            {
                return this.department;
            }
            public void setDepartment(string new_department) //sets the new department the prof is in
            {
                this.department = new_department;
            }
            public string getResearchArea()//returns the research area prof is in
            {
                return this.researchArea;
    
            }
            public void setResearchArea(string new_research_area)//sets new research area of prof
            {
                this.researchArea = new_research_area;
            }
         }
 }
 ```
 Program.cs
``` cs 
using System;
namespace MidtermProject
{//This whole area is just what I tested my code with
    class Program
    {
        static void Main(string[] args)
        {
            Person person1 = new Person("Truman", "Tiger", "12345", Category.student);
            Student student1 = new Student("Mickey", "Mouse", "23456", "Information Technology", 87);
            Professor prof1 = new Professor("Elmer", "Fudd", "56789", "Computer Science", "NLP");

            Console.WriteLine("\n-------Person 1-------------");
            person1.getPersonInfo();


            Console.WriteLine("\n-------Student 1-------------");
            student1.getPersonInfo();
            Console.WriteLine($"Class: {student1.getStudentClass()} | Credit Hours: {student1.getCreditHours()}");
            student1.updateCreditHours(15);
            Console.WriteLine($"Updated Class: {student1.getStudentClass()} | Updated Credit Hours: {student1.getCreditHours()}");

            Console.WriteLine("\n-------Professor 1-------------");
            prof1.getPersonInfo();
            Console.WriteLine($"Dept: {prof1.getDepartment()} | Research Area: {prof1.getResearchArea()}");
            prof1.setFirstName("Wiley");
            prof1.setLastName("Coyote");
            prof1.setResearchArea("Autonomous Systems");
            prof1.setDepartment("Information Technology");
            Console.WriteLine($"\nNew Name: {prof1.getFirstName()} {prof1.getLastName()}");
            Console.WriteLine($"New Dept: {prof1.getDepartment()} | New Research Area: {prof1.getResearchArea()}");

        }
    }
}
```
| **Page**  | **Description** |
| ------ | ----------- |
| [0.](https://github.com/aaronmcgough/Midterm-Project#readme)     | Home |
| [1.](https://github.com/aaronmcgough/Midterm-Project/blob/main/Death%20and%20DDT%20Document)     | Death and DDT Document. |
| [2.](https://github.com/aaronmcgough/Midterm-Project/blob/main/Death%20and%20DDT%20References)     | Death and DDT References. |
| [3.](https://github.com/aaronmcgough/Midterm-Project/blob/main/The%20Peregrine)     | The Peregrine. |
| [5.](https://github.com/aaronmcgough/Midterm-Project/blob/main/Peregrines)     | Peregrines. |
