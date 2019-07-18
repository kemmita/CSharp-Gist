1. Create an additional project right next to your project titled yourprojectname.UnitTests, this will be under Test Unit Test project.
2. to create an actual test class, add a new class and name it classnameTests.cs
3. Below is the test class 
```cs
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using TestNinja.Fundamentals;

namespace TestNinja.UnitTests
{
    [TestClass]
    public class ReservationTests
    {
        [TestMethod]
        public void UserOldEnoughToOrderRoom_UserEntersOldEnoughAge_ReturnsTrue()
        {
            // Arrange - Act
            var reservation = new Reservation().UserOldEnoughToOrderRoom(new User {Age = 21});

            // Assert 
            Assert.IsTrue(result);
        }

        [TestMethod]
        public void UserOldEnoughToOrderRoom_UserEntersNotOldEnoughAge_ReturnsFalse()
        {
            var reservation = new Reservation().UserOldEnoughToOrderRoom(new User {Age = 12 });
            Assert.IsFalse(reservation);
        }
    }
}

```
4. Below is the actual class we are testing in the other project.
```cs
namespace TestNinja.Fundamentals
{
        public bool UserOldEnoughToOrderRoom(User user)
        {
            if(user.Age >= 21)
            {
                return true;
            }
            return false;
        }
        
    }

    public class User
    {
        public bool IsAdmin { get; set; }
        public bool IsCustomer{ get; set; }
        public int Age { get; set; }
    }
}
```
