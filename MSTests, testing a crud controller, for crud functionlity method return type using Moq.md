1. The initial issue when wanting to test this controller is that no Repository/service is used to absrtract the logicv of intearcting with the databse.
```cs
using System.Data.Entity;

namespace TestNinja.Mocking
{
    public class EmployeeController
    {
        private EmployeeContext _db;

        public EmployeeController()
        {
            _db = new EmployeeContext();
        }

        public ActionResult DeleteEmployee(int id)
        {
            var employee = _db.Employees.Find(id);
            _db.Employees.Remove(employee);
            _db.SaveChanges();
            return RedirectToAction("Employees");
        }

        private ActionResult RedirectToAction(string employees)
        {
            return new RedirectResult();
        }
    }

    public class ActionResult { }
 
    public class RedirectResult : ActionResult { }
    
    public class EmployeeContext
    {
        public DbSet<Employee> Employees { get; set; }

        public void SaveChanges()
        {
        }
    }

    public class Employee
    {
    }
}
```
2. In order for us to write a Unit test, we will first need to create an interface of Employee and then implement that interface via a repository.
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace TestNinja.Mocking
{
    public interface IEmployeeRepository
    {
        void DeleteEmployee(int id);
    }
    public class EmployeeRepository : IEmployeeRepository
    {
        private EmployeeContext _employee;

        public EmployeeRepository()
        {
            _employee = new EmployeeContext();
        }

        public void DeleteEmployee(int id)
        {
            var employee = _employee.Employees.Find(id);
            if (employee == null) return;

            _employee.Employees.Remove(employee);
            _employee.SaveChanges();
        }

    }
}
```
3. we will now consume that repository in our EmployeeController
```cs
using System.Data.Entity;

namespace TestNinja.Mocking
{
    public class EmployeeController
    {
        private IEmployeeRepository _employee;

        public EmployeeController(IEmployeeRepository employee)
        {
            _employee = employee;
        }

        public ActionResult DeleteEmployee(int id)
        {
            _employee.DeleteEmployee(id);
            return RedirectToAction("Employees");
        }

        private ActionResult RedirectToAction(string employees)
        {
            return new RedirectResult();
        }
    }

    public class ActionResult { }

    public class RedirectResult : ActionResult { }

    public class EmployeeContext
    {
        public DbSet<Employee> Employees { get; set; }

        public void SaveChanges()
        {
        }
    }

    public class Employee
    {
    }
}
```
4. The Initial test is to verify we can delete a user.
```cs
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Moq;
using TestNinja.Mocking;

namespace TestNinja.Tests
{
    [TestClass]
    public class EmployeControllerTests
    {
        [TestMethod]
        public void DeleteEmployee_RedirectToEmployeeAction()
        {
            var employee = new Mock<IEmployeeRepository>();
            var controller = new EmployeeController(employee.Object);
            controller.DeleteEmployee(1);
            employee.Verify(e => e.DeleteEmployee(1));
        }

        [TestMethod]
        public void DeleteEmployeeMethodReturnTypeValidation_ReturnAction()
        {
            var employee = new Mock<IEmployeeRepository>();
            var controller = new EmployeeController(employee.Object);

            var result = controller.DeleteEmployee(1);
            Assert.IsInstanceOfType(result, typeof(ActionResult));
        }
    }
}

```
