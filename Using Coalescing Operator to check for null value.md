1. the ?? will check if str1 is null, if it is, it will recieve the value of "not null"
```cs
      static void Main(string[] args)
        {
            string str1 = null;

            string final = str1 ?? "not null";
            Console.WriteLine(final);
        }
```
