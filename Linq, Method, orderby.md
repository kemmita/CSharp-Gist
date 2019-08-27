1. Below we use Orderby to order customer by there name for those who live in London.
```cs
namespace Tester
{

    class Program
    {
        static void Main(string[] args)
        {
            var customers = new List<Customer>
            {
                new Customer{Name = "John", City = "London"},
                new Customer{Name = "Sam", City = "London"},
                new Customer{Name = "Russ", City = "Berlin"},
            };
            var cust = customers.Where(c => c.City == "London").OrderBy(c => c.Name);
            foreach (var c in cust)
            {
                Console.WriteLine(c.Name);
            }
        }

    }
    class Customer
    {
        public string Name { get; set; }
        public string City { get; set; }
    }

}
```
