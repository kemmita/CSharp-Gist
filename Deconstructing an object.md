```cs
 class Program
    {
        static void Main(string[] args)
        {

            var p = new person{Id =  1, Name = "Sam"};

            var (id,name) = p;

            Console.WriteLine(name);

            Console.Read();
        }

    }

    class person
    {
        public int Id { get; set; }
        public string Name { get; set; }

        public void Deconstruct(out int id, out string name)
        {
            id = Id;
            name = Name;
        }
    }
```
