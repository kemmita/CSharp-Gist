1. We can use the out keyword to return more than one return type.
```cs
  static void Main(string[] args)
        {
            // you must define the out modifier when calling the method
            BanksReaction(7.2m, out string message, out bool approved);

            Console.WriteLine($"{message}, {approved}");

            Console.ReadLine();
        }
        
        // this method must declare void as a return type.
        static void BanksReaction(decimal x, out string message, out bool approved)
        {
            if (x > 6.8m)
            {
                message = "Welcome to the bank!";

                approved = true;
            }
            else 
            {
                message = "Leave the bank!";

                approved = false;
            }
        }
```
