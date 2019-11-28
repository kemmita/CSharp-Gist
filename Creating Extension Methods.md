1. Sometimes you will want to add a method to a class without edidting the class itself. You can do this using extenstion methods.
```cs
    class Program
    {
        static void Main(string[] args)
        {
            string post =
                "one tow three four five six seven";
            //string is a cealed class of Microsoft, we will not be able to edit the src code for this class directly, so we 
            //will create an extension method instead.
            var shortened = post.Shorten(5);
            int x = 10;

            Console.WriteLine(shortened);
        }
    }
```
2. We will need to create a new class, it will need to Be static.
```cs
   public static class StringExtensions
    {
    //In order to create the extension method, the method will need to be static and in some but not all have the same return type
    //of the class being extended. The params passed will need to contain at least one, it will be the stype extended so in this case
    //this String str, to understand "this" I will paste in the line of code above "var shortened = post.Shorten(5);"
    //see how we can take our variable post and append the method of shorten like so ".Shorten(5)" so below you could think of
    // this meaning "this.Shorten(5)" bc this = String and the String in this case is post
        public static string Shorten(this String str, int num)
        {
            if (num == 0)
            {
                return "";
            }

            var words = str.Split(' ');
            if (words.Length <= num)
            {
                return str;
            }

            return string.Join(" ", words.Take(num));
        }
    }
```
