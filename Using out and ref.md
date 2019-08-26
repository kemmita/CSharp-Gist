1. Usintg out or ref allows you to pass a var to your method that will in the end be asisgned a value, this value can be used throughout the rest of your application.
```cs
    class Program
    {
        static void Main(string[] args)
        {
            int a = 5;
            int b = 5;
            int result;
            AddNum(a, b, out result);
            Console.WriteLine(result);
        }

        public static int AddNum(int first, int second, out int result)
        {
            return result = first + second;
        }
    }
```
2. Before ref or out, we would have simply used
```cs
    class Program
    {
        static void Main(string[] args)
        {
            int a = 5;
            int b = 5;
            int result = AddNum(a, b);
            Console.WriteLine(result);
        }

        public static int AddNum(int first, int second)
        {
            return first + second;
        }
    }
```
