#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <conio.h>




struct details
{
    char name[10];
    int  aquan;
    float cp;
};

typedef struct details details;



struct dealers
{//56 bites
    int id;
    int car[6];
    float amount;
    float pcar[6];//
    int tqua;//total quantity
};
typedef struct dealers dealers;





void accept(int a)
{
    int c;
    do{
            printf("\nEnter The Amount correctly !! :\n");
            scanf("%d",&c);
            if(c==a)
            {
                printf("\nAmount entered sucessfully .........\n");
                printf("\n\n\t\t\t\t\tTHANK YOU FOR CHOOSING TATA MOTORS\n\n");
            }


    }while(c!=a);

}





//taking input of cars

int inputs(int a)
{   int du;

    do{
    printf(" Enter n.o of cars required : ");
    scanf("%d",&du);
    if(du>a)
    {
        printf("\n::::::Out of stock !! see the available cars(%d) and enter correctly :::::\n",a);
    }
    }while(du>a);

    return du;
}

//manager 1

void totalamount(dealers *baseaddress,int h)
{
    int i=0;float sum=0;
    for(i=0;i<h;i++)
    {
        sum+=(baseaddress+i)->amount;
    }

    printf("\n -> The total amount received by all customers is %.2f (in lakhs)\n",sum);


}


void main()
{
    //initialisation of car details
    details cars[6];

    strcpy(cars[0].name,"Nano");
    cars[0].aquan=200;
    cars[0].cp=2.5;

    strcpy(cars[1].name,"Altroz");
    cars[1].aquan=100;
    cars[1].cp=5.44;

    strcpy(cars[2].name,"Nexon");
    cars[2].aquan=250;
    cars[2].cp=7.0;

    strcpy(cars[3].name,"Harrier");
    cars[3].aquan=50;
    cars[3].cp=13.84;


    strcpy(cars[4].name,"NexonEV");
    cars[4].aquan=125;
    cars[4].cp=13.99;

    strcpy(cars[5].name,"TigorEv");
    cars[5].aquan=110;
    cars[5].cp=10.58;
    //done


    //calloc
    dealers *pd,*dd;
    int i=0,j;//initial 1 dealer
    int l=0;//for loop
    int ch;//choce for selecting cars
    int du;//dummy cars;
    int con;//to contiue shop
    float cost;
    int h=1;//
    int pj,lov;
    int close;
    int des;
    int password;
    int upassword=1234;
    int sid;
    int bals;
    int bal;
    int check ;

    int menu;//to retun to main menu
    pd=(dealers *)calloc(1,sizeof(dealers));
    dd=pd;
    if(pd==NULL)
    {

        printf("\n Out of space insert SD card \n");
    }



    do{


        do{
    //dealer or manager
    printf("\n\t\t\t\t\t  WELCOME TO TATA MOTORS\n");
    printf("\nEnter : \n1.For Dealer's Portal\n2.For Manager's poratal\n");
    printf("Enter :: ");
    scanf("%d",&check);
        }while(check!=1&&check!=2);


    if(check==1)
    {
          if(pd==NULL)
          {
              printf("\nOUT OF SPACE INSERT SD CARD....\n");
          }
          if(h>1)
          {
               pd=(dealers *)realloc(pd,h*sizeof(dealers));
             // printf("address of pd and dd %d %d ",(pd),(dd));
             dd->amount=0.0;
             dd->id=0;
             dd->pcar[0]=0.0;
             dd->pcar[1]=0.0;
             dd->pcar[2]=0.0;
             dd->pcar[3]=0.0;
             dd->pcar[4]=0.0;
             dd->pcar[5]=0.0;
             dd->car[0]=0.0;
             dd->car[1]=0.0;
             dd->car[2]=0.0;
             dd->car[3]=0.0;
             dd->car[4]=0.0;
             dd->car[5]=0.0;
             dd->tqua=0;
          }
       //welcome manager entering id
        printf("\n\t\t\t\t\t\tWelcome Dealer ! \n \n\n");
        printf("\nEnter your id : ");
        scanf("%d",&dd->id);


        //displaying car details
        do{
        do{
        printf("\n\n*************************************************************************************************************\n\n");
        printf("Name\t\t\tAVAILABLE QUANTITY\t\t\tCOST PER ITEM(in lakhs)\n");
        for(l=0;l<6;l++)
        {
            printf("%s\t\t\t%d\t\t\t\t\t%.3f\n",cars[l].name,cars[l].aquan,cars[l].cp);
        }
        printf("\n\n*************************************************************************************************************\n\n");

        //taking n.o of cars neededed

        printf("\nEnter 1 to purchase 'NANO' \n");
        printf("\nEnter 2 to purchase 'ALTOZ' \n");
        printf("\nEnter 3 to purchase 'NEXON' \n");
        printf("\nEnter 4 to purchase 'HARRIER' \n");
        printf("\nEnter 5 to purchase 'NEXONEV'\n");
        printf("\nEnter 6 to purchase 'TIGOREV' \n");
        printf("\nEnter :");
        scanf("%d",&ch);
        printf("\n\n*************************************************************************************************************\n\n");
        }while(ch!=1&&ch!=2&&ch!=3&&ch!=4&&ch!=5&&ch!=6);

        if(ch==1)
        {   printf("\t\t\t\t\t\TATA MOTORS \n");
            printf("\n Brand                     :NANO\n");
            printf(" Cost/1                    :%.3fLakhs\n",cars[0].cp);
            du=inputs(cars[0].aquan);
            dd->tqua+=du;
            dd->car[0]+=du;//increase the n.o nanos bouth after many puchases
            cars[0].aquan-=dd->car[0];//remaining cars
            cost=(cars[0].cp)*du;
            dd->amount+=cost;
            dd->pcar[0]+=cost;
            printf(" Cost of %d cars are       : %.2f Lakhs\n",du,cost);

 printf("\n\n*************************************************************************************************************\n\n");


        }


        else if(ch==2)
        {
            printf("\t\t\t\t\t\TATA MOTORS \n");
            printf("\n Brand                     :ALTROZ\n");
            printf(" Cost/1                    :%.3fLakhs\n",cars[1].cp);
            du=inputs(cars[1].aquan);
            dd->tqua+=du;
            dd->car[1]+=du;//increase the n.o nanos bouth after many puchases
            cars[1].aquan-=dd->car[1];//remaining cars
            cost=(cars[1].cp)*du;
            dd->amount+=cost;
            dd->pcar[1]+=cost;
            printf(" Cost of %d cars are        : %.2f Lakhs\n",du,cost);

 printf("\n\n*************************************************************************************************************\n\n");

        }



           else if(ch==3)
        {
            printf("\t\t\t\t\t\TATA MOTORS \n");
            printf("\n Brand                     :NEXON\n");
            printf(" Cost/1                    :%.3fLakhs\n",cars[2].cp);
            du=inputs(cars[2].aquan);
            dd->tqua+=du;
            dd->car[2]+=du;//increase the n.o nanos bouth after many puchases
            cars[2].aquan-=dd->car[2];//remaining cars
            cost=(cars[2].cp)*du;
            dd->amount+=cost;
            dd->pcar[2]+=cost;
            printf(" Cost of %d cars are        : %.2f Lakhs\n",du,cost);

 printf("\n\n*************************************************************************************************************\n\n");

        }



          else if(ch==4)
        {
            printf("\t\t\t\t\t\TATA MOTORS \n");
            printf("\n Brand                     :HARRIER\n");
            printf(" Cost/1                    :%.3fLakhs\n",cars[3].cp);
            du=inputs(cars[3].aquan);
            dd->tqua+=du;
            dd->car[3]+=du;//increase the n.o nanos bouth after many puchases
            cars[3].aquan-=dd->car[3];//remaining cars
            cost=(cars[3].cp)*du;
            dd->amount+=cost;
            dd->pcar[3]+=cost;
            printf(" Cost of %d cars are        : %.2f Lakhs\n",du,cost);

 printf("\n\n*************************************************************************************************************\n\n");

        }




           else if(ch==5)
        {
            printf("\t\t\t\t\t\TATA MOTORS \n");
            printf("\n Brand                     :NEXONEV\n");
            printf(" Cost/1                    :%.3fLakhs\n",cars[4].cp);
            du=inputs(cars[4].aquan);
            dd->tqua+=du;
            dd->car[4]+=du;//increase the n.o nanos bouth after many puchases
            cars[4].aquan-=dd->car[4];//remaining cars
            cost=(cars[4].cp)*du;
            dd->amount+=cost;
            dd->pcar[4]+=cost;
            printf(" Cost of %d cars are        : %.2f Lakhs\n",du,cost);

 printf("\n\n*************************************************************************************************************\n\n");

        }



            else if(ch==6)
        {
            printf("\t\t\t\t\t\TATA MOTORS \n");
            printf("\n Brand                     :TIGOREV\n");
            printf(" Cost/1                    :%.3fLakhs\n",cars[5].cp);
            du=inputs(cars[5].aquan);
            dd->tqua+=du;
            dd->car[5]+=du;//increase the n.o nanos bouth after many puchases
            cars[5].aquan-=dd->car[5];//remaining cars
            cost=(cars[5].cp)*du;
            dd->amount+=cost;
            dd->pcar[5]+=cost;

            printf(" Cost of %d cars are        : %.2f Lakhs\n",du,cost);

 printf("\n\n*************************************************************************************************************\n\n");

        }

        printf("\n\n \t\t\t Wannn ! continue shopping again ? press (1) or To exit any n.o >> ");
        scanf("%d",&con);
    }while(con==1);

    //now printing details
printf("\n\n*************************************************************************************************************\n\n");
      printf("\n\t\t\t\t\t\t\tGENARATING BILL:\n");
    printf("\n\nUser-id\t\t\t\t:%d\n\n",dd->id);
    printf(" Nano 's selected\t\t:%d |cost\t\t:%fLakhs\n",dd->car[0],dd->pcar[0]);
    printf(" Altoz's selected\t\t:%d |cost\t\t:%fLakhs\n",dd->car[1],dd->pcar[1]);
    printf(" Nexon 's selected\t\t:%d |cost\t\t:%fLakhs\n",dd->car[2],dd->pcar[2]);
    printf(" Harrier's selected\t\t:%d |cost\t\t:%fLakhs\n",dd->car[3],dd->pcar[3]);
    printf(" NexonEV's selected\t\t:%d |cost\t\t:%fLakhs\n",dd->car[4],dd->pcar[4]);
    printf(" TigorEV's selected\t\t:%d |cost\t\t:%fLakhs\n",dd->car[5],dd->pcar[5]);

    printf("\n Total Amount : %f (in Lakhs)\n",dd->amount*100000);

    //taking amount from user
    accept((dd->amount)*100000);//calling function


          h++;dd++;

    }





    //managers part
    else
    {
        printf("\n\t\t\t\t\tWELCOME MANAGER !\n");
        do{
        printf("\nEnter your password :\n");
        scanf("%d",&password);
        if(password!=upassword)
        {
            printf("\n\n!PASSWORD DOESN'T MATCH\n\n");
        }
        else
        {
            printf("\n\nSUCESSFULLY LOGGEDIN\n\n");
        }

        }while(password!=upassword);
        printf("\nPress (1) to close plant ... or any n.o to return to main menu\n");
        scanf("%d",&close);
        if(close==1)
        {
            do{
            printf("\n****************************************************************************************\n\n");
            printf("\nPress (1) To display total amount received today                  \n");
            printf("\nPress (2) To display the items purchased with quantity by dealers \n");
            printf("\nPress (3) To display the dealers id's who bought the highest and least quantity of each model  \n");
            printf("\nPress (4) To display remaining quantities of  each car            \n");
            printf("\nPress (5) To display  details all dealers with purchased quantities    \n");
            printf("\nPress (6) To EXIT\n");
            printf("\n****************************************************************************************\n\n");
            printf("Enter :");
            scanf("%d",&des);
            printf("\n****************************************************************************************\n\n");
            if(des==1)
            {
                   totalamount(pd,h);//call by reference
                   printf("\n\n\n\n\n\n");
            }
            else if(des==2)
            {    do{
                printf("\n  The available user id's are :-\n");

                for(i=0;i<h-1;i++)
                {
                    printf("\n\nUser-id\t\t\t\t:%d\n\n",(pd+i)->id);
                }
                printf("\nEnter id :");
                scanf("%d",&sid);
                for(i=0;i<h-1;i++)
                {   if(sid==(pd+i)->id){
                    printf("\n\nUser-id\t\t\t\t:%d\n\n",(pd+i)->id);
                    printf("Nano 's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[0],(pd+i)->pcar[0]);
                    printf("Altoz's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[1],(pd+i)->pcar[1]);
                    printf("Nexon 's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[2],(pd+i)->pcar[2]);
                    printf("Harrier's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[3],(pd+i)->pcar[3]);
                    printf("NexonEV's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[4],(pd+i)->pcar[4]);
                    printf("TigorEV's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[5],(pd+i)->pcar[5]);

                    printf("\n\nTotal quantity is : %d\n",(pd+i)->tqua);
                    bal=1;break;
                }
                else
                {
                    bal=0;
                }
                }
                if(bal==0){
                    printf("\nError (id) : %d doesn't exist ..\n",sid);
                }



            printf("\nDo you wann check again press(1) or else any n.o to go back\n");
            scanf("%d",&bals);

            }while(bals==1);

            }

            else if(des==3)
            {   int small,large,id1,id2;


               /* for(i=0;i<h-1;i++)
                {
                     if(i<h-2){
                    if( ((pd+i)->tqua) < ((pd+i+1)->tqua ))
                    {
                        small=(pd+i)->tqua;
                        id1=(pd+i)->id;
                    }
                    else
                    {
                        small=(pd+i+1)->tqua;
                         id1=(pd+i+1)->id;
                    }
                    if( ((pd+i)->tqua) > ((pd+i+1)->tqua ))
                    {
                        large=(pd+i)->tqua;
                         id2=(pd+i)->id;

                    }
                    else
                    {
                        large=(pd+i+1)->amount;
                        id2=(pd+i+1)->id;
                    }

                }}*/

                /*
                     id1=(pd+0)->id;
                     id2=(pd+0)->id;
                for(i=1;i<h-1;i++)
                {
                    if(small<(pd+i)->tqua){}
                    else
                    {
                        small=(pd+i)->tqua;
                        id1=(pd+i)->id;
                    }

                    if(large>(pd+i)->tqua){}
                    else {
                        large=(pd+i)->tqua;
                        id2=(pd+i)->id;
                    }

                }


                printf("\n\nThe customer who bought highest quantity(%d) id   :%d\n",large,id2);
                printf("\nThe customer who bought lowest quantity (%d)id      :%d\n",small,id1);
                */
                for(j=0;j<6;j++)
                {





                       small=0,large=0,id1=0,id2=0,lov=0;


                for(i=0;i<h-1;i++)
                {
                      if((pd+i)->car[j]!=0)
                {

                    small=(pd+i)->car[j],id1=(pd+i)->id;
                    if(small<(pd+i)->car[j]){}
                    else{
                        small=(pd+i)->car[j];
                        id1=(pd+i)->id;
                    }

                   if(large>(pd+i)->car[j]){}
                    else{
                        large=(pd+i)->car[j];
                        id2=(pd+i)->id;
                    }
                }


                }




                    if(j==0){
                    printf("\n The dealer id who bought the nano cars of highest quantity(%d) is %d and  dealer id of lowest quantity(%d) is  %d \n",large,id2,small,id1);
                    }
                    else if(j==1){
                    printf("\n The dealer id who bought the Altroz cars of highest quantity(%d) is %d and  dealer id of lowest quantity(%d) is  %d\n",large,id2,small,id1);
                    }

                    else if(j==2){
                    printf("\n The dealer id who bought the Nexon cars of highest quantity(%d) is %d and  dealer id of lowest quantity(%d) is  %d\n",large,id2,small,id1);
                    }

                    else if(j==3){
                    printf("\n The dealer id who bought the Harrier cars of highest quantity(%d) is %d and  dealer id of lowest quantity(%d) is  %d\n",large,id2,small,id1);
                    }

                    else if(j==4){
                    printf("\n The dealer id who bought the NexonEV cars of highest quantity(%d) is %d and  dealer id of lowest quantity(%d) is  %d\n",large,id2,small,id1);
                    }

                    else if(j==5){
                    printf("\n The dealer id who bought the TigorEV cars of highest quantity(%d) is %d and  dealer id of lowest quantity(%d) is  %d\n",large,id2,small,id1);
                    }
                }


                }




            else if(des==4)
            {
                   printf("\n\n*************************************************************************************************************\n\n");
        printf("Name\t\t\tREMAINING  QUANTITY\t\t\t)\n");
        for(i=0;i<6;i++)
        {
            printf("%s\t\t\t%d\t\t\t\t\t\n",cars[i].name,cars[i].aquan);
        }
        printf("\n\n*************************************************************************************************************\n\n");

            }

            else if(des==5)
            {
                for(i=0;i<h-1;i++)
                {
                    printf("\n\nUser-id\t\t\t\t:%d\n\n",(pd+i)->id);
                    printf("Nano 's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[0],(pd+i)->pcar[0]);
                    printf("Altoz's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[1],(pd+i)->pcar[1]);
                    printf("Nexon 's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[2],(pd+i)->pcar[2]);
                    printf("Harrier's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[3],(pd+i)->pcar[3]);
                    printf("NexonEV's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[4],(pd+i)->pcar[4]);
                    printf("TigorEV's selected\t\t:%d |cost\t\t:%fLakhs\n",(pd+i)->car[5],(pd+i)->pcar[5]);

                    printf("\n\nTotal quantity is : %d\n",(pd+i)->tqua);

                }


            }

            }while(des!=6);












        }


    }



    }while(1);



}
