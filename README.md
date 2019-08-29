//121810308022
#include <iostream>
using namespace std;
int n;
class candidate{
	public:
		string name;
		int vote;
};

void outputElection(candidate* arr){
	int total_vote=0;
	for(int i=0;i<n;i++)
	{
		total_vote=total_vote+arr[i].vote; 
	}

	cout<<"result of the election......"<<endl;
	cout<<"name of candidate"<<"\t"<<"vote received"<<"\t"<<"percentage"<<endl;
	for(int i=0;i<n;i++){
		cout<<arr[i].name<<"\t\t\t";
		cout<<arr[i].vote<<"\t\t";
		cout<<(arr[i].vote*100)/total_vote<<"%"<<endl;
	}

	int max=INT_MIN,count=0;
	int index[10]={0};

	for(int i=0;i<n;i++){
		if(arr[i].vote>max){
			max=arr[i].vote;
		}
	}
	
	for(int i=0;i<n;i++){
		if(arr[i].vote==max){
			index[count]=i;
			count++;
		}
	}
	
	if(count==1)
		cout<<"The winner is "<<arr[index[count-1]].name<<endl;
	else{
		cout<<"There is tie between:"<<endl;
		for(int i=0;i<count-1;i++)
			cout<<arr[index[i]].name<<", ";
		cout<<arr[index[count-1]].name<<endl;
		cout<<"all are winner\n";
	}
	return ;
}

int main(){ 
	string s;
	int v;
	candidate arr[100];
	cout<<"enter total no.of candidates:";
	cin>>n;
	cout<<"enter candidates last name, there are "<<n<<"\tcandidates:-\n";
	for(int i=0;i<n;i++){
		cout<<"enter candidate "<<i+1<<" last name\n";
		cin>>s;
		arr[i].name=s;
		cout<<"enter no of votes received by candidate "<<i<<endl;
		cin>>v;
		arr[i].vote=v;
	}
	outputElection(arr);
	return 0;}
