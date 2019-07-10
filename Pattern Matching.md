1. Below we use the is keyword to detect the correct class
```cs
namespace TopicNewCSharp
{
    public class Shape { }

    public class Circle: Shape
    {
        public int Length { get; set; }
    }

    public class Square : Shape
    {
        public int Length { get; set; }
    }

    public class Rectangle : Shape
    {
        public int Length { get; set; }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Circle ci = new Circle();
            DisplayShape(ci);
        }
        public static void DisplayShape(Shape shape)
        {
            if (shape is Circle C)
            {
                Console.WriteLine(C.Length = 17);
            }
        }
    }
}
```
