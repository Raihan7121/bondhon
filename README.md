#include <bits/stdc++.h>
using namespace std;
bool viewer=true;
string wantedgender;
string education();
string religion();
string dist();
string gender();
string nation();
string marit();
string hobby();
const int today_day=21,today_month=5,today_year=2023;
class day1{
    protected:
int day,month,year;
public:
    int bday(){return day;}
    int bmonth(){return month;}
    int byear(){return year;}
   void setday(int d,int m,int y)
   {
      day=d;
      month=m;
      year=y;
   }
   void getday()
   {
      cout<<"Birthday: "<<day<<'/'<<month<<'/'<<year<<endl;
    }

    };

class fullname{
    protected:
string fname,lname;
public:
    string gfname(){return fname;}
    string glname(){return lname;}
    void setname(string a,string b)
    {
        fname=a;
        lname=b;
    }
    void getname()
    {
        cout<<fname<<" "<<lname<<endl;
    }
    };
class fathername{
    protected:
string ffname,flname;
public:
    string gffname(){return ffname;}
    string gflname(){return flname;}
    void setfname(string a,string b)
    {
        ffname=a;
        flname=b;
    }
    void getfname()
    {
        cout<<"Father's Name : "<<ffname<<" "<<flname<<endl;
    }
    };
class mothername{
    protected:
string mfname,mlname;
public:
    string gmfname(){return mfname;}
    string gmlname(){return mlname;}
    void setmname(string a,string b)
    {
        mfname=a;
        mlname=b;
    }
    void getmname()
    {
        cout<<"Mother's Name : "<<mfname<<" "<<mlname<<endl;
    }
    };
class contactinfo{
protected:
long long phnmbr;
string email,fb_id;
public:
    long long gphnmbr(){return phnmbr;}
    string gemail(){return email;}
    string gfb_id(){return fb_id;}
    void setinfo(string s,string b,long long a=8801923163381)
    {
        phnmbr=a;
        email=s;
        fb_id=b;
    }
    void getinfo()
    {
        cout<<"contact number: +"<<phnmbr<<endl;
        cout<<"Email: "<<email<<endl;
        cout<<"Facebook Id: "<<fb_id<<endl;
    }
};
class address{
protected:
string district;
public:
    string gdistrict(){return district;}
    void setaddress(string s){
        district=s;
        }
    void getaddress(){
        cout<<"HomeTown: "<<district<<endl;
        }
    };
class heightweight{
protected:
    int feet,inch;
    float weight;
public:
    int gfeet(){return feet;}
    int ginch(){return inch;}
    float gweight(){return weight;}
    void setheightweight(int f,int i,float w)
    {
      feet=f ;inch=i;weight=w;
    }
    void getheightweight()
    {
        cout<<"Height: "<<feet<<" feet "<<inch<<" inch"<<endl;
        cout<<"Weight: "<<weight<<" kg"<<endl;
    }
};
class age{
protected:
int aday,amonth,ayear;
public:
   virtual void setage()=0;
   void getage()
   {
      cout<<"Age: "<<ayear<<" years "<<amonth<<" months "<<aday<<" days "<<endl;
    }
    void gage()
   {
      cout<<"you are "<<ayear<<" years "<<amonth<<" months "<<aday<<" days old."<<endl;
    }
    };
class person:public day1,public fullname,public fathername,public mothername,public contactinfo,public address,public heightweight,public age{
    protected:
string religion,nationality,gender,marital_status,hobby,educational_status;
public:
    string greligion(){return religion;}
    string gnationality(){return nationality;}
    string ggender(){return gender;}
    string gmarital_status(){return marital_status;}
    string ghobby(){return hobby;}
    string geducational_status(){return educational_status;}
    virtual void getshort(){}
    void setage()
   {
      aday=today_day-day+1;
      amonth=today_month-month;
      ayear=today_year-year;
      if(aday<=0){aday+=30;amonth--;}
      else if(aday>30){aday-=30;amonth++;}
      if(amonth<=0){amonth+=12;ayear--;}
      else if(amonth>12){amonth-=12;ayear++;}
   }
   void setperson(string a,string b,string c,string d="Single",string e="Islam",string f="Bangladeshi")
   {
     religion=e,nationality=f,gender=c,marital_status=d,hobby=a,educational_status=b;
   }
   void getperson()
   {
       cout<<"Religion: "<<religion<<endl;
       cout<<"Nationality: "<<nationality<<endl;
       cout<<"Gender: "<<gender<<endl;
       cout<<"Marital status: "<<marital_status<<endl;
       cout<<"Hobby: "<<hobby<<endl;
       cout<<"Educational status: "<<educational_status<<endl;
   }
   void getdetail()
   {
       cout<<"Name: ";
       getname();
       getfname();
       getmname();
       getday();
       getage();
       getheightweight();
       getperson();
       getaddress();
       getinfo();
   }
};
string getss(long long a)
{
    string s;
    while(a)
    {
        s.push_back(a%10+'0');
        a/=10;
    }
    reverse(s.begin(),s.end());
    return s;
}
class bondhonuser:public person{
    protected:
    string password;
    int id;

public:
    static int cnt;
    void setid(int i){id=i;}
    int getid(){return id;}
    void setpassword(string s){password=s;}
    void setpassword()
    {char c=id%10+'0';
      password=fname[0]+fname[1]+fname[2]+c;
    }
    void setinfo(string s,string b,long long a=0)
    {
        if(a)phnmbr=a;
        else phnmbr=8801923163381+id;
        email=s;
        fb_id=b;
    }
    bool isvalid(string s){
        if(s==password)return true;
        return false;
        }
    void getshort()
    {
        cout<<id<<' ';
        getname();

    }
    bool findperson(int a,int b)
    {
        if(ayear>=a&&ayear<=b&&gender==wantedgender)return true;
        return false;
    }
    bool findperson(string dis)
    {
        if(dis==district&&gender==wantedgender)return true;
        return false;
    }
    bool findperson(string edu,int a)
    {
        if(edu==educational_status&&gender==wantedgender)return true;
        return false;
    }
    bool findperson(string rel,char c)
    {
        if(rel==religion&&gender==wantedgender)return true;
        return false;
    }
void setbondhon(string a,string b,string c,string d,string e,string f,int dd,int mm,int yy,string g,int ft,int in,float wt,string h,string ed,string gn,string re)
{
    setid(cnt++);
    setname(a,b);
    setfname(c,d);
    setmname(e,f);
    setday(dd,mm,yy);
    setage();
    string s,s1;
    s=fname+lname+getss(id)+"@gmail.com";
    long long p=8801920771838+cnt%1000;
    s1="https://www.facebook.com/profile.php?id="+getss(p*4+5);
    setinfo(s,s1,p);
    setaddress(g);
    setheightweight(ft,in,wt);
    setperson(h,ed,gn,"single",re,"bangladeshi");
    password=fname+getss(id);
}
string get1stname(){return fname;}
friend istream& operator>>(istream &in,bondhonuser&);
friend ostream& operator<<(ostream &out,bondhonuser&);
};
int bondhonuser:: cnt=2007001;
bondhonuser visitor;
bondhonuser database[123];

void signin()
{int idn,cntt=0;string pass,id;
system("cls");
D:
    cout<<"enter your id: \n";
    cin>>idn;idn%=1000;
    if(idn>122){cout<<"invalid id!\n";goto D;}
    system("cls");
    cout<<"enter your password: \n";
    cin>>pass;
    system("cls");
    if(database[idn].isvalid(pass)){
     visitor=database[idn];
     cout<<"congress "<<visitor.gfname()<<' '<<visitor.glname()<<"!"<<endl;
     visitor.gage();
     viewer=false;
    }
        else{cntt++;
        if(cntt<4&&viewer){
            cout<<"invalid id password!!try again.\n";
            goto D;
        }
        else if(viewer){
            cout<<"you tried maximum times. thank you!\n";
        }}
}

istream& operator>>(istream &in,bondhonuser& visitor)
{
    visitor.setid(122);
    string s,g,gen="male";int a,b,c;long long ph;float w;
    system("cls");
    cout<<"enter your gender\n";
    gen=gender();
    system("cls");
    cout<<"enter your first name and last name\n";
    in>>s>>g;
    visitor.setname(s,g);
    system("cls");
    cout<<"enter your date of birth(dd/mm/yy)\n";
    in>>a>>b>>c;
    visitor.setday(a,b,c);
    visitor.setage();
    system("cls");
    cout<<"enter your father's first name and last name\n";
    in>>s>>g;
    visitor.setfname(s,g);
    system("cls");
    cout<<"enter your mother's first name and last name\n";
    in>>s>>g;
    visitor.setmname(s,g);
    system("cls");
    cout<<"enter your phone number\n";
    in>>ph;
    system("cls");
    cout<<"enter your email\n";
    in>>s;
    system("cls");
    cout<<"enter your facebook account\n";
    in>>g;
    visitor.setinfo(s,g,ph);
    system("cls");
    cout<<"enter your height(feet/inche)\n";
    in>>a>>b;
    system("cls");
    cout<<"enter your weight(kg)\n";
    in>>w;
    visitor.setheightweight(a,b,w);
    system("cls");
string r,n,m,h,e,dd;
    cout<<"enter your hometown\n";
    dd=dist();
    visitor.setaddress(dd);
    system("cls");
    cout<<"enter your religion\n";
    r=religion();
    system("cls");
    cout<<"enter your nationality\n";
    n=nation();
    system("cls");
    cout<<"enter your marital_status\n";
    m=marit();
    system("cls");
    cout<<"enter your hobby\n";
    h=hobby();
    system("cls");
    cout<<"enter your educational_status\n";
    e=education();
    visitor.setperson(h,e,gen,m,r,n);
    system("cls");
    cout<<"enter your password to set\n";
    in>>gen;
    visitor.setpassword(gen);
    database[122]=visitor;
    system("cls");
    cout<<"Hi!! ";visitor.getname();cout<<endl;
    return in;
}
 ostream& operator<<(ostream &out,bondhonuser& ob){
out<<"Id no: "<<ob.getid()<<endl;
        ob.getdetail();
        return out;
}
string marit()
{
D:    cout<<"1.single\n2.married\n3.divorced\n";
    int a;cin>>a;
    if(a==1)return "single";
    else if(a==2)return "married";
    else if(a==3)return "divorced";
    else{cout<<"invalid number!enter correct one\n";goto D;}
}
string gender()
{
  D:  cout<<"1.male\n2.female\n";
    int a;cin>>a;
    if(a==1)return "male";
    else if(a==2)return "female";
    else{cout<<"invalid number!enter correct one\n";goto D;}
}
string nation()
{
 D:   cout<<"1.bangladeshi\n2.indian\n3.pakisthani\n4.nepali\n5.chinese\n6.rasiyan\n";
    int a;cin>>a;
    if(a==1)return "bangladeshi";
    else if(a==2)return "indian";
    else if(a==3)return "pakisthani";
    else if(a==4)return "nepali";
    else if(a==5)return "chinese";
    else if(a==6)return "rasiyan";
    else{cout<<"invalid number!enter correct one\n";goto D;}
}
string hobby()
{
 D:   cout<<"1.gardening\n2.photography\n3.cooking\n4.fishing\n5.reading_book\n6.singing\n";
    int a;cin>>a;
    if(a==1)return "gardening";
    else if(a==2)return "photography";
    else if(a==3)return "cooking";
    else if(a==4)return "fishing";
    else if(a==5)return "reading_book";
    else if(a==6)return "singing";
    else{cout<<"invalid number!enter correct one\n";goto D;}
}
string religion()
{
  D:  cout<<" 1.islam\n 2.hindu\n 3.christan\n 4.buddha\n";
    int a;cin>>a;
    if(a==1)return "islam";
    else if(a==2)return "hindu";
    else if(a==3)return "christan";
    else if(a==4)return "buddha";
    else{cout<<"invalid number!enter correct one\n";goto D;}
}
string education()
{
D:    cout<<"1.psc\n2.jsc\n3.ssc\n4.hsc\n5.bsc\n6.msc\n";
    int a;cin>>a;
    if(a==1)return "psc";
    else if(a==2)return "jsc";
    else if(a==3)return "ssc";
    else if(a==4)return "hsc";
    else if(a==5)return "bsc";
    else if(a==6)return "msc";
    else{cout<<"invalid number!enter correct one\n";goto D;}
}
string dist()
{
 D:   cout<<"1.dhaka\n2.chittagong\n3.rajshahi\n4.sylhet\n5.comila\n6.khulna\n7.barisal\n";
    int a;cin>>a;
    if(a==1)return "dhaka";
    else if(a==2)return "chittagong";
    else if(a==3)return "rajshahi";
    else if(a==4)return "sylhet";
    else if(a==5)return "comila";
    else if(a==6)return "khulna";
    else if(a==7)return "barisal";
    else{cout<<"invalid number!enter correct one\n";goto D;}
}


void findcandidate()
{
    vector<int>v; int a,b,c;v.push_back(0);
    system("cls");
    cout<<"I'm looking for \n";
    wantedgender=gender();
 F:
    system("cls");
    cout<<"which method do you want to search\n ";
    cout<<"1.age \n 2.religion \n 3.educational status \n 4.district \n";
    cin>>a;
    if(a==1)
    {system("cls");
        cout<<"aged from __ to__\n";
        cin>>a>>b;
        for(int i=0;i<123;i++)
        {
            if(database[i].findperson(a,b))v.push_back(i);
        }
        system("cls");
    }
    else if(a==2)
    {system("cls");
        cout<<"which religion __\n";
        string s=religion();
        for(int i=0;i<123;i++)
        {
            if(database[i].findperson(s,'c'))v.push_back(i);
        }
        system("cls");
    }
    else if(a==3)
    {system("cls");
        cout<<"which educational status __\n";
        string s=education();
        for(int i=0;i<123;i++)
        {
            if(database[i].findperson(s,1))v.push_back(i);
        }
        system("cls");
    }
    else if(a==4)
    {system("cls");
        cout<<"which district __\n";
        string s=dist();
        for(int i=0;i<123;i++)
        {
            if(database[i].findperson(s))v.push_back(i);
        }
        system("cls");
    }
    if(viewer){
        cout<<"at first you need to login or singup\n1.login\n2.signup\n";
        cin>>b;
        if(b==1)signin();
        else if(b==2) cin>>visitor;
    }
    if(v.size()>1){
    cout<<"your search list\nsl no id no  name \n";
    for(int i=1;i<v.size();i++){
        cout<<i<<' ';
        person* p=dynamic_cast<person*>(&database[v[i]]);
        p->getshort();
    }
    while(1)
    {
      cout<<"\nenter sl no to see detail or\n0 to exit or\n1000 for again search\n";
   G:     cin>>a;
        if(a==0)break;
        else if(a==1000){v.clear();goto F;}
        else if(a>=v.size()){
                cout<<"\nwrong serial number enter correct one\n";
        goto G;
                }
       else{
          cout<<"\n\n"<<database[v[a]];
       }
    }
    }
    else cout<<"not found\n";
    system("cls");
    cout<<"thanks!! for using bondhon\n";

}
void setdata()
{
    database[1].setbondhon("peyal","saha","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","hindu");
    database[2].setbondhon("ebrahim","zain","Aryan","zain","Aishwarya","zain",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","islam");
    database[3].setbondhon("arghy","basak","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","hindu");
    database[4].setbondhon("polok","barman","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","hindu");
    database[5].setbondhon("raihan","hossain","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[6].setbondhon("abu","omayer","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","islam");
    database[7].setbondhon("sakibur","rahman","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","islam");
    database[8].setbondhon("riad","islam","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","islam");
    database[9].setbondhon("tamim","islam","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","male","islam");
    database[10].setbondhon("sifatul","islam","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[11].setbondhon("tashibul","islam","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","islam");
    database[12].setbondhon("byejid","hossain","Aryan","zain","Aishwarya","zain",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","islam");
    database[13].setbondhon("muhit","islam","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","islam");
    database[14].setbondhon("tanvir","hossain","Abir","khan","Suhana","akther",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","islam");
    database[15].setbondhon("shoab","ahamed","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[16].setbondhon("umar","faruk","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","islam");
    database[17].setbondhon("mahin","hossain","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","islam");
    database[18].setbondhon("shahria","rafi","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","islam");
    database[19].setbondhon("sujoy","sadhu","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","male","islam");
    database[20].setbondhon("ahsanul","hasib","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[21].setbondhon("amlan","sarkar","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","hindu");
    database[22].setbondhon("mansief","bhyan","Aryan","bhyan","Aishwarya","begum",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","islam");
    database[23].setbondhon("ariful","islam","Dev","das","Tisha","rahman",12,3,2001,"khulna",5,3,58,"singing","hsc","male","islam");
    database[24].setbondhon("fariha","sanzana","Abir","rahman","Suhana","islam",29,8,2002,"dhaka",4,8,48,"reading","hsc","female","islam");
    database[25].setbondhon("hasibul","hasan","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[26].setbondhon("abir","rahman","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","islam");
    database[27].setbondhon("mushfiqur","rahman","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","islam");
    database[28].setbondhon("mezbaur","rahman","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","islam");
    database[29].setbondhon("rahimeen","fatin","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,67,"fishing","hsc","male","islam");
    database[30].setbondhon("raufun","ahsan","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");


    database[31].setbondhon("sumaiya","khan","Arjun","khan","Riya","khan",12,2,2000,"khulna",5,6,60,"reading","hsc","female","islam");
    database[32].setbondhon("mosabbir","hossen","Aryan","hosen","Aishwarya","islam",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","islam");
    database[33].setbondhon("ahnaf","taseen","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","islam");
    database[34].setbondhon("sabekunnahar","naboni","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","female","islam");
    database[35].setbondhon("shrawosy","modak","Aditya","khan","Roshni","modak",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","female","hindu");
    database[36].setbondhon("sayma","mushsharat","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","female","islam");
    database[37].setbondhon("prova","rani","Rohan","rahman","Ananya","khan",24,2,2002,"chittagong",5,3,52,"gardening","hsc","female","hindu");
    database[38].setbondhon("naveed","lihazi","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","islam");
    database[39].setbondhon("meheru","zannat","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","female","islam");
    database[40].setbondhon("mahamudul","shawcha","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[41].setbondhon("nafiul","hasan","Arjun","hasan","Riya","akther",12,2,2000,"khulna",5,6,60,"reading","hsc","male","islam");
    database[42].setbondhon("sajib","biswas","Aryan","biswas","Aishwarya","biswas",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","hindu");
    database[43].setbondhon("musfiqur","safin","Dev","rahman","Tisha","khan",12,3,2001,"khulna",5,3,58,"singing","hsc","male","islam");
    database[44].setbondhon("asif","rahman","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","islam");
    database[45].setbondhon("babla","islam","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[46].setbondhon("kawsar","khan","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","islam");
    database[47].setbondhon("hemayetul","jami","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","islam");
    database[48].setbondhon("tanzir","turzo","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","islam");
    database[49].setbondhon("sadikuzzaman","abir","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","male","islam");
    database[50].setbondhon("arefin","nahid","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[51].setbondhon("arafath","hosen","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","islam");
    database[52].setbondhon("efty","hasan","Aryan","zain","Aishwarya","zain",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","islam");
    database[53].setbondhon("kazi tasrif","basak","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","islam");
    database[54].setbondhon("ahnaf","mahi","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","islam");
    database[55].setbondhon("abdullah","shafi","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[56].setbondhon("avishek","debnath","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","hindu");
    database[57].setbondhon("bornil","chowdhury","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","hindu");
    database[58].setbondhon("swagoto","brinto","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","hindu");
    database[59].setbondhon("asif","mahmud","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","male","islam");
    database[60].setbondhon("shahriar","rokon","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[61].setbondhon("sanzida","tithi","Arjun","islam","Riya","akther",12,2,2000,"khulna",5,6,60,"reading","hsc","female","islam");
    database[62].setbondhon("swapnil","kundu","Aryan","kundu","Aishwarya","kundu",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","hindu");
    database[63].setbondhon("dipesh","talukdar","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","hindu");
    database[64].setbondhon("farhan","miraz","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","islam");
    database[65].setbondhon("forhad","rony","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[66].setbondhon("anto","kumar","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","hindu");
    database[67].setbondhon("tamal","priyo","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","hindu");
    database[68].setbondhon("faysal","mahmud","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","islam");
    database[69].setbondhon("amit","kairy","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","male","hindu");
    database[70].setbondhon("saad","uddin","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[71].setbondhon("ekramul","apon","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","islam");
    database[72].setbondhon("hafsa","tazrian","Aryan","zain","Aishwarya","zain",24,2,2002,"dhaka",5,4,62,"gardening","hsc","female","hindu");
    database[73].setbondhon("loman","shuvo","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","islam");
    database[74].setbondhon("mofazzal","hosen","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","islam");
    database[75].setbondhon("nafis","ashik","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[76].setbondhon("azmain","mubassir","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","islam");
    database[77].setbondhon("tonmoy","kundy","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","hindu");
    database[78].setbondhon("tasfia","samiha","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","female","islam");
    database[79].setbondhon("bayzed","ahmed","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","male","islam");
    database[80].setbondhon("hafizur","rahman","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[81].setbondhon("tanjimul","hassan","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","islam");
    database[82].setbondhon("ashrarul","sifat","Aryan","zain","Aishwarya","zain",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","islam");
    database[83].setbondhon("amit","paul","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","hindu");
    database[84].setbondhon("sohel","khan","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","islam");
    database[85].setbondhon("sayaka","alam","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","female","islam");
    database[86].setbondhon("niloy","das","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"coding","hsc","male","hindu");
    database[87].setbondhon("shanzida","rahman","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","female","islam");
    database[88].setbondhon("mayesha","zaman","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","female","islam");
    database[89].setbondhon("farzana","rahman","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","female","islam");
    database[90].setbondhon("khalil","ullah","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[91].setbondhon("tahsinur","rahman","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","islam");
    database[92].setbondhon("aritra","likhan","Aryan","zain","Aishwarya","zain",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","islam");
    database[93].setbondhon("iqbal","mahamud","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","islam");
    database[94].setbondhon("anirban","ghosh","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","hindu");
    database[95].setbondhon("nafiul","islam","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[96].setbondhon("anirban","roy","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","hindu");
    database[97].setbondhon("ahanaf","rifat","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","islam");
    database[98].setbondhon("bisal","roy","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","hindu");
    database[99].setbondhon("arju","afrin","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","female","islam");
    database[100].setbondhon("tahmid","islam","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[101].setbondhon("choyan","barua","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","hindu");
    database[102].setbondhon("sumaiya","rahim","Aryan","zain","Aishwarya","zain",24,2,2002,"dhaka",5,4,62,"gardening","hsc","female","islam");
    database[103].setbondhon("faiyaz","mahmud","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","male","islam");
    database[104].setbondhon("atikur","rahman","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","islam");
    database[105].setbondhon("marufa","akter","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","female","islam");
    database[106].setbondhon("asif","akbar","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","male","islam");
    database[107].setbondhon("abid","hasan","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","islam");
    database[108].setbondhon("laboni","rahman","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","female","islam");
    database[109].setbondhon("sourav","debnath","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","male","hindu");
    database[110].setbondhon("shayka","islam","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","female","islam");

    database[111].setbondhon("plaban","das","Arjun","saha","Riya","saha",12,2,2000,"khulna",5,6,60,"reading","hsc","male","hindu");
    database[112].setbondhon("azhar","uddin","Aryan","zain","Aishwarya","zain",24,2,2002,"dhaka",5,4,62,"gardening","hsc","male","islam");
    database[113].setbondhon("maria","joli","Dev","basak","Tisha","saha",12,3,2001,"khulna",5,3,58,"singing","hsc","female","islam");
    database[114].setbondhon("ahmed","safa","Abir","barman","Suhana","barman",29,8,2002,"dhaka",5,7,66,"reading","hsc","male","islam");
    database[115].setbondhon("minhaz","mahadi","Aditya","islam","Roshni","begum",12,2,2002,"dhaka",5,6,60,"sleeping","hsc","male","islam");
    database[116].setbondhon("shaeer","swapnil","Joy","rahman","Diya","khatun",12,2,2000,"sylhet",5,6,60,"photography","hsc","female","hindu");
    database[117].setbondhon("tirtho","mondal","Rohan","rahman","Ananya","islam",24,2,2002,"chittagong",5,3,52,"gardening","hsc","male","hindu");
    database[118].setbondhon("mahir","azmain","Anik","hosen","Ishika","begum",12,3,2001,"khulna",5,8,61,"reading","hsc","male","islam");
    database[119].setbondhon("dipto","saha","Rahul","khan","Nisha","akther",29,8,2002,"rajshahi",5,7,57,"fishing","hsc","male","hindu");
    database[120].setbondhon("shible","sadik","Anirban","islam","Nandini","rahman",12,2,2002,"barisal",5,4,58,"cooking","hsc","male","islam");

    database[121].setbondhon("anik","ekka","Arjun","saha","Riya","saha",12,2,2000,"rajshahi",5,6,60,"reading","hsc","male","islam");
}
int rai() {
    setdata();

    //for(int i=1;i<12;i++)database[i].getdetail();
cout<<"welcome to bondhon!\n1.login\n2.signup\n3.find someone\n";
D:
int a;cin>>a;
if(a==1){signin();goto G;}
else if(a==2){cin>>visitor;goto G;}
else if(a==3)findcandidate();
else{cout<<"invalid number!enter correct one\n";goto D;}
  return 0;
  G:
      cout<<"enter__\n1.find someone\n2.exit\n";
      cin>>a;
      if(a==1)findcandidate();
      else if(a!=2){cout<<"invalid number!\n";goto G;}
  return 0;
}
void store()
{
    ofstream out("result.txt");
    {for(int i=1;i<123;i++){
        bondhonuser v=database[i];
     out<<v.getid()<<' '<<v.gfname()<<' '<<v.glname()<<' '<<v.gffname()<<' '<<v.gflname()<<' '<<v.gmfname()<<' '<<v.gmlname()<<' '<<v.bday()<<' '<<v.bmonth()<<' '<<v.byear()<<' ';
     out<<v.gfeet()<<' '<<v.ginch()<<' '<<v.gweight()<<' '<<v.greligion()<<' '<<v.gnationality()<<' '<<v.ggender()<<' ';
     out<<v.gmarital_status()<<' '<<v.ghobby()<<' '<<v.geducational_status()<<' '<<v.gdistrict()<<' ';
     out<<v.gphnmbr()<<' '<<v.gemail()<<' '<<v.gfb_id()<<endl;
    }
    }
    out.close();
    return;
}
int main()
{
    rai();
    store();
}

