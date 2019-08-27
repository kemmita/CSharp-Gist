1. Using Generics, we can create reusable code, below we alter the data type of a class.
```cs
namespace Tester
{
    class Couple<T>
    {
        public T First { get; set; }
        public T Second { get; set; }
    } 
    class Program
    {
        static void Main(string[] args)
        {
            var c = new Couple<int>();
            c.First = 1;
            c.Second = 2;

            var cV2 = new Couple<double>();
            cV2.First = 1.99;
            cV2.Second = 2.99;
        }

    }

}
```
2. Below is a Generic method we can use to itterate over a list no matter the data type past.
```cs
   class Program
    {
        static void Main(string[] args)
        {
            var strList = new List<string>
            {
                "str1",
                "str2",
                "str3",
                "str4",
            };
            PrintItems(strList);
        }
        public static void PrintItems<T>(List<T> items)
        {
            foreach (var item in items)
            {
                Console.WriteLine(item);
            }
        }

    }
```
