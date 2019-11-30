1. We will create a new abstract class for a basic database class.
```cs
   public abstract class Database
    {
        public virtual string Connection { get; set; }
        public virtual string Command { get; set; }

        public abstract string DatabaseOverview();
    }
```
2. Below is two concrete implementations.
```cs
    public class SQLServerDB : Database
    {
        public override string Connection { get; set; } = "sql connection";
        public override string Command { get; set; } = "sql command";

        public override string DatabaseOverview()
        {
            return "Common Relation DB";
        }
    }
    
        public class OleDB : Database
    {
        public override string Connection { get; set; } = "oledb conneciton";
        public override string Command { get; set; } = "oledb command";

        public override string DatabaseOverview()
        {
            return "OLD Relation DB";
        }
    }
```
3. Based on what the user enters our abstract class will intiliaze in two the form of one of the two concrete classes above.
```cs
        static void Main(string[] args)
        {
            Database database;
            var read = Console.ReadLine();
            if (read.Equals("SQL"))
            {
                database = new SQLServerDB();
                Console.WriteLine(database.Connection);
                Console.WriteLine(database.Command);
            }
            else
            {
                database = new OleDB();
                Console.WriteLine(database.Connection, database.Command);
            }

            Console.WriteLine(database.DatabaseOverview());

        }
```
