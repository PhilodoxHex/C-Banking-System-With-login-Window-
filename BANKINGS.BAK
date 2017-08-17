//*****************************************************//
//           HEADER FILES USED IN THE PROGRAM          //
//*****************************************************//

#include<iostream.h>
#include<conio.h>
#include<process.h>         // for exit(0) //
#include<dos.h>             // for delay //
#include<iomanip.h>         // for setprecision //
#include<stdio.h>	  // for gets //
#include<stdlib.h>
#include<string.h>        // for strcpy //
#include<ctype.h>
#include<time.h>
#include<fstream.h>

//*****************************************************//
//                 HEADER FILES END HERE               //
//*****************************************************//

//*****************************************************//
//          CLASSES USED IN THE WHOLE PROGRAM          //
//*****************************************************//
class MAIN{
   long int accno;
   char name[80];
   char type;
   long int amt;
   int pin;
   long int depamt,withamt;
       public:
   int sid;
   void createacc(void);
   void signin(void);
   void accaccessed(void);
   void balenq(void);
   void bank_network(void);
   void dismyinfo(void);
   void modinfo(void);
   void depam(void);
   void witham(void);
   long int getaccno()
   {
      return accno;
   }
   char *getname()
   {
      return name;
   }
   char gettype()
   {
      return type;
   }
   long int getamt()
   {
      return amt;
   }
   int getpin()
   {
      return pin;
   }
   MAIN()
   {
      sid=0;
   }
}m;
//*****************************************************//
//                 CLASSES END HERE                    //
//*****************************************************//

//*****************************************************//
//                   FILE FUNCTION                     //
//*****************************************************//

void write_file(void);
void search(void);
void delete_account(void);
void hide(void);
void unhide(void);

//*****************************************************//
//              FILE FUNCTION ENDS HERE                //
//*****************************************************//

void main()
{   begin:  //begin is the declaration of a new file for goto command
    clrscr ();
    int ch=0;
    do
    {
       clrscr();
       cout<<"                  "<<"*****************************************"<<"\n";
       cout<<"                  "<<"*****************************************"<<"\n";
       cout<<"                  "<<"**               WELCOME               **"<<"\n";
       cout<<"                  "<<"**                 TO                  **"<<"\n";
       cout<<"                  "<<"**       HERUMB BANK OF COMMERCE       **"<<"\n";
       cout<<"                  "<<"** \"EXPERIENCE NEW GENERATION BANKING\" **"<<"\n";
       cout<<"                  "<<"**                                     **"<<"\n";
       cout<<"                  "<<"*****************************************"<<"\n";
       cout<<"                  "<<"*****************************************"<<"\n";
       delay(300);
       cout<<"    "<<"1. CREATE AN ACCOUNT"<<"\n";
       delay(300);
       cout<<"    "<<"2. SIGN IN"<<"\n";
       delay(300);
       cout<<"    "<<"3. PEOPLE CONNECTED TO US"<<"\n";
       delay(300);
       cout<<"    "<<"4. EXIT"<<"\n";
       delay(300);
       cout<<"    "<<"ENTER YOUR CHOICE(1-4):";
       cin>>ch;
       if(ch==1)
       {
	  write_file();
       }
       else if(ch==2)
       {
	  m.signin();
       }
       else if(ch==3)
       {
	  m.bank_network();
       }
       else
       {
	  exit(0);
       }
    }while(ch>=1 && ch<=3);
    getch();
}

void MAIN::createacc()
{   clrscr();
    cout<<"                "<<"YOU ARE ONE STEP FAR TO BE A PART OF OUR NETWORK\n";
    delay(150);
    cout<<"\n";
    cout<<"-----------------------------NEW ACCOUNT ENTRY FORM-----------------------------";
    accno:
    cout<<"   "<<"Enter Your 5-digit Account No.: ";
    cin>>accno;
    if(accno<10000 || accno>99999)
    {
	  cout<<"Account No. should be of 5 digits only.\n";
	  goto accno;
    }
    else if(accno>=10000 && accno<=99999)
    {

    }
    else
    {
	  cout<<"Invalid Account No. Please Try Again.....";
	  goto accno;
    }
    cout<<"\n";
    cout<<"   "<<"Enter Your Full Name: ";
    gets(name);
    cout<<"\n";
    acctype:
    cout<<"   "<<"C-Current\n";
    cout<<"   "<<"S-Saving\n";
    cout<<"   "<<"F-Fixed Deposit\n";
    cout<<"   "<<"Enter Account Type(C\\S\\F): ";
    cin>>type;
    cout<<"\n";
    if(type=='C' || type=='c')
    {  c:
       cout<<"   "<<"Enter Your Opening Amount(>=1000): ";
       cin>>amt;
       cout<<"\n";
       if(amt<1000)
       {    cout<<"Your least Starting Amount should be Rs.1000.";
	    goto c;
       }
    }

    else if(type=='S' || type=='s')
    {  s:
       cout<<"   "<<"Enter Your Opening Amount(>=500): ";
       cin>>amt;
       cout<<"\n";
       if(amt<500)
       {    cout<<"Your least Starting Amount should be Rs.500.";
	    goto s;
       }
    }

    else if(type=='F' || type=='f')
    {  f:
       cout<<"   "<<"Enter Your Opening Amount(>=10000): ";
       cin>>amt;
       cout<<"\n";
       if(amt<10000)
       {    cout<<"Your least Starting Amount should be Rs.10000.";
	    goto f;
       }
    }

    else
    {
       cout<<"   "<<"Please Enter Correct Choice!!!!!!!";
       delay(500);
       goto acctype;
    }
    cout<<"   "<<"Your ATM PIN is: ";
    srand(time(NULL));
    pin=rand()%9000+1000;
    cout<<pin;
    sid=0;
    cout<<"\n\n"<<"   "<<"THANKS FOR USING OUR SERVICES YOUR ACCOUNT IS CREATED SUCCESSFULLY..........";
    getch();
}

void write_file()
{
    ofstream fout;
    fout.open("account.dat",ios::out|ios::app|ios::binary);
    m.createacc();
    fout.write((char*)&m,sizeof(m));
    fout.close();
}

void MAIN::signin()
{   clrscr();
    int flag=0;
    char ch;
    long int accno1=0,pin1=0;
    ifstream fin;
    cout<<"                  "<<"HERUMB BANK OF COMMERCE ACCOUNT ACCESS FORM\n";
    cout<<"+------------------------------------------------------------------------------+";
    cout<<"   "<<"Enter Your Account Number:";
    cin>>accno1;
    cout<<"\n";
    cout<<"   "<<"Enter Your PIN:";
    cin>>pin1;
    fin.open("account.dat",ios::in|ios::binary);
    while(fin.read((char*)&m,sizeof(m)))
    {
       if(accno1==accno && pin1==pin)
       {   flag=1;
	   accaccessed();
       }

    }

    if (flag==0)
    {   forgot:
	cout<<"\n"<<"   "<<"Forgot Account Number/PIN(Y/N):";
	cin>>ch;
	if(ch=='Y' || ch=='y')
	{
	   bank_network();
	}

	else if(ch=='N' || ch=='n')
	{

	}

	else
	{
	   goto forgot;
	}
    }
    fin.close();
}

void MAIN::bank_network()
{   clrscr();
    ifstream fin;
    char ch, utype;
    cout<<"                             "<<"PEOPLE CONNECTED TO US"<<"\n";
    delay(150);
    cout<<"===============================================================================\n";
    cout<<"A/c no.                 NAME                 Type           Balance        PIN\n";
    cout<<"===============================================================================\n";
    fin.open("account.dat",ios::in|ios::binary);
    if(!fin)
       cout<<"   "<<"File doesn't exists";
    int i=5;
    while(fin.read((char*)&m,sizeof(m)))
    {
       if(sid==0)
       {
	  utype=toupper(type);
	  gotoxy(0,i);
	  cout<<accno;
	  gotoxy(20,i);
	  cout<<name;
	  gotoxy(47,i);
	  cout<<utype;
	  gotoxy(61,i);
	  cout<<amt;
	  gotoxy(76,i);
	  cout<<pin<<"\n";
	  i++;
       }
    }
    fin.close();
    getch();
    main();
}

void MAIN::accaccessed()
{   clrscr();
    signedin:
    int ch;
    cout<<"               "<<"HERUMB BANK OF COMMERCE WELCOMES ";
    cout<<name;
    delay(150);
    cout<<"\n\n";
    cout<<"   "<<"1. Deposit Amount\n\n";
    cout<<"   "<<"2. Withdraw Amount\n\n";
    cout<<"   "<<"3. Balance Enquiry\n\n";
    cout<<"   "<<"4. Display My Information\n\n";
    cout<<"   "<<"5. Modify Information\n\n";
    cout<<"   "<<"6. Search A Friend\n\n";
    cout<<"   "<<"7. Hide My Account\n\n";
    cout<<"   "<<"8. Unhide My Account\n\n";
    cout<<"   "<<"9. Close This Account\n\n";
    cout<<"   "<<"10. Signout\n\n";
    cout<<"   "<<"Enter Your Choice:";
    cin>>ch;
    switch(ch)
    {
	case 1: depam();
		break;
	case 2: witham();
		break;
	case 3: balenq();
		break;
	case 4: dismyinfo();
		break;
	case 5: modinfo();
		break;
	case 6: search();
		break;
	case 7: hide();
		break;
	case 8: unhide();
		break;
	case 9: delete_account();
		break;
	case 10: main();
		 break;
	default: cout<<"Please Enter Correct Choice.";
		 delay(300);
		 goto signedin;
    }
}

void MAIN::depam()
{   clrscr();
    char ch,found='f';
    int pin2;
    long pos;
    fstream fio("account.dat", ios::out | ios::in | ios::binary);
    cout<<"                            "<<"DEPOSIT AMOUNT SLIP\n";
    delay(150);
    cout<<"\n";
    forgot:
    cout<<"   "<<"Enter Your PIN: ";
    cin>>pin2;
    while(fio.read((char*)&m,sizeof(m)))
    {
       pos=fio.tellg();
       if(m.pin==pin2)
       {
	  cout<<"\n"<<"   "<<"Enter Deposit Amount: ";
	  cin>>depamt;
	  amt=amt+depamt;
	  fio.seekg(pos-sizeof(m));
	  fio.write((char*)&m,sizeof(m));
	  found='t';
	  fio.close();
	  break;
       }
    }

    if(found=='f')
    {
       cout<<"\n"<<"   "<<"Forgot Account Number/PIN(Y/N):";
	cin>>ch;
	if(ch=='Y' || ch=='y')
	{
	   dismyinfo();
	}

	else if(ch=='N' || ch=='n')
	{

	}

	else
	{
	   goto forgot;
	}
    }
    cout<<"\n";
    cout<<"   "<<"Your Transaction has been made Successfully.\n\n";
    choice:
    getch();
    accaccessed();
}

void MAIN::witham()
{   clrscr();
    char ch,found='f';
    int pin2;
    long pos;
    fstream fio("account.dat", ios::out | ios::in | ios::binary);
    overdraft:
    cout<<"                            "<<"WITHDRAW AMOUNT SLIP\n";
    delay(150);
    cout<<"\n";
    cout<<"   "<<"Enter Your PIN: ";
    cin>>pin2;
    while(fio.read((char*)&m,sizeof(m)))
    {
       pos=fio.tellg();
       if(m.pin==pin2)
       {
	  cout<<"\n"<<"   "<<"Enter Withdraw Amount: ";
	  cin>>withamt;
	  if(withamt<=amt)
	  {
	     cout<<"\n"<<"   "<<"Your Transaction has been made Successfully.\n";
	     amt=amt-withamt;
	  }
	  fio.seekg(pos-sizeof(m));
	  fio.write((char*)&m,sizeof(m));
	  found='t';
	  fio.close();
	  break;
       }
       else
       {
	  cout<<"   "<<"You are exceeding the limits of your balance for withdrawl.\n";
	  cout<<"   "<<"Your current balance is Rs."<<amt<<"\n";
	  cout<<"   "<<"Sorry for your Inconvinience, Please Try Again.";
	  getch();
	  clrscr();
	  goto overdraft;
       }
    }
    if(found=='f')
    {
       cout<<"\n"<<"   "<<"Forgot Account Number/PIN(Y/N):";
	cin>>ch;
	if(ch=='Y' || ch=='y')
	{
	   dismyinfo();
	}

	else if(ch=='N' || ch=='n')
	{

	}

	else
	{
	   goto overdraft;
	}
    }
    getch();
    accaccessed();
}

void MAIN::balenq()
{   clrscr();
    char ch;
    ifstream fin;
    cout<<"                            "<<"BALANCE ENQUIRY UNIT\n";
    delay(150);
    cout<<"\n";
    fin.open("account.dat", ios::in | ios::binary);
    cout<<"   "<<"Dear "<<name<<",\n\n";
    cout<<"   "<<"Account No.: "<<accno<<"\n\n";
    cout<<"   "<<"Your Present Balance amount is of Rs."<<amt<<"\n\n";
    getch();
    accaccessed();
}

void MAIN::dismyinfo()
{   clrscr();
    char ch;
    ifstream fin;
    fin.open("account.dat", ios::in | ios::binary);
    cout<<"                             "<<"ACCOUNT HOLDER DETAIL";
    delay(150);
    cout<<"\n\n";
    cout<<"   "<<"Account Number: "<<accno<<"\n\n";
    cout<<"   "<<"Name of Account Holder: "<<name<<"\n\n";
    if(type=='C' || type=='c')
    {
       cout<<"   "<<"Account Type: Current"<<"\n\n";
    }
    else if(type=='S' || type=='s')
    {
       cout<<"   "<<"Account Type: Saving"<<"\n\n";
    }
    else
    {
       cout<<"   "<<"Account Type: Fixed Deposit"<<"\n\n";
    }
    cout<<"   "<<"Balance: "<<amt<<"\n\n";
    cout<<"   "<<"PIN: "<<pin<<"\n\n";
    getch();
    accaccessed();
}

void MAIN::modinfo()
{   clrscr();
    char ch,newname[80];
    long pos;
    long int accno2;
    fstream fio("account.dat", ios::out | ios::in | ios::binary);
    cout<<"                            "<<"ACCOUNT MODIFY UNIT\n";
    delay(150);
    cout<<"\n";
    cout<<"   "<<"Confirm Account Number:";
    cin>>accno2;
    cout<<"\n";
    cout<<"   "<<"Name of Account Holder:";
    gets(newname);
    while(fio.read((char*)&m,sizeof(m)))
    {
       pos=fio.tellg();
       if(accno2==accno)
       {
	  strcpy(name,newname);
	  fio.seekg(pos-sizeof(m));
	  fio.write((char*)&m,sizeof(m));
	  fio.close();
	  break;
       }
    }
    cout<<"\n";
    cout<<"   "<<"Account Type:"<<type<<"\n\n";
    cout<<"   "<<"Balance:"<<amt<<"\n\n";
    cout<<"   "<<"Record Updated.";
    getch();
    accaccessed();
}

void search()
{   clrscr();
    ifstream fin;
    fin.open("account.dat", ios::in | ios::binary);
    long int accno2;
    int flag=0;
    cout<<"                                "<<"SEARCH A FRIEND\n";
    cout<<"   "<<"Enter the Account No. of The Person You want to Search: ";
    cin>>accno2;
    cout<<"\n";
    while(fin.read((char*)&m,sizeof(m)))
    {
       if(accno2==m.getaccno())
       {   flag=1;
	   cout<<"---------------------"<<"ACCOUNT HOLDER DETAILS"<<"---------------------\n";
	   cout<<"   "<<"Account Number: "<<m.getaccno()<<"\n";
	   cout<<"   "<<"Account Holder Details: "<<m.getname()<<"\n";
	   cout<<"   "<<"Account Type: "<<m.gettype()<<"\n";
	   cout<<"   "<<"Account Balance: "<<m.getamt()<<"\n";
       }
    }

    if(flag==0)
    {
       cout<<"   "<<"Please Enter Correct Account Number.";
       getch();
       m.accaccessed();
    }
    fin.close();
    getch();
    m.accaccessed();
}

void hide()
{
   clrscr();
   char ch,found='f';
   int pin3;
   long pos;
   fstream fio("account.dat", ios::out | ios::in | ios::binary);
   cout<<"                              "<<"HIDE ACCOUNT SLIP\n";
   delay(150);
   cout<<"\n";
   forgot:
   cout<<"   "<<"Enter Your PIN: ";
   cin>>pin3;
   while(fio.read((char*)&m,sizeof(m)))
   {
      pos=fio.tellg();
      if(m.getpin()==pin3)
      {
	 m.sid=1;
	 fio.seekg(pos-sizeof(m));
	 fio.write((char*)&m,sizeof(m));
	 found='t';
	 fio.close();
	 break;
      }
   }

   if(found=='f')
   {
      cout<<"\n"<<"   "<<"Forgot Account Number/PIN(Y/N):";
      cin>>ch;
      if(ch=='Y' || ch=='y')
      {
	 m.dismyinfo();
      }

      else if(ch=='N' || ch=='n')
      {

      }

      else
      {
	 goto forgot;
      }
   }
   cout<<"\n";
   cout<<"   "<<"Your Account has been Hided.\n\n";
   getch();
   m.accaccessed();
}

void unhide()
{
   clrscr();
   char ch,found='f';
   int pin3;
   long pos;
   fstream fio("account.dat", ios::out | ios::in | ios::binary);
   cout<<"                            "<<"UNHIDE ACCOUNT SLIP\n";
   delay(150);
   cout<<"\n";
   forgot:
   cout<<"   "<<"Enter Your PIN: ";
   cin>>pin3;
   while(fio.read((char*)&m,sizeof(m)))
   {
      pos=fio.tellg();
      if(m.getpin()==pin3)
      {
	 m.sid=0;
	 fio.seekg(pos-sizeof(m));
	 fio.write((char*)&m,sizeof(m));
	 found='t';
	 fio.close();
	 break;
      }
   }

   if(found=='f')
   {
      cout<<"\n"<<"   "<<"Forgot Account Number/PIN(Y/N):";
      cin>>ch;
      if(ch=='Y' || ch=='y')
      {
	 m.dismyinfo();
      }

      else if(ch=='N' || ch=='n')
      {

      }

      else
      {
	 goto forgot;
      }
   }
   cout<<"\n";
   cout<<"   "<<"Your Account has been Unhided.\n\n";
   getch();
   m.accaccessed();
}

void delete_account()
{  clrscr();
   long int accno2;
   cout<<"                              "<<"CLOSE THE ACCOUNT\n";
   ifstream fio("account.dat",ios::in);
   ofstream file("temp.dat", ios::out);
   char confirm, found='f';
   wrong:
   cout<<"   "<<"Please Confirm Your Account No.:";
   cin>>accno2;
   while(fio.read((char*)&m,sizeof(m)))
   {  if(m.getaccno()==accno2)
      {  found='t';
	 cout<<"\n"<<"   "<<"Are you sure you want to Close your Account(Y\\N)? ";
	 cin>>confirm;
	 if(confirm=='n')
	 {
	    file.write((char*)&m,sizeof(m));
	 }
      }
      else
	 file.write((char*)&m,sizeof(m));
   }
   if(found=='f')
   {
      cout<<"\n"<<"   "<<"Please Enter Correct Account No.";
      getch();
      goto wrong;
   }
   fio.close();
   file.close();
   remove("account.dat");
   rename("temp.dat","account.dat");
   cout<<"\n"<<"   "<<"THANK YOU FOR BEING A PART OF HBC WE WILL MISS YOU";
   getch();
   main();
}

