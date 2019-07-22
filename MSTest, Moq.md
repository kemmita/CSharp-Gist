1. Service class
```cs
namespace TestNinja.Mocking
{
    public interface IFileReader
    {
        string Read(string path);
    }
    public class FileReader : IFileReader
    {
        public string Read(string path)
        {
            return File.ReadAllText(path);
        }
    }
}
```
2. Video Service class
```cs
namespace TestNinja.Mocking
{
    public class VideoService
    {
        private IFileReader _fileReader;
        public VideoService(IFileReader fileReader = null)
        {
            _fileReader = fileReader ?? new FileReader();
        }
        public string ReadVideoTitle()
        {
            var str = _fileReader.Read("C:/ConsoleAppTest/Program.cs");
            var video = JsonConvert.DeserializeObject<Video>(str);
            if (video == null)
                return "Error parsing the video.";
            return video.Title;
        }
   }
}
```
3. VideoServiceTests
```cs
namespace TestNinja.Tests.Mocking
{
    [TestClass]
    public class VideoServiceTests
    {
        [TestMethod]
        [ExpectedException(typeof(ArgumentNullException))]
        public void ReadVideoTitle_EmptyFile_ReturnError()
        {
            var filereader = new Mock<IFileReader>();

            filereader.Setup(fr => fr.Read("vide.txt")).Returns("");

            var service = new VideoService(filereader.Object);

            var result = service.ReadVideoTitle();

            Assert.AreEqual(result, "");
        }
    }
}
```
