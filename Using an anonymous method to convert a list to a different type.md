1. Conver the list to a different type.
```cs
    class Program
    {
        static void Main(string[] args)
        {
            var users = new List<User>
            {
                new User
                {
                    Id = 1, Name = "fred"
                }
            };

            var su = users.Select(x => {
                        return new SuperUser
                        {
                            Id = x.Id,
                            Name = x.Name
                        };
                    }).ToList();

            foreach (var item in su)
            {
                Console.WriteLine(item.Name);
            }
        }
    }

    class User
    {
        public int Id { get; set; }
        public string Name { get; set; }
    }

    class SuperUser
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public int Age { get; set; }
    }
```
