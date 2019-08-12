```cs
namespace Gods
{
    enum Vehicle { Car, Van, Truck} 
    class Program
    {
        static void Main(string[] args)
        {
            var x = Vehicle.Car;
            Console.WriteLine(x);
            if (x == Vehicle.Car)
            {
                Console.WriteLine("true");
            }
        }
    }
}
```
