1. Below is the method we are testing against.
```cs
        public static int Divide(int numerator, int denominator)
        {
            if (denominator == 0)
            {
                throw new DivideByZeroException("Denominator is zero.");
            }
            return numerator / denominator;
        }
```

2. Below is the untitest
```cs
     [TestMethod]
        [ExpectedException(typeof(DivideByZeroException))]
        public void Test_Divide_DenominatorisZero()
        {
            Library.Calculator.Divide(6, 0);
        }
```
