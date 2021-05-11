1. With delegates we can specify the logic of a specific method without hard coding it, this will allow developers to define the logic and pass it to the method they need to use.
```cs
   class Program
    {
        static void Main(string[] args)
        {
            var emp = new Employee();
            var empList = new List<Employee>
            {
                new Employee{Id = 1, Name = "John", Experience = 5, Salary = 4500},
                new Employee{Id = 2, Name = "Jane", Experience = 1, Salary = 5500},
                new Employee{Id = 3, Name = "Sven", Experience = 10, Salary = 19500}
            };
            
            //we want to promote employees with experience greater than 5
            emp.PromoteEmployee(empList, x => x.Experience >= 5);
        }
    }
```

2. Below we implement the delegate
```cs
    public delegate bool IsPromotable(Employee employee);
    public class Employee
    {
        public string Name { get; set; }
        public int Id { get; set; }
        public int Salary { get; set; }
        public int Experience { get; set; }
        public void PromoteEmployee(List<Employee> employees, IsPromotable isPromotable)
        {
            foreach (var employee in employees)
            {
                if (isPromotable(employee))
                {
                    Console.WriteLine($"{employee.Name} can be promoted");
                }
            }
        }
    }
```
