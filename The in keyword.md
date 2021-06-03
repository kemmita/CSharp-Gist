1. The in keyword allows you to send in a readonly reference to the memory of the args being passed in to a funciton. 
```cs
 public struct Point
    {
        public double X, Y;

        public Point(double x, double y)
        {
            X = x;
            Y = y;
        }

        public override string ToString()
        {
            return $"({X},{Y})";
        }
    }

    class Program
    {
        static double MeasureDistance(in Point p1, in Point p2)
        {
            var dx = p1.X - p2.X;
            var dy = p1.Y - p2.Y;

            return Math.Sqrt(dx * dx + dy * dy);
        }
        static void Main(string[] args)
        {
            var p1 = new Point(1,1);
            var p2 = new Point(7,9);

            Console.WriteLine(MeasureDistance(p1, p2));
        }
    }
```
