1. By using the select linq operator, we can transform our data, below we transform our list being created to only return
the customer name.
```cs
 class Program
    {
        static void Main(string[] args)
        {
            var customers = new List<Customer>
            {
                new Customer{Name = "John", City = "London"},
                new Customer{Name = "Sam", City = "London"},
                new Customer{Name = "Russ", City = "Berlin"},
                new Customer{Name = "Russ", City = "Berlin"},
                new Customer{Name = "Russ", City = "Berlin"},
                new Customer{Name = "Russ", City = "Berlin"},
            };
            var countries = new List<Country>
            {
                new Country{Name = "England", City = "London"},
                new Country{Name = "Germany", City = "Berlin"},
            };
            var customer = customers.Where(c => c.City == "Berlin").Select(c => c.Name);
            foreach (var item in customer)
            {
                Console.WriteLine(item);
            }
        }
    }
```
