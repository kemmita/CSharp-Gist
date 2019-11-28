1. The only data type commonly used in .NET that can be null is string, if we want to make other types nullable, we can do so like
below.
```cs
  static void Main(string[] args)
        {
            int? x = null;
        }
```
2. If you want to check if a nullable has a value, use the ".HasValue" method
```cs
  static void Main(string[] args)
        {
            int? x = null;
            int y;

            if (x.HasValue)
            {
                y = x.Value;
            }
            else
            {
                y = x.GetValueOrDefault();
            }
        }
```
3. If you want to assign the value of a nullable to a non nullable, you can do so like below using the ".GetValueOrDefault" method
```cs
      static void Main(string[] args)
        {
            int? x = null;
            int y;
            y = x.GetValueOrDefault();
        }
```
