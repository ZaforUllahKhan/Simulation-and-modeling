# Simulation-and-modeling
#include<stdio.h>
#include<conio.h>
int total_waiting_time=0,total_idle_time=0,wait_count=0;
struct simulation{
    int cust_no;
    int rd_ar;
    int intr_arr_time;
    int arr_time;
};

typedef struct simulation Simulation;

void schedule_arrival_time (Simulation s[],int n);

main(){

    Simulation s[200];
    int i,j,n=0;
    printf(" Enter customer number: ");
    scanf("%d",&n);
    printf(" Enter random digit for arrival time for each customer: \n");
    for(i=1;i<2;i++){
      printf("  RD.Arrival[1]: -\n");
      s[i].cust_no=1;
      s[i].rd_ar=0;
      s[i].intr_arr_time=0;
    }
    for(i=2;i<=n;i++){
        printf("  RD.Arrival[%d]: ",i);
        scanf("%d",&s[i].rd_ar);
        s[i].cust_no=i;
        if(s[i].rd_ar > 0 && s[i].rd_ar < 10) s[i].intr_arr_time=1;
        else if(s[i].rd_ar > 11 && s[i].rd_ar < 20) s[i].intr_arr_time=2;
        else if(s[i].rd_ar > 21 && s[i].rd_ar < 30) s[i].intr_arr_time=3;
        else if(s[i].rd_ar > 31 && s[i].rd_ar < 40) s[i].intr_arr_time=4;
        else if(s[i].rd_ar > 41 && s[i].rd_ar < 50) s[i].intr_arr_time=5;
        else if(s[i].rd_ar > 51 && s[i].rd_ar < 60) s[i].intr_arr_time=6;
        else if(s[i].rd_ar > 61 && s[i].rd_ar < 70) s[i].intr_arr_time=7;
        else if(s[i].rd_ar > 71 && s[i].rd_ar < 100) s[i].intr_arr_time=8;
        else{printf(" Warning!! Please Enter RD. around 1-99"); return 0;}
    }

    schedule_arrival_time( s, n);

     printf("\n   -----------------------------------------\n");
    printf("\n  | Cust.| RD. for | Inter_arrival | Arrival \n");
    printf("  |  No. |Arrival.T|     Time      |  Time   |\n");
    printf("\n   -----------------------------------------\n");
    for(i=1; i<=n; i++){

        printf("     %d       %d         %d              %d         \n",
               s[i].cust_no,s[i].rd_ar,s[i].intr_arr_time,s[i].arr_time);
    if(i!=n){
    printf("   --------------------------------------------------------\n");
        }
    else{
        printf("   -----------------------------------------------------\n");
        }
    }

}

void schedule_arrival_time (Simulation s[],int n){
    int i;
    for( i=2; i<=n; i++){
        s[i].arr_time=s[i-1].arr_time+s[i].intr_arr_time;
    }
}
