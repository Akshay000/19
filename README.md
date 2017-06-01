# 19
public class ExceptionHandling
{
    public static void main(String[] args)
    {
          Scanner sc = new Scanner(System.in);  //Declaring Scanner variable to take input from user
 
          System.out.println("Enter Your Age");
 
          int age = sc.nextInt();         //Taking input from user
 
          try
          {
              if(age < 0)
              {
                  throw new Exception();    //throws an Exception if age is negative
              }
          }
          catch(Exception ex)
          {
              System.out.println(ex);     //Prints exception description
          }
    }
}


//Defining Our own exception by extending Exception class
 
class AgeIsNegativeException extends Exception
{
    String errorMessage;
 
    public AgeIsNegativeException(String errorMessage)
    {
        this.errorMessage = errorMessage;
    }
 
    //Modifying toString() method to display customized error message
 
    @Override
    public String toString()
    {
        return errorMessage;
    }
}


public class ExceptionHandling
{
    public static void main(String[] args)
    {
          Scanner sc = new Scanner(System.in);  //Declaring Scanner variable to take input from user
 
          System.out.println("Enter Your Age");
 
          int age = sc.nextInt();         //Taking input from user
 
          try
          {
              if(age < 0)
              {
                  throw new AgeIsNegativeException("Age can not be negative");    //throws AgeIsNegativeException if age is negative
              }
          }
          catch(AgeIsNegativeException ex)
          {
              System.out.println(ex);    //Output : Age can not be negative
          }
    }
}


//Defining Our own exception class by extending ArithmeticException class
 
class InvalidWithdrawlMoneyException extends ArithmeticException
{
    //Overriding toString() method of ArithmeticException as per our needs
 
    @Override
    public String toString()
    {
        return "You don't have that much of money in your account";
    }
}
 
//Using above customized ArithmeticException
public class ExceptionHandling
{
    public static void main(String[] args)
    {
        int balance = 5000;            //Initializing the balance
 
        Scanner sc = new Scanner(System.in);     //Scanner variable to take input from user
 
        System.out.println("Enter Withdrawl Money");
 
        int withdrawlMoney = sc.nextInt();      //taking input from the user
 
        try
        {
            //checking withdrawl money with the balance
            //if withdrawl money is more than the balance,
            //then it throws Exception
 
            if(withdrawlMoney > balance)
            {
                throw new InvalidWithdrawlMoneyException();
            }
            else
            {
                System.out.println("Transaction Successful");
            }
        }
        catch(InvalidWithdrawlMoneyException ex)
        {
            //InvalidWithdrawlMoneyException will be caught here
 
            System.out.println(ex);
        }
    }
}


public class ExceptionHandling
{
    public static void main(String[] args)
    {
        int balance = 5000;            //Initializing the balance
 
        Scanner sc = new Scanner(System.in);     //Scanner variable to take input from user
 
        System.out.println("Enter Withdrawl Money");
 
        int withdrawlMoney = sc.nextInt();      //taking input from the user
 
        try
        {
            //checking withdrawl money with the balance
            //if withdrawl money is more than the balance,
            //then it throws Exception
 
            if(withdrawlMoney > balance)
            {
                //throwing exception using anonymous inner class
 
                throw new ArithmeticException()
                {
                    @Override
                    public String toString()
                    {
                        return "You don't have that much of money in your account";
                    }
                };
            }
            else
            {
                System.out.println("Transaction Successful");
            }
        }
        catch(ArithmeticException ex)
        {
            System.out.println(ex);
        }
    }
}
