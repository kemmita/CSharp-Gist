1. Depending on the data provided, we can return two different types from the classes, we created.
```cs
namespace TestNinja.Fundamentals
{
    public class CustomerController
    {
        public ActionResult GetCustomer(int id)
        {
            if (id == 0)
                return new NotFound();
            
            return new Ok();
        }
    }
    
    public class ActionResult { }
    
    public class NotFound : ActionResult { }
 
    public class Ok : ActionResult { }
}
```
2. We use the IsInstanceOfType method provided by MSTests
```cs
        [TestMethod]
        public void GetCustomerTest()
        {
            var controller = new CustomerController();
            var result = controller.BDay(1989);
            Assert.IsInstanceOfType(result, typeof(int));
        }
```
