# ATM-Application
package programs;
import java.util.Scanner;
import java.util.ArrayList;
public class ATMApplication{
public static void main(String[] args) {
 
        String userName = "RISHITA GANGWAL";
        String password = "1234";
        String bankName = "XYZ Bank Limited";
        int balance=0;
        int minbal = 1500;
        boolean flag=true;
        ArrayList<String> trans = new ArrayList<String>();
 
        Scanner sc = new Scanner(System.in);
        System.out.println("Welcome to " + bankName);
        
        System.out.println("Please Enter Your PIN Number:  ");
        String enteredPassword = sc.nextLine();
        while(flag==true)
        {
        if (enteredPassword.equalsIgnoreCase(password))
        {
            System.out.println("Account Name Holder : " + userName);
            System.out.println("Please choose the following options- ");
            System.out.println("1. Transaction History");
            System.out.println("2. Withdrawal");
            System.out.println("3. Deposit Amount");
            System.out.println("4. Transfer Amount");
            System.out.println("5. Quit");
        }
        
            else{
            System.out.println("Oops! Your have entered wrong PIN Number.");
         }
        
            
        int option = sc.nextInt();
         
        switch(option)
        {
            case 1:
            {
                System.out.println("Your Transaction History");
                for(String q: trans)
                {
                    System.out.println(q);               
                }break;
            }  
            case 2:
            {    
              System.out.println("Please Enter the Amount to Witdraw: ");
                double withdrawAmount = sc.nextDouble();
                
                if (withdrawAmount > balance) {
                    System.out.println("Oh No! Insufficient Balance. Please Try Again..");
                } else {
                    balance -= withdrawAmount;
                    System.out.println("You have successfully withdraw " + withdrawAmount
                            + " \nNow your balnce is " + balance);
                }
                }break;
                case 3:
                {
                    System.out.println("Please Enter The Amount To Deposit: ");
                    double depositAmount = sc.nextDouble();
                
                    balance += depositAmount;
                    System.out.println("You have successfully deposited " + depositAmount
                        + " \nNow your balnce is " + balance);
               }break;    
               case 4:
               {
                 while(true)
                 {
                     System.out.println("Enter the account number of the beneficiary: ");
                     int accno=sc.nextInt();
                     System.out.println("Enter the IFSC code of the Bank of the beneficiary: ");
                     String ifsc =sc.next();
                     System.out.println(accno);
                     System.out.println("Please confirm the account number of the beneficiary: ");
                     System.out.println("1. Correct");
                     System.out.println("2. Inorrect");
                     int confo=sc.nextInt();
                     if(confo==1)
                     {
                       System.out.println("Enter the amount you want to transfer: ");
                       int transfamt=sc.nextInt();
                     if((transfamt % 10)==0)
                     {
                         if(transfamt <= balance)
                         {
                             if((balance - transfamt) < 1000)
                         {
                             System.out.println("Minimum balance has to be Rs1000");
                         }
                             else
                         {
                             balance = balance - transfamt;
                             String sf1= String.format("You have successfully transferred Rs %d to %d",transfamt,accno);
                             String sf2= String.format("Your balance is Rs %d",balance);
                             System.out.println(sf1);
                             System.out.println(sf2);
                             
                             String tf= String.format("Transfer - Rs %d",transfamt);
                             trans.add(tf);
                             break;
                        } 
                        }
                             else
                         {
                             System.out.println("Oh no! Insufficient Blance.. :(");
                         } 
                         }
                          else
                             System.out.println("Enter the amount in multiple of 100!");
                         }  
                             else
                             System.out.println("You entered incorrect account number!");
                         }   
                         break;
                        }
        
           
            case 5:
               {
                   System.out.println("THANK YOU FOR VISITNG OUR ATM!");
                   flag=false;
                   break;
               }
               default: 
                   System.out.println("Please choose a correct Option: ");
               break;
        }
        if(flag==true){
               System.out.println("Would you like to do another transaction?");
                    System.out.println("1. Yes");
                    System.out.println("2. No");
                    int df=sc.nextInt();
                    if(df==1)
                       flag = true;
                    else
                        flag = false;            
         }  
}
}
}
