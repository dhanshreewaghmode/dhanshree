# dhanshree
package cases;

import java.io.IOException;

import org.apache.poi.EncryptedDocumentException;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

import dsw.Path_config;
import pom_class.Pom_method;

public class Test_case1 {
	
	public static  void main(String[] args) throws EncryptedDocumentException, IOException {
		System.setProperty("webdriver.chrome.driver",Path_config.chrome);
		
		WebDriver driver =new ChromeDriver();
		driver.get("https://facebook.com");
		driver.manage().window().maximize();
		
		Pom_method login = new Pom_method(driver);
		
		//login. UserID("dhanshreewaghmode@gmail.com");
		//login.EnterPass("31924082848");
		//login.clickLogin();
		Excel_third util=new Excel_third();
		login.UserID(util.excelRead(0,0));
		login.EnterPass(util.excelRead(0,1));
		login.clickLogin();
		
		Excel_third img = new Excel_third();
		img.Screen__shot(driver);
	}

}
