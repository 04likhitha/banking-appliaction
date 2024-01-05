#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#define max 20
int index1;
struct bank{
    int acno;
    char name[30];
    int balance;
};
struct bank b[max];
void deposit(int d){
    b[index1].balance=b[index1].balance+d;
}
void withdrawal(int w){
    if(b[index1].balance<w){
        printf("\nInsufficient Balance");
    }
    else{
    b[index1].balance=b[index1].balance-w;
    }
}
void checkbalance(){
    printf("%d\n",b[index1].balance);
}
void search(int a,char s[]){
    int hkey=a%max,i;
    for(i=0;i<max;i++){
        index1=(hkey+i)%max;
        if(b[index1].acno==a){
            printf("welcome %s\n",s);
            printf("Your account no.:%d\n",a);
            break;
        }
        else{
            printf("creating an account\n");
            creatacc(a,s);
            printf("welcome %s\n",s);
            printf("Your account no.:%d\n",a);
            break;
        }
    }
    if(i==max){
        printf("\n Record can't be inserted");
    }
}
void creatacc(int a,char s[]){
    int hkey=a%max,ba,i;
    for(i=0;i<max;i++){
        index1=(hkey+i)%max;
        if(b[index1].acno==0){
            b[index1].acno=a;
            strcpy(b[index1].name,s);
            printf("Enter amt to add:");
            scanf("%d",&ba);
            b[index1].balance=ba;
            break;
        }
    }
}

void main(){
    int acno,ch,d,w,i,j,ac,n;
    char s[100];
    char na[100];
    for(i=0;i<max;i++){
        b[i].acno=0;
    }
    printf("no.of accounts:");
    scanf("%d",&n);
    for(j=0;j<n;j++){
        printf("Enter name:");
        scanf("%s",na);
        printf("Enter account no.:");
        scanf("%d",&ac);
        creatacc(ac,na);
    }
    printf("Customer");
    printf("\n");
    printf("enter account no.");
    scanf("%d",&acno);
    printf("enter name:");
    scanf("%s",s);
    search(acno,s);
    while(1){
        printf("Bank Opeartions");
        printf("\n1.Check Balance");
        printf("\n2.Deposit");
        printf("\n3.Withdrawal");
        printf("\n4.Exit");
        printf("\nEnter ur choice");
        scanf("%d",&ch);
        switch(ch){
            case 1:
                  checkbalance();
                  break;
            case 2:
                  printf("Enter deposit amt");
                  scanf("%d",&d);
                  deposit(d);
                  break;
            case 3:
                  printf("Enter withdrawal amt");
                  scanf("%d",&w);
                  withdrawal(w);
                  break;
            case 4:
                  exit(0);
                  break;
            default:
                   printf("\nWrong choice");
        }
        
    }
    
}
