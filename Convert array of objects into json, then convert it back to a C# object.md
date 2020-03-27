1. C# We use an Array of objects, for the example. but using a list of objects would also work the same way.
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

            var json = JsonConvert.SerializeObject(userAddresses);

            File.WriteAllText(@"addressArrayTest.json", json);
            
            
            //Below we must specify the type to deserialize to.
            var objResponse1 = JsonConvert.DeserializeObject<UserAddress[]>(json);

            foreach (var item in objResponse1)
            {
                Console.WriteLine(item.Id);
            }
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
