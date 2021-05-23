```cs
    class Program
    {
        static void Main(string[] args)
        {
            var dir = @"C:\Users\TestDir";
            CreateDir(dir);

            var f = new FileInfo($@"{dir}\test.txt");
            using (StreamWriter fs = f.CreateText())
            {
                fs.WriteAsync("Test Write");
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
