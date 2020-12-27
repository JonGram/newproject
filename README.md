    //Find the Nth number after removing all 9 digit numbers
//Incomplete program
#include <iostream>
#include <vector>
#include <string>
using namespace std;
  
// Method to count nine digit numbers
int nineDigits(unsigned int pos, unsigned int len) {

    if (len - pos == 1) {
        return 0;

    }
    else if(len>pos) {
        double exp = len - pos;
        pos += 1;
        return 9 * nineDigits(pos, len) + (int)pow(exp, 10);
    }
    
}
// Method to return Nth number after removing all nine digits
int findNth(int N) {
    string str;
    int subtract = 0;
    str = to_string(N);
    int num = 0;

    for (unsigned int i = 0; i < str.length(); ++i) {
        if (str[i] == '9') {
            
             subtract += ((int)(str[i]) - 48) * nineDigits(i, str.length());
             for (int j = 0; j < str.length(); ++j) {
                 subtract += ((int)str[j] - 48) * (int)pow((double)j, 10);
             }
            
          
        }
        else if(str[i] != 0) {
            subtract += ((int)(str[i])-48)* nineDigits(i, str.length());
        }
        else if (str[i] == 0) {
            subtract += nineDigits(i, str.length());
        }
    }
    num = stoi(str) - subtract;
    return num;
}

//Main method
int main(){
    int choice = 0;
    unsigned int number;
    while(choice != 9){
       cout<<"Enter a positive number: "<<endl;
       cin>>number;
       cout<<findN(number)<<endl;
       cout<<"Enter choice"<<endl;
       cin>>choice;
    }
    return 0;
}
   
   
