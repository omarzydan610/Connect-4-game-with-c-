#include<iostream>
using namespace std;
#define rows 6
#define cols 7

char arr[rows][cols]={{' ',' ',' ',' ',' ',' ',' '},
                      {' ',' ',' ',' ',' ',' ',' '},
                      {' ',' ',' ',' ',' ',' ',' '},
                      {' ',' ',' ',' ',' ',' ',' '},
                      {' ',' ',' ',' ',' ',' ',' '},
                      {' ',' ',' ',' ',' ',' ',' '}};
int mode=0,counter=0,winner=0;
string name1,name2,name3;
bool ans=false;

void modeSelection(){
  cout<<"========= WELCOME TO CONNECT 4 GAME =========\n";
  cout<<"Mods:\n";
  cout<<"1- 1 vs 1\n";
  cout<<"2- 1 vs computer\n";
  cout<<"Enter the number of mode you want to play : ";
  cin>>mode;
  cout<<endl;
}

void win1(){
  for(int i=0;i<rows;i++){
    for(int j=0;j<4;j++){
      if(arr[i][j]=='X' and arr[i][j+1]=='X' and arr[i][j+2]=='X' and arr[i][j+3]=='X'){
        winner=1;
        ans= true;
        return;
      }
      else if(arr[i][j]=='0' and arr[i][j+1]=='0' and arr[i][j+2]=='0' and arr[i][j+3]=='0'){
        winner=2;
        ans= true;
        return;
      }
    }
  }
  for(int i=0;i<3;i++){
    for(int j=0;j<cols;j++){
      if(arr[i][j]=='X' and arr[i+1][j]=='X' and arr[i+2][j]=='X' and arr[i+3][j]=='X'){
        winner=1;
        ans= true;
        return;
      }
      else if(arr[i][j]=='0' and arr[i+1][j]=='0' and arr[i+2][j]=='0' and arr[i+3][j]=='0'){
        winner=2;
        ans= true;
        return;
      }
    }
  }
  for(int i=5;i>=3;i--){
    for(int j=0;j<4;j++){
      if(arr[i][j]=='X' and arr[i-1][j+1]=='X' and arr[i-2][j+2]=='X' and arr[i-3][j+3]=='X'){
        winner=1;
        ans= true;
        return;
      }
      else if(arr[i][j]=='0' and arr[i-1][j+1]=='0' and arr[i-2][j+2]=='0' and arr[i-3][j+3]=='0'){
        winner=2;
        ans= true;
        return;
      }
    }
  }
  for(int i=0;i<3;i++){
    for(int j=0;j<=3;j++){
      if(arr[i][j]=='X' and arr[i+1][j+1]=='X' and arr[i+2][j+2]=='X' and arr[i+3][j+3]=='X'){
        winner=1;
        ans= true;
        return;
      }
      else if(arr[i][j]=='0' and arr[i+1][j+1]=='0' and arr[i+2][j+2]=='0' and arr[i+3][j+3]=='0'){
        winner=2;
        ans= true;
        return;
      }
    }
  }
  if(counter==42){
    cout<<"        --==🤦‍♂️\b🤦‍♂️\b DRAW 🤦‍♂️\b🤦‍♂️\b==--\n";
    ans= true;
    return;
  }
}

void win2(){
  for(int i=0;i<rows;i++){
    for(int j=0;j<4;j++){
      if(arr[i][j]=='X' and arr[i][j+1]=='X' and arr[i][j+2]=='X' and arr[i][j+3]=='X'){
        winner=3;
        ans= true;
        return;
      }
      else if(arr[i][j]=='0' and arr[i][j+1]=='0' and arr[i][j+2]=='0' and arr[i][j+3]=='0'){
        winner=4;
        ans= true;
        return;
      }
    }
  }
  for(int i=0;i<3;i++){
    for(int j=0;j<cols;j++){
      if(arr[i][j]=='X' and arr[i+1][j]=='X' and arr[i+2][j]=='X' and arr[i+3][j]=='X'){
        winner=3;
        ans= true;
        return;
      }
      else if(arr[i][j]=='0' and arr[i+1][j]=='0' and arr[i+2][j]=='0' and arr[i+3][j]=='0'){
        winner=4;
        ans= true;
        return;
      }
    }
  }
  for(int i=5;i>=3;i--){
    for(int j=0;j<4;j++){
      if(arr[i][j]=='X' and arr[i-1][j+1]=='X' and arr[i-2][j+2]=='X' and arr[i-3][j+3]=='X'){
        winner=3;
        ans= true;
        return;
      }
      else if(arr[i][j]=='0' and arr[i-1][j+1]=='0' and arr[i-2][j+2]=='0' and arr[i-3][j+3]=='0'){
        winner=4;
        ans= true;
        return;
      }
    }
  }
  for(int i=0;i<3;i++){
    for(int j=0;j<=3;j++){
      if(arr[i][j]=='X' and arr[i+1][j+1]=='X' and arr[i+2][j+2]=='X' and arr[i+3][j+3]=='X'){
        winner=3;
        ans= true;
        return;
      }
      else if(arr[i][j]=='0' and arr[i+1][j+1]=='0' and arr[i+2][j+2]=='0' and arr[i+3][j+3]=='0'){
        winner=4;
        ans= true;
        return;
      }
    }
  }
  if(counter==42){
    cout<<"--==DRAW==--\n";
    ans= true;
    return;
  }
}

void print(){
  cout<<"\n  1   2   3   4   5   6   7\n";
  for(int i=0;i<29;i++){
    cout<<'-';
  }
  cout<<endl;
  for(int i=0;i<rows;i++){
    for(int j=0;j<cols;j++){
      if(j==0){
        cout<<"| ";
      }
      if(j>=0 and j<6){
        cout<<arr[i][j]<<" | ";
      }
      else{
        cout<<arr[i][j]<<" ";
        cout<<"|";
      }
    }
    cout<<endl;
  }
  for(int i=0;i<29;i++){
    cout<<'-';
  }
  cout<<endl<<endl;
}

void print_winner(){
  if(winner==1){
    cout<<"🎉🎉🎉 "<<name1<<" won 🎉🎉🎉\n";
  }
  else if(winner==2){
    cout<<"🎉🎉🎉 "<<name2<<" won 🎉🎉🎉\n";
  }
  else if(winner==3){
    cout<<"🎉🎉🎉 Computer won 🎉🎉🎉\n";
  }
  else if(winner==4){
    cout<<"🎉🎉🎉 You won 🎉🎉🎉\n";
  }
  else{
    return;
  }
}

int main(){
  int n,m=0,b=1,id=0,sym,z,playerNum,
  count1=-1,
  count2=-1,
  count3=-1,
  count4=-1,
  count5=-1,
  count6=-1,
  count7=-1;
  modeSelection();

  if(mode==1){
    cout<<"Enter the first player name\n";
    cin>>name1;
    cout<<"Enter the second player name\n";
    cin>>name2;
    print();
    while(ans==false){
      if(id%2==0){
        sym='X';
        playerNum=1;
        cout<<"          It's "<<name1<<" turn\n";
        cout<<"Enter the column you want to drop in : ";
        cin>>n;
        cout<<endl;
      }
      else{
        sym='0';
        playerNum=2;
        cout<<"          It's "<<name2<<" turn\n";
        cout<<"Enter the column you want to drop in : ";
        cin>>n;
        cout<<endl;
      }

      if(!(n>0 and n<8)){
        cout<<"Enter a number between 1 and 7\n\n";
        cout<<endl;
        continue;
      }
      counter++;

      if(n==1){
        count1++;
        if(count1==6){
          count1--;
          counter--;
          cout<<"THIS COLUMN IS  allready FILLED\n\n";
          continue;
        }
        z=count1;
      }
      else if(n==2){
        count2++;
        if(count2==6){
          count2--;
          counter--;
          cout<<"THIS COLUMN IS  allready FILLED\n";
          continue;
        }
        z=count2;
      }
      else if(n==3){
        count3++;
        if(count3==6){
          count3--;
          counter--;
          cout<<"THIS COLUMN IS  allready FILLED\n\n";
          continue;
        }
        z=count3;
      }
      else if(n==4){
        count4++;
        if(count4==6){
          count4--;
          counter--;
          cout<<"THIS COLOMN IS  allready FILLED\n\n";
          continue;
        }
        z=count4;
      }
      else if(n==5){
        count5++;
        if(count5==6){
          count5--;
          counter--;
          cout<<"THIS COLUMN IS  allready FILLED\n\n";
          continue;
        }
        z=count5;
      }
      else if(n==6){
        count6++;
        if(count6==6){
          count6--;
          counter--;
          cout<<"THIS COLUMN IS  allready FILLED\n\n";
          continue;
        }
        z=count6;
      }
      else if(n==7){
        count7++;
        if(count7==6){
          count7--;
          counter--;
          cout<<"THIS COLUMN IS  allready FILLED\n\n";
          continue;
        }
        z=count7;
      }
      arr[5-z][n-1]=sym;
      id++;
      print();
      win1();
    }
  }

  else if(mode==2){
    cout<<"Enter your name\n";
    cin>>name3;
    while(ans==false){
      if(id%2==0){
        sym='X';
        cout<<"       It's computer turn\n";
        cout<<endl;
        counter++;
        if(b==1){
          count1++;
          if(count1==6){
            count1--;
            counter--;
            b++;
            continue;
          }
          z=count1;
        }
        else if(b==2){
          count2++;
          if(count2==6){
            count2--;
            counter--;
            b++;
            continue;
          }
          z=count2;
        }
        else if(b==3){
          count3++;
          if(count3==6){
            count3--;
            counter--;
            b++;
            continue;
          }
          z=count3;
        }
        else if(b==4){
          count4++;
          if(count4==6){
            count4--;
            counter--;
            b++;
            continue;
          }
          z=count4;
        }
        else if(b==5){
          count5++;
          if(count5==6){
            count5--;
            counter--;
            b++;
            continue;
          }
          z=count5;
        }
        else if(b==6){
          count6++;
          if(count6==6){
            count6--;
            counter--;
            b++;
            continue;
          }
          z=count6;
        }
        else if(b==7){
          count7++;
          if(count7==6){
            count7--;
            counter--;
            b++;
            continue;
          }
          z=count7;
        }
        arr[5-z][b-1]=sym;
        b+=3;
        if(b>7){
          b=1;
        }
      }

      else{
        sym='0';
        cout<<"       It's your turn\n";
        cout<<"Enter the column you want to drop in : ";
        cin>>n;
        cout<<endl;
        if(!(n>0 and n<8)){
          cout<<"Enter a number between 1 and 7\n\n";
          cout<<endl;
          continue;
        }
        counter++;
        if(n==1){
          count1++;
          if(count1==6){
            count1--;
            counter--;
            cout<<"THIS COLUMN IS  allready FILLED\n\n";
            continue;
          }
          z=count1;
        }
        else if(n==2){
          count2++;
          if(count2==6){
            count2--;
            counter--;
            cout<<"THIS COLUMN IS  allready FILLED\n";
            continue;
          }
          z=count2;
        }
        else if(n==3){
          count3++;
          if(count3==6){
            count3--;
            counter--;
            cout<<"THIS COLUMN IS  allready FILLED\n\n";
            continue;
          }
          z=count3;
        }
        else if(n==4){
          count4++;
          if(count4==6){
            count4--;
            counter--;
            cout<<"THIS COLOMN IS  allready FILLED\n\n";
            continue;
          }
          z=count4;
        }
        else if(n==5){
          count5++;
          if(count5==6){
            count5--;
            counter--;
            cout<<"THIS COLUMN IS  allready FILLED\n\n";
            continue;
          }
          z=count5;
        }
        else if(n==6){
          count6++;
          if(count6==6){
            count6--;
            counter--;
            cout<<"THIS COLUMN IS  allready FILLED\n\n";
            continue;
          }
          z=count6;
        }
        else if(n==7){
          count7++;
          if(count7==6){
            count7--;
            counter--;
            cout<<"THIS COLUMN IS  allready FILLED\n\n";
            continue;
          }
          z=count7;
        }
        arr[5-z][n-1]=sym;
      }
      id++;
      print();
      win2();
    }
  }
  print_winner();
}
