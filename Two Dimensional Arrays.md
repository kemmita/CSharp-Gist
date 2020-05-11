```cs
        static void Main(string[] args)
        {
              // below we have a 3 row by 4 col array.
             var x = new int[3, 4];

            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 4; j++)
                {
                    // each col for the respective row will be filled befoe jumping to the next row.
                    x[i, j] = i * j;
                }
            }


            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 4; j++)
                {
                    Console.Write(x[i,j] + "\t");
                }
            }

            Console.Read();
        }
```
