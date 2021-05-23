1. Method that will take 5+ seconds to complete.
```cs
        private void DoTimeConsumingWork()
        {
            Thread.Sleep(5000);
            System.IO.StreamWriter writer = new System.IO.StreamWriter("test.txt"); //open the file for writing.
            writer.Write(DateTime.Now.ToString()); //write the current date to the file. change this with your date or something.
            writer.Close(); //remember to close the file again.
            writer.Dispose(); //remember to dispose it from the memory.
        }
```
2. To make this method call async wrap it in a Task.Run and await it.
```cs
        private async void button1_Click(object sender, EventArgs e)
        {
            button1.Enabled = false;
            
            // Here is the method call.
            await Task.Run(DoTimeConsumingWork);

            button1.Enabled = true;
        }
```
