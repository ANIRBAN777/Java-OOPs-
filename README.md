# Java-OOPs-
Problem
AutonomousCar class – 
int carId, noOfTestsConducted, noOfTestsPassed;
String brand, environment, grade;
Use getter-setter. Create constructor which takes parameter except grade.

Create class Solution with main method. Implement 2 static methods – findTestPassedByEnv and updateCarGrade in Solution class.

	* 
findTestPassedByEnv method


This method will take 2 input parameters - array of AutonomousCar objects and string parameter environment. The method will return the sum of the noOfTestsPassed attribute from autonomousCar objects for the environment passed as parameter.
If no autonomousCar with the given environment is present in the array of AutonomousCar objects, then the method should return 0.

	* 
updateCarGrade method


This method will take a String parameter brand, along with the array of AutonomousCar objects. The method will return the autonomousCar object, if the input String parameter matches with the brand attribute of the autonomousCar object. Before returning the object, the grade should be derived based on the rating calculation mentioned below. This grade value should be assigned to the object. If any of the above conditions are not met, then the method should return null.
The grade attribute should be calculated as follows – 
rating=(noOfTestsPassed * 100)/noOfTestsConducted 
If the rating >= 80 then grade = ‘A1’, otherwise the grade = ‘B2’.
The above mentioned static methods should be called from the main method. 

For findTestPassedByEnv method – The main method should print the totalTestPassed as it is, if the returned value is greater than 0, or it should print “There are no tests passed in this particular environment”.

For updateCarGrade method – The main method should print the brand and grade of the returned autonomousCar object. The brand and grade should be concatinated with :: while printing. 
Ex – Tesla::A1, where Tesla is the brand and Al is the grade.
If the returned value is null then it should print “No Car is available with the specified brand”.

Before calling these static methods in main, use Scanner object to read the values of 4 autonomousCar objects (except grade attribute). 
Next, read the value for environment and brand.


Solution
Need
	* 
clear concept of Object access from method
	* 
clear concept of Object access its member variables
	* 
static method
	* 
array of objects
	* 
array of object pass to method parameter
	* 
String comparision
	* 
Object return from method




import java.util.Scanner;

class AutonomousCar{
    int carId, noOfTestsConducted, noOfTestsPassed;
    String brand, environment, grade;
    
    int getnoOfTestsPassed(){
        return noOfTestsPassed;
    }
    String getEnv(){
        return environment;
    }
    String getBrand(){
        return brand;
    }
}

public class Solution{
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        AutonomousCar ac[] = new AutonomousCar[4];
        for(int i=0;i<ac.length;i++){
            ac[i] = new AutonomousCar();
        }
        for(int i=0;i<ac.length;i++){
            ac[i].carId=sc.nextInt();
            ac[i].brand=sc.next();
            ac[i].noOfTestsConducted=sc.nextInt();
            ac[i].noOfTestsPassed=sc.nextInt();
            ac[i].environment=sc.next();
        }
        String env=sc.next();
        String brand=sc.next();
        int totalTestPassed=findTestPassedByEnv(ac, env);
        if(totalTestPassed==0)
            System.out.println("There are no tests passed in this particular environment");
        else
            System.out.println(totalTestPassed);
        AutonomousCar acar = updateCarGrade(ac, brand);  →  return object
        if(acar==null)
            System.out.println("No Car is available with the specified brand");
        else
            System.out.println(acar.getBrand()+"::"+acar.grade);
    }
    
    public static int findTestPassedByEnv(AutonomousCar ac[], String env){
        int test=0;
        for(int i=0;i<ac.length;i++){
            if(env.equalsIgnoreCase(ac[i].getEnv())){
                test+=ac[i].getnoOfTestsPassed();
            }
        }
        return test;
    }
    public static AutonomousCar updateCarGrade(AutonomousCar ac[], String brand){
        for(int i=0;i<ac.length;i++){
            if(brand.equalsIgnoreCase(ac[i].getBrand())){
                int rating=(ac[i].getnoOfTestsPassed()*100)/ac[i].noOfTestsConducted;
                if(rating >= 80)
                    ac[i].grade="A1";
                else
                    ac[i].grade="B2";
                return ac[i];    →  return object
            }
        }
        return null;
    }
}

Input
100    Tesla             1000     500     Hills
200    Ford              2000    1500   Desert
300    Royce            3000    1700   Hills
400    Mercedez     1000     400     Desert
Desert
Mercedez

Output
1900
Mercedez::B2







