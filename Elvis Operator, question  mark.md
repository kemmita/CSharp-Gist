1. The elvis operator is used to check if an element is null just like the terenary operator can be used.
```cs
 class Program
    {
        static void Main(string[] args)
        {
            string str = null;
            string strCheck = (str == null ? null : str.ToString());
            string strCheckV2 = str?.ToString();
            Console.WriteLine(strCheck);
            Console.WriteLine(strCheckV2);
        }
    }
```
