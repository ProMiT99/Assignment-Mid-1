#include<bits/stdc++.h>
using namespace std;


int k=0,t_product=0;
int c_id[1000]={0};
int location[1000]={0};

class inventory
{
    int id;
    string p_name;
    string c_name;
    int p_price;
    int p_quantity;



public:
    void update();
    void get_value(int total_p);
    void product_name();
    void find_by_product_id( int targetid);

};

    void inventory::get_value(int total_p)
    {
        int f=0;
        while(f==0)
        {
        int f1=0;
        cout<<"product id: ";
        cin>>id;


            for(int i=0;i<total_p;i++)
            {
                if(c_id[i]==id)
                {
                    cout<<"This id is already in use."<<endl;
                    f1=1;
                    break;
                }
            }
            if(f1==0)
            {
                c_id[k]=id;
                k++;
                 f=1;
            }
        }
        cout<<"product name: ";
        cin>>p_name;
        cout<<"Product company name: ";
        cin>>c_name;
        cout<<"Product Price: ";
        cin>>p_price;
        cout<<"Quantity of product: ";
        cin>>p_quantity;
        cout<<endl;

    }

    void inventory :: update()
    {
        cout<<"Previous information"<<endl;
        cout<<endl<<"1) Product Price: "<<p_price<<endl;
        cout<<"2)Product Quantity: "<<p_quantity<<endl;
        cout<<"which one to update"<<endl<<"1.price"<<endl<<"2.Quantity"<<endl<<"3.Both"<<endl;
        int up;
        cin>>up;
        while(1)
        {
            if(up==1)
            {
                cout<<"Update price: ";
                cin>>p_price;
                break;
            }
            if(up==2)
            {
                cout<<endl<<"Update quantity: ";
                cin>>p_quantity;
                break;
            }

            if(up==3)
            {
                cout<<"Update price: ";
                cin>>p_price;
                cout<<endl<<"Update quantity: ";
                cin>>p_quantity;
                break;
            }
            else
            {
                cout<<"You press wrong button"<<endl;
            }
        }
    }
void inventory::product_name()
    {
        cout<<"Product name: "<<p_name<<"\t #Product id: "<<id<<endl;
    }

void inventory:: find_by_product_id( int targetid)
    {
        if(id==targetid)
        {
            cout<<endl<<"1) product id: "<<id;
            cout<<endl<<"2) product name: "<<p_name;
            cout<<endl<<"3) Product company name: "<<c_name;
            cout<<endl<<"4) Product Price: "<<p_price;
            cout<<endl<<"5) Product quantity: "<<p_quantity<<endl;
        }
    }
int main()
{
    int store=0,n,x,s=0;
     inventory arr[1000];
    do
    {
        cout<<"1.Input information for new products."<<endl<<"2.Product search"<<endl<<"3.Update product information"<<endl<<"4.Exit"<<endl;
        cout<<endl<<"Press to select: ";
        cin>>s;
    switch(s)
    {

case 1:
    cout<<"Enter the total number of product you want to in: ";
    cin>>n;
    t_product+=n;
    cout<<endl;



    for(int i=store;i<t_product;i++)
       {
           arr[i].get_value(n);
       }
       store=t_product;

        break;

    break;

case 2:
            if(k==0)
            {
                cout<<"No information of a product are stored here."<<endl<<endl;
            }
    else{
        cout<<"-----ALL product name & ID show in below.-----";
        for(int i=0;i<t_product;i++)
                arr[i].product_name();
        cout<<endl<<"Press 0 to EXIT.";
        int j=t_product;
        while(j--)
            {
                cout<<endl<<"Which no. product you want to with all information. Input product ID number: ";
                cin>>x;
                for(int i=0;i<t_product;i++)
                    arr[i].find_by_product_id(x);
                if(x==0)
                    break;
            }
    }
    break;

case 3:
        int get;
        cout<<"Showing previous product information"<<endl;
        for(int i=0;i<t_product;i++)
        {

            arr[i].product_name();
        }
        cout<<"input position: ";
        cin>>get;
        arr[get-1].update();


    break;
case 4:
            break;
default:
            cout<<"Invalid choice. Please try again"<<endl;
            break;

    }
        }while(s!=4);
}
