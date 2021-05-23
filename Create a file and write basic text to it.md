```cs
    class Program
    {

        static void Main(string[] args)
        {
            var dir = @"C:\Users\g656375\source\repos\ConsoleApp1\ConsoleApp1\TestDir";
            CreateDir(dir);

            using (StreamWriter fs = File.CreateText($@"{dir}\test.txt"))
            {
                fs.WriteAsync("Test Write Test");
            }
        }
        
        private static void CreateDir(string dir)
        {
            if (!Directory.Exists(dir))
            {
                var newDir = new DirectoryInfo(dir); 
                newDir.Create();
            }
        }

    }
```
