# Job_Scheduling_Greedy_Method
import java.util.*;
public class Job_scheduling {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        System.out.print("Enter the number of Jobs: ");
        int n=sc.nextInt();
        String jobs[]=new String[n];
        int profits[]=new int[n];
        int deadlines[]=new int[n];
        System.out.print("Enter the Jobs: ");
        for(int i=0;i<n;i++) {

            jobs[i] = sc.next();
        }
            System.out.print("Enter the Profits:");
        for(int i=0;i<n;i++) {
            profits[i]=sc.nextInt();

        }

            System.out.print("Enter the DeadLines:");
        for(int i=0;i<n;i++) {

            deadlines[i]=sc.nextInt();
        }

        for(int i=0;i<n-1;i++)
        {
            for(int j=i+1;j<n;j++)
            {
                if(profits[i]<profits[j])
                {
                    int temp=profits[i];
                    profits[i]=profits[j];
                    profits[j]=temp;

                    temp=deadlines[i];
                    deadlines[i]=deadlines[j];
                    deadlines[j]=temp;

                    String temp1=jobs[i];
                    jobs[i]=jobs[j];
                    jobs[j]=temp1;
                }
            }
        }
        System.out.println("---Ordering Paradigm---");
        System.out.print("Jobs: ");
        for(int i=0;i<n;i++)
        {
            System.out.print(jobs[i]+" ");
        }
        System.out.println();
        System.out.print("Profits:  ");
        for(int i=0;i<n;i++)
        {
            System.out.print(profits[i]+" ");
        }
        System.out.println();
        System.out.print("DeadLines: ");
        for(int i=0;i<n;i++)
        {
            System.out.print(deadlines[i]+" ");
        }
        System.out.println();
        System.out.println("-----------------------");
        // to find the maximum of deadlines cuz that is the total time alloted
        int max=deadlines[0];
        for(int i=0;i<n;i++)
        {
            if(deadlines[i]>max)
            {
                max=deadlines[i];
            }
        }
        String x[]=new String[max];
        int profit=0;
        for(int i=0;i<n;i++)
        {
            int pp=deadlines[i];
            pp=pp-1;
            if(x[pp]==null )
            {
                x[pp]=jobs[i];
                profit+=profits[i];
            }
            else
            {
                while(pp!=-1)
                {
                    if(x[pp]==null)
                    {
                        x[pp]=jobs[i];
                        profit+=profits[i];
                        break;
                    }
                    pp=pp-1;
                }
            }

        }
        System.out.print("The order in which jobs has to be done to earn maximum profit:");
        for(int i=0;i<max;i++)
        {
            System.out.print(x[i]+" ");
        }
        System.out.println();
        System.out.print("Profit Earned: "+profit);
    }
}
