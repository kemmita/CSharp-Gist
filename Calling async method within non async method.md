1. Async Methos
```cs
static async Task<string> DoWorkAsync()
        {
            return await Task.Run(() =>
            {
                Thread.Sleep(5000);
                return "Work is done.";
            });
        }
```
2. Non async method to call method above.
```cs
static void Main(string[] args)
        {
            var res = DoWorkAsync().Result;
            Console.WriteLine(res);
        }
```
3. If it is a async method returning void, use th4e Wait keyword instead of Result.
```cs
static void Main(string[] args)
        {
            var res = DoWorkWithNoReturnTypeAsync().Wait();
        }
```
