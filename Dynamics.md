1. Dynamics allow you to change the data type of the variable on the go.
```cs
    static void Main(string[] args)
        {
            dynamic variable = "Russ";
            Console.WriteLine(variable);
            variable = 10;
            Console.WriteLine(variable);
        }
```
