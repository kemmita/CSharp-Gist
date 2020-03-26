1. We will first create the EventClass
```cs
  public class EventClass 
    {
        //First declare our EventHandler. Then bring in the classes that will subscribe to the event.
        public event EventHandler OnPurchase;
        private readonly Stock _stock;
        private readonly Boss _boss;
        
        public EventClass()
        {
            _stock = new Stock();
            _boss = new Boss();
            Subscribe();
        }
        
        //Below we subscribe the classes and their specific methods to the event.
        public void Subscribe()
        {
            OnPurchase += _stock.StockGoingUp;
            OnPurchase += _boss.TellBoss;
        }
        
        //When this function is called in the main programm class, all funcitons listening in other classes will fire off.
        public void Purchase(bool purchased)
        {
            if (purchased)
            {
                OnPurchase?.Invoke(this, EventArgs.Empty);
            }
        }
    }
```
2. Here are the two classes and the functions that will fire off when tghe event is invoked.
```cs
   public class Stock
    {
        public void StockGoingUp(object sender, EventArgs e)
        {
            Console.WriteLine("Stock went up today!");
        }
    }
    
      public class Boss
    {
        public void TellBoss(object sender, EventArgs e)
        {
            Console.WriteLine("The boss was told");
        }
    }
```
3. Finally in our main program class, we trigger the method that will invoke the event
```cs
    class Program
    {
        static void Main(string[] args)
        {
            var e = new EventClass();

            Console.WriteLine("Would you like to purchase the item?");

            var response = Console.ReadLine();

            if (response.Equals("yes"))
            {
                e.Purchase(true);
            }
            else
            {
                e.Purchase(false);
            }
        }
    }
```
