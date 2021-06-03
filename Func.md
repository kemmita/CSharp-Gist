1. We want to create a function, a funciton in the Person class that will let us know if that person can apply for the school they wish to go to. Instead of writing a bunch of if statements for different GPA levels we will pass a Func that will allow the developer to define the GPA level the person needs to exceed.
```cs
  public class Person
    {
        public double GPA { get; set; }
        
        // The developer will be able to fluently define what gpa is needed to apply
        public bool CanApply(Func<double, bool> CheckGPA)
        {
            return CheckGPA(GPA);
        }
    }
```
2. Consumer class
```cs
  static void Main(string[] args)
        {
            var harvardList = new List<Person>{new Person{GPA = 3.5}, new Person{GPA = 3.9}, new Person{GPA = 2.9}};
            var UOMList = new List<Person>{new Person{GPA = 3.3}, new Person{GPA = 4.0}, new Person{GPA = 2.6}};

            harvardList.Select(x => x.CanApply(x => x > 3.8));
            UOMList.Select(x => x.CanApply(x => x > 3.2));
        }
```
