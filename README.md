# TEST-SCRIPT-
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import java.util.concurrent.TimeUnit;
import java.io.File;
import org.apache.commons.io.FileUtils;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.Point;
import java.awt.image.BufferedImage;
public class ScreenshotElement{
   public static void main(String[] args) {
      System.setProperty("webdriver.chrome.driver", "C:\\Users\\ghs6kor\\Desktop\\Java\\chromedriver.exe");
      WebDriver driver = new ChromeDriver();
      String url ="https://www.tutorialspoint.com/about/about_careers.htm";
      driver.get(url);
      driver.manage().timeouts().implicitlyWait(12, TimeUnit.SECONDS);
      // identify logo
      WebElement l=driver.findElement(By.xpath( "//*[@class='top-logo']"));
      // capture screenshot and store the image
      File s = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
      BufferedImage f = ImageIO.read(s);
      //location of webelement
      Point location= l.getLocation();
      // Dimension of element
      int w= l.getSize().getWidth();
      int h=l.getSize().getHeight();
      // Image Crop
      BufferedImage cImage= f.getSubimage(location.getX(), location.getY(), w, h);
      ImageIO.write(cImage, "png", s);
      FileUtils.copyFile(s, new File("tutorialpointlogo.png"));
      driver.quit();
   }
}
