# Killer-Sudoku
CS101 Project- C++
#include<iostream>

using namespace std;



struct coord{

    int x,y;

};

struct cage{

    coord c[81];

};



bool IsSum(int a[9][9],int i,int j,cage*r,int*p,int n, int*q){

    int o=-1; bool found=false;

    for(int m=0;m<n;m++){

        for(int k=0; k<*(p+m);k++){

            if(i==(r+m)->c[k].x && j==(r+m)->c[k].y){

                o=m;

                found=true;

                break;

            }

        }

        if(found) break;

    }

    if(*(p+o)==2){

        for(int t=0;t<8;t++){

            if(*(q+o)==(11+t)){

                if(a[i][j]<(t+2)) return 0;

            }

        }

    }

    if(*(p+o)==3){

        for(int t=0;t<8;t++){

            if(*(q+o)==(20+t)){

                if(a[i][j]<(t+2)) return 0;

            }

        }

    }

    if(a[i][j]>*(q+o))return 0;

    else{

    int u=1;

    for(int h=0;h<*(p+o);h++)

    {

        if(a[((r+o)->c[h].x)][((r+o)->c[h].y)]==0){ u=0; break;}

    }

    if(u==0) return 1;

    else

    {int sum=0;

        for(int d=0;d<*(p+o);d++){

            sum+=a[(r+o)->c[d].x][(r+o)->c[d].y];}

        if(sum==*(q+o)) return 1;

        else return 0;

    }

        

    }

}





bool IsinCage(int a[9][9],int i, int j,cage*r,int*p,int n){

    int o=-1; bool found=false;

            /*for(int w=0;w<9;w++){

                for(int z=0;z<9;z++){

                    cout<<a[w][z]<<" ";

                }

                cout<<endl;

            }

            cout<<endl;*/

            if(i==8 && j==8){

                for(int w=0;w<9;w++){

                    for(int z=0;z<9;z++){

                        cout<<a[w][z]<<" ";

                    }

                    cout<<endl;

                }

                return true;

            }

            a[i][j]=0;

        }

    }

    return false;

}



int main(){


    int a[9][9]; int n;

    cin>>n;

    int numbers[n],sum[n]; cage b[n];

    

    for(int i=0;i<n;i++){

        cin>>numbers[i]>>sum[i];

        for(int j=0;j<numbers[i];j++){

            cin>>b[i].c[j].x>>b[i].c[j].y;

        }

    }

    

    for(int i=0;i<9;i++){

        for(int j=0;j<9;j++){a[i][j]=0;}

    }

    

    cage*r=b;int*p=numbers;int*q=sum;

    int i=0,j=0;

    solver(a,p,q,r,n,i,j);

    }
