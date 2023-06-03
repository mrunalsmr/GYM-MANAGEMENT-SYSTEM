# GYM-MANAGEMENT-SYSTEM
//Fitness centers and gyms play a vital role in helping individuals achieve their fitness goals and maintain a healthy lifestyle. However, managing a gym efficiently can be a challenging task, requiring careful organization, effective communication, and streamlined processes.
import java.util.*;

import java.io.*;

class MainMenu

{

  public void menu()

  {

    System.out.println("\t\t\t\t\t WELCOME TO GYM MANAGEMENT SYSTEM");

    System.out.println("\n\nPress 1 : To insert new trainee");

    System.out.println("Press 2 : To see existing trainees ");

    System.out.println("Press 3 : To remove trainee");

    System.out.println("Press 4 : To modify trainee details");

    System.out.println("Press 5 : for weekly schedule");

    System.out.println("Press 6 : To Exit ");

  }

}

class Trainee_Add

{

    public void createFile()

    {

        Scanner sc=new Scanner(System.in);

 

        TraineeDetail emp=new TraineeDetail();

        emp.getInfo();

        try{

            File f1=new File("file"+emp.trainee_id+".txt");

            if(f1.createNewFile()){

                FileWriter myWriter = new FileWriter("file"+emp.trainee_id+".txt");

                myWriter.write("Trainee ID:"+emp.trainee_id+"\n"+"Trainee Name     :"+emp.name+"\n"+

                "Traineee Salary   :"+emp.trainee_fee);

                myWriter.close();

                System.out.println("\nTrainee data has been Added :)\n");

 

                System.out.print("\nPress Enter to Continue...");

                sc.nextLine();

            }

            else {

                System.out.println("\nTrainee already exists :(");

                System.out.print("\nPress Enter to Continue...");

                sc.nextLine();

            }

        }

        catch(Exception e){System.out.println(e);}

    }

}

 

class TraineeDetail

{

    String name;

    String trainee_id;

    String trainee_fee;

    String trainee_contact;

    public void getInfo()

    {

        Scanner sc=new Scanner(System.in);

        System.out.print("Enter Trainee's name --------: ");

        name=sc.nextLine();

        System.out.print("Enter trainee's ID ----------: ");

        trainee_id=sc.nextLine();

        System.out.print("Enter contact Info --: ");

        trainee_contact=sc.nextLine();

        System.out.print("Enter trainee's fees ------: ");

        trainee_fee=sc.nextLine();

    }

}

 

class Trainee_Show

{

  public void viewFile(String s) throws Exception

  {

    File file = new File("file"+s+".txt");

    Scanner sc = new Scanner(file);

 

    while (sc.hasNextLine())

     {

       System.out.println(sc.nextLine());

     }

   }

}

 

 

class Trainee_Remove

{

    public void removeFile(String ID)

    {

 

    File file = new File("file"+ID+".txt");

      if(file.exists())

       {

         if(file.delete());

         {

           System.out.println("\nTrainee has been removed Successfully");

         }

       }

      else

       {

            System.out.println("\nTrainee does not exists :( ");

       }

     }

}

 

class Trainee_Update

{

  public void updateFile(String s,String o,String n) throws IOException

  {

   File file = new File("file"+s+".txt");

   Scanner sc = new Scanner(file);

   String fileContext="";

   while (sc.hasNextLine())

       {

         fileContext =fileContext+"\n"+sc.nextLine();

       }

   FileWriter myWriter = new FileWriter("file"+s+".txt");

   fileContext = fileContext.replaceAll(o,n);

   myWriter.write(fileContext);

   myWriter.close();

 

  }

}

 

class CodeExit

{

  public void out()

  {

    System.out.println("Thank you ");

    System.exit(0);

  }

}

 

class GymManagementSystem

{

  public static void main(String arv[])

  {

    /* To clear the output Screen */

    System.out.print("\033[H\033[2J");

 

    Scanner sc=new Scanner(System.in);

    Trainee_Show epv =new Trainee_Show();

 

    int i=0;

 

    MainMenu obj1 = new MainMenu();

    obj1.menu();

    while(i<7)

    {

 

      System.out.print("\nPlease Enter choice :");

      i=Integer.parseInt(sc.nextLine());

 

      /* Switch Case Statements */

      switch(i)

      {

        case 1:

        {

        Trainee_Add ep =new Trainee_Add();

        ep.createFile();

 

        System.out.print("\033[H\033[2J");

        obj1.menu();

        break;

        }

        case 2:

        {

          System.out.print("\nPlease Enter trainee's id :");

          String s=sc.nextLine();

          try

          {

            epv.viewFile(s);}

            catch(Exception e){System.out.println(e);}

 

            System.out.print("\nPress Enter to Continue...");

            sc.nextLine();

            System.out.print("\033[H\033[2J");

            obj1.menu();

            break;

          }

 

        case 3:

        {

          System.out.print("\nPlease Enter trainee's ID :");

          String s=sc.nextLine();

          Trainee_Remove epr =new Trainee_Remove();

          epr.removeFile(s);

 

          System.out.print("\nPress Enter to Continue...");

          sc.nextLine();

          System.out.print("\033[H\033[2J");

          obj1.menu();

          break;

        }

        case 4:

        {

            System.out.print("\nPlease Enter Trainee's ID :");

            String I=sc.nextLine();

            try

            {

              epv.viewFile(I);

            }

            catch(Exception e)

            {

              System.out.println(e);

            }

            Trainee_Update epu = new Trainee_Update();

            System.out.print("Please Enter the detail you want to Update :");

    	      System.out.print("\nFor Example :\n");

 

            System.out.println("If you want to Change the Name, then Enter Current Name and Press Enter. Then write the new Name then Press Enter. It will Update the Name.\n");

            String s=sc.nextLine();

            System.out.print("Please Enter the Updated Info :");

            String n=sc.nextLine();

            try

            {

              epu.updateFile(I,s,n);

 

              System.out.print("\nPress Enter to Continue...");

              sc.nextLine();

              System.out.print("\033[H\033[2J");

              obj1.menu();

              break;

            }

            catch(IOException e)

            {

              System.out.println(e);

            }

        }

        case 6:

        {

          CodeExit obj = new CodeExit();

          obj.out();

        }

        case 5:

        {

        	 System.out.print("Monday : Legs");

        	 System.out.print("\nTuesday : Biceps");

        	 System.out.print("\nWednesday: Triceps");

        	 System.out.print("\nThursay : Thread");

        	 System.out.print("\nfriday : Hardcore body");

        	 System.out.print("\nSaturday : Muscles");

        	 System.out.print("\n\t\t \tAll the trainers are requested to follow this schedule");

        }

        	

      }

    }

  }

}

