1. C#
```cs
    class Program
    {
        static void Main(string[] args)
        {
            var userAddresses = new UserAddress[2]
            {
                new UserAddress{Id = 1, Street = "Street 1", Zip = "44021"},
                new UserAddress{Id = 2, Street = "Street 2", Zip = "54021"}
            };

            var json = JsonConvert.SerializeObject(new
            {
                //Without defining this name below the json would be provided without a name for the array containing the objects.
                userAddresses = userAddresses
            });

            File.WriteAllText(@"addressArrayTest.json", json);
        }
    }

    class UserAddress
    {
        public int Id { get; set; }
        public string Street { get; set; }
        public string Zip { get; set; }
    }
```
2. Below is the JSON produced
```json
{"userAddresses":
    [
        {"Id":1,"Street":"Street 1","Zip":"44021"},
        {"Id":2,"Street":"Street 2","Zip":"54021"}
    ]
}
```
