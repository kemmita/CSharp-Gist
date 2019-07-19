1. Below we have a function that returns all of the odd numbers in a given array.
```cs
   public IEnumerable<int> GetOddNumbers(int limit)
        {
            for (var i = 0; i <= limit; i++)
                if (i % 2 != 0)
                    yield return i; 
        }
```
2. Below in our unit test, we will verify that the array returned above, returns 1,3,5 when given a max value of 5
```cs
   [TestMethod]
        public void GetOddNumbers_ReturnOddNumbers_Passing()
        {
            var result = new Fundamentals.Math().GetOddNumbers(5);
            Assert.AreEqual(result, new[] { 1,3,5});
        }
```
