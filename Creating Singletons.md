1. at times, we may only want to invoke a method once a time. To only have one instance run at a time.
```cs
    public sealed class Singleton
    {
        private static Singleton _instance = null;
        private Singleton() { }
        public static Singleton GetInstance
        {
            get
            {
                if (_instance == null)
                {
                    _instance = new Singleton();
                }

                return _instance;
            }
        }

        public void PrintDetails(string message)
        {
            Console.WriteLine(message);
        }
    }
```
2. Below we invoke Singletion.getinstance twice, but this will only run one instance at a time.
```cs
        static void Main(string[] args)
        {
            var s1 = Singleton.GetInstance;
            s1.PrintDetails("Here it is kid");
            var s2 = Singleton.GetInstance;
            s2.PrintDetails("here it is again");
        }
```
