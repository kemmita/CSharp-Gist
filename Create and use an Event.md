1. First we will want to create a class that will contain the event signature
```cs
namespace Tester
{
    public class VideoEncoder
    {
        //Define Event
        public event EventHandler<EventArgs> VideoEncoded;
        //Raise Event
        protected virtual void OnVideoEncoded()
        {
            VideoEncoded?.Invoke(this, EventArgs.Empty);
        }
        public void Encode(Video video)
        {
            Console.WriteLine("Encoding Video....");
            Thread.Sleep(3000);
            OnVideoEncoded();
        }
    }
}
```
2. Next we will create a class and within that class we will have a method that will subscribe to the event.
```cs
namespace Tester
{
    public class MailService
    {
        public void OnVideoEncoded(object source, EventArgs e)
        {
            Console.WriteLine("Send email");
        }
    }
}
```
3. program.cs
```cs
namespace Tester
{
    class Program
    {
        static void Main(string[] args)
        {
            var video = new Video() { Titile = "Video 1" };
            var videoEncoder = new VideoEncoder();// publisher
            var mailService = new MailService();// subscriber
            videoEncoder.VideoEncoded += mailService.OnVideoEncoded;
            videoEncoder.Encode(video);
        }
    }
}
```
