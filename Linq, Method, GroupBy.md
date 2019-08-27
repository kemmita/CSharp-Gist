       List<Person> people = new List<Person>()
                    {
                        new Person("Tod", "Vachev", 1, 180, 21, Gender.Male),
                        new Person("MIke", "Blanch", 1, 180, 21, Gender.Male),
                        new Person("Tod", "Vachev", 1, 180, 26, Gender.Male),
                        new Person("Tod", "Vachev", 1, 180, 29, Gender.Male),
                        new Person("John", "Johnson", 2, 170, 10, Gender.Male),
                        new Person("Anna", "Maria", 3, 150, 22, Gender.Female),
                        new Person("Kyle", "Wilson", 4, 164, 12, Gender.Male),
                        new Person("Anna", "Williams", 5, 164, 65, Gender.Male),
                        new Person("Maria", "Ann", 6, 160, 19, Gender.Female),
                        new Person("John", "Jones", 7, 160, 22, Gender.Male),
                        new Person("Samba", "TheLion", 8, 175, 78, Gender.Male),
                        new Person("Aaron", "Myers", 9, 182, 23, Gender.Male),
                        new Person("Aby", "Wood", 10, 165, 20, Gender.Female),
                        new Person("Maddie", "Lewis", 11, 160, 19, Gender.Female),
                        new Person("Lara", "Croft", 12, 162, 23, Gender.Female)
                    };
            var multiKey = people.GroupBy(p => new {p.Gender, p.Age});
            foreach (var key in multiKey)
            {
                Console.WriteLine(key.Key);
                foreach (var p in key)
                {
                    Console.WriteLine(p.FirstName);
                }
            }

            Console.ReadLine();
        }
