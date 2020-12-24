```cs
var crypto = new AesCryptoServiceProvider();
crypto.KeySize = 128;
crypto.BlockSize = 128;
crypto.GenerateKey();
var key = Convert.ToBase64String(crypto.Key);
```
