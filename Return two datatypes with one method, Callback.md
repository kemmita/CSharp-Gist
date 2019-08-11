1. Using a delegate we can return datatypes. We use the call back to set a value based on the return type of the method called. Once we know the return of the initial method, we can then go to where we called the method and use a callback to return a nother datatype.

2. First class
```cs
      public class Thor 
    {
        public delegate void Del(int num);

        // Create a method for a delegate.
        public static void DelegateMethod(string message)
        {
            System.Console.WriteLine(message);
        }

        public string ReturnTwo(int year, Del callback)
        {
            if (year >= 1940)
            {
                callback(1);
                return "We will not buy the book submitted";
            }
            else
            {
                callback(0);
                return "We will buy the book submitted";
            }
            return "we will buy your book";
        }
    }
```
3. Class that will instantiate the method above and will use the callback delegate function to declare a bool value. 
```cs
    class Program
    {
        static void Main(string[] args)
        {
            var t = new Thor();
            bool choice = true;
            //we returned the original string type of the method called and then based on the delegat param returned, we set a bool                   property.
            Console.WriteLine(
            t.ReturnTwo(1955, delegate(int num)
            {
                var c = num == 0 ? choice = true : choice = false;
            }));
            Console.WriteLine(choice);
        }
    }
```
