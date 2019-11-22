```cs
namespace Tester
{
    class Program
    {
        static void Main(string[] args)
        {
            var users = new List<User>();
            for (int i = 1; i <= 1023; i++)
            {
                users.Add(new User
                {
                    Id = i,
                    Name = $"name{i}"
                });
            }

            for (int i = 1; i < users.Count; i++)
            {
                int Group = i;
                int RecordsPerGroup = 100;
                var usersToProcess = users.Skip((Group - 1) * RecordsPerGroup).Take(RecordsPerGroup).ToList();

                if (usersToProcess.Count > 0)
                {
                    Console.WriteLine($"Group#{i}****************");
                    foreach (var user in usersToProcess)
                    {
                        Console.WriteLine(user.Name);
                    }
                }
                else
                {
                    break;
                }
            }
 


        }
    }

    class User
    {
        public int Id { get; set; }
        public string Name { get; set; }
    }
}
```
