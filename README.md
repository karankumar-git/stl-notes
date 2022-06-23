# stl-striver-notes
Best Notes to revise all the concepts of STL.
#include <bits/stdc++.h>
using namespace std;
int n;
vector<int> v;

/*-----Notes Start from here-----*/

void explainPair(){
	pair<int,int> p1 = {1,4};
	cout<<p1.first<<" "<<p1.second<<endl;

	pair<int,pair<int,int>> p2 = {1,{4,5}};
	cout<<p2.first<<" "<<p2.second.first<<" "<<p2.second.second<<endl;

	//also use as datatype of array
	pair<int,int> arr[] = {{1,3},{2,4},{4,5}};
	cout<<arr[1].first<<" "<<arr[2].second<<endl;
}

void explainVector(){
	vector<int> v;			//{}
	v = {10,20,30,40};
	v.push_back(1);			//{1}
	v.emplace_back(2);		//{1,2}

	vector<pair<int,int>> vp;
	vp.push_back({1,3});	//Must put braces 
	vp.emplace_back(1,2);	//automatically put braces 
	
	for(auto it : vp){
		cout<<it.first<<" "<<it.second<<endl;
	}

	//already filled vector
	vector<int> valready(10,100);	//{100,100,...10times }
	
	//copy vector in another vector
	vector<int> vcopy(valready);

	vector<int>::iterator it1 = vcopy.begin();	//consider it as a pointer
	vector<int>::iterator it2 = vcopy.end();	//it points to the next of last index
	//   10 20 30 40
	//   |           |
	//  begin       end

	//Get value with iterator
	cout<<*it1<<*(it1++)<<endl;

	// vector<int>::iterator it3 = vcopy.rend();	//reverse-end
	// vector<int>::iterator it4 = vcopy.rbegin(); //reverse-begin
	//     10 20 30 40
	//   |           |
	//   rend      rbegin      rbegin++ = 30

	cout<<v.front()<<" "<<v.back()<<endl;

	for(vector<int>::iterator it5 = v.begin(); it5!=v.end(); it5++){
		cout<<*it5<<" ";
	}
	cout<<endl;

	// auto helps to auto assign the datatype
	// auto it = v.begin();  auto assigns as iterator
	// auto s = "karan";     auto assigns as string

	for(auto it5 = v.begin(); it5!=v.end(); it5++){
		cout<<*it5<<" ";
	}
	cout<<endl;

	for(auto it : v){
		cout<< it<<" ";
	}
	cout<<endl;


	//Erase / Delete 
	v.erase(v.begin()+1);	//{10,30,40,1,2}
	v.erase(v.begin()+1,v.begin()+3);	//{10,1,2}   [start,end)

	//Insert 

	v.insert(v.begin()+2,199);	//{10,1,199,2} (it,Element)
	v.insert(v.begin()+1,3,99);	//{10,99,99,99,1,199,2}  (it,NoOfTimes,Element) 

	v.pop_back();	//{10,99,99,99,1,199}	
	v.clear();	//{}
	cout<<v.size()<<endl;	//0

	cout<<v.empty()<<endl;	//1-true 0-false
}

void explainList(){
	//list is same as vector but it gives to add from front.
	//work like DLL
	list<int> l;
	l.push_back(1);
	l.emplace_back(2);

	l.push_front(4);
	l.emplace_front(3); //{3,4,1,2}
	l.pop_back();
	l.pop_front();
	for(int x : l){
		cout << x << " ";
	}
	cout << endl;
	// rest are same as vector
	// begin, end, rbegin, rend, clear, insert, size, swap
}

void explainDeque(){
	//exactly same as list and vector
	deque<int> q;
	// push_back,emplace_back,push_front,emplace_front,pop_back,pop_front
	// rest are same as vector
	// begin, end, rbegin, rend, clear, insert, size, swap
}

void explainStack(){
	stack<int> s;	//LIFO - jo last m aaya wahi first jaega 
	s.push(1);
	s.push(2);
	s.emplace(3);
	cout << s.top() << endl;
	s.pop();
	cout << s.top() << endl;	//top of stack
	cout << s.empty() << endl;	//true or false

	stack<int> s1,s2;
	s1.push(1);
	s2.push(2);
	s1.swap(s2);	//copy stack
	cout << s1.top() << " " << s2.top() << endl;

	//all operations take O(1)
}

void explainQueue(){
	queue<int> q;	//FIFO
	q.push(1);
	q.push(2);
	q.emplace(3);

	cout << q.back() << endl;	//3
	cout << q.front() << endl;	//1

	q.pop();	// 2 3
	cout << q.front() << endl;	//2

	//size swap empty same as stack
	//all operations take O(1)
}

void explainPriorityQueue(){
	priority_queue<int> pq;		// Max Heap - Max at top
	pq.push(1);
	pq.push(2);
	pq.emplace(3);

	cout << pq.top() << endl;
	pq.pop();
	cout << pq.top() << endl;

	//size swap empty same as stack

	priority_queue<int, vector<int>, greater<int>> minheap;
	minheap.push(1);
	minheap.push(2);
	cout << minheap.top() << endl;

	// push - logn
	// pop - logn
	// top - O(1)
}

void explainSet(){
	// sorted + unique elements
	set<int> s;
	s.insert(1);
	s.insert(2);
	s.insert(3);
	s.emplace(3);

	// Functionality of insert in vector can be used also,
	// that only increases efficiency
	// begin,end,rbegin,rend,size,empty,swap are same as above

	auto it = s.find(5); 	// s.end()
	it = s.find(3);
	s.erase(1);		// (element)
	s.erase(it);	// (iterator)
	// s.erase(it + 3, it + 6); 	// [start,end)
	int cnt = s.count(2);

}

void explainBinarySearch(){
	vector<int> v = {1, 3, 4, 4, 5, 5, 5, 5, 5, 8, 9};
	cout << binary_search(v.begin(), v.end(), 3) << endl;
	cout << binary_search(v.begin(), v.end(), 5) << endl;

	auto low =  lower_bound(v.begin(), v.end(), 4)  ;
	cout << low - v.begin() << endl;
	auto up = upper_bound(v.begin(), v.end(), 4);
	cout << up - v.begin() << endl;
}

void explainMultiset(){
	// Sorted + NotUnique
	multiset<int> ms;
	ms.insert(1);	// {1}
	ms.insert(1);	// {1,1}
	ms.insert(1);	// {1,1,1}
	ms.insert(1);	// {1,1,1,1}
	ms.insert(2);	// {1,1,1,1,2}
	ms.insert(3);	// {1,1,1,1,2,3}
	ms.insert(3);	// {1,1,1,1,2,3,3}

	ms.erase(1);	// erase all the 1's erased
	ms.erase(ms.find(2));	// only single value is erased
	int cnt = ms.count(1);	// 0
	ms.erase(ms.find(1), ms.find(2));	// [startiterator,enditerator)

	// rest all are same as set
}

void explainUnorderedSet(){
	// Unsorted + Unique
	unordered_set<int> us;
	us.insert(1);
	us.insert(2);

	us.erase(1);
	us.erase(us.find(2));

	// LowerBound and UpperBound function doesn't work
	// Because it is not sorted

	// All operation in O(1) 99%
	// 1% it takes in O(N)
}

void explainMap(){
	// Unique keys + Sorted		<key,pair> 
	map<int, int> mp;
	mp[1] = 2;	// {1,2}
	mp.emplace(3, 1);	// {1,2},{3,1}
	mp.insert({2, 4});	// {1,2},{2,4},{3,1}

	for(auto it: mp){
		//     ---key---           --value--
		cout << it.first << " " << it.second << endl;
	}

	auto it = mp.find(1);
	cout << (*it).second << endl;	// 2

	it = mp.upper_bound(1);
	it = mp.lower_bound(2);

	// erase, swap, size, empty are same as above
}

void explainMultiMap(){
	multimap<int, int> mp;
	// everything is same as map but it can store duplicated keys with sorted in nature;
	// only mp[key] can't be use here, instead you can use insert and emplace
}

void explainUnorderedMap(){
	unordered_map<int, int> mp;

	// all operations work in constant time;
	// 1 out of 100 case, it shows O(N); 
}

void explainAlgorithms(){
	int a[n];
	sort(a, a + n);
	sort(v.begin(), v.end());
	sort(a + 2, a + 4);

	sort(v.begin(), v.end(), greater<int>());

	pair<int, int> a[] = {{1, 3}, {2, 3}};
	// default it sort according to first element
	// but if want to sort according to second element
	sort(a, a + n, comp);

	int num = 7;
	//counts the set bits in num
	// 7 = 000000000111    --32bit number
	int count = __builtin_popcount(num);	// 3
	long long num = 2;
	count = __builtin_popcountll(num);	// 1

	string s = "123";
	sort(s.begin(), s.end());	//if want to print all the permutations, then ensure item must be sorted

	reverse(s.begin(), s.end()); 	//reverse the array

	while(next_permutation(s.begin(),s.end())){
		cout << s << endl;
	}

	auto it = max_element(a, a + n);	// return iterator of max element
	cout << *it << endl;
	it = min_element(a, a + n);		//return iterator of min element
	cout << *it << endl;
}

// Comparator function must have return type 'bool'
// In Leetcode, Use "static bool" rather than "bool"
bool comp(pair<int,int> p1, pair<int,int> p2){
	if(p1.second < p2.second){
		return true;
	}
	else if(p1.second > p2.second){
		return false;
	}
	else if(p1.second == p2.second){
		if(p1.first <= p2.first){
			return true;
		}
		else{
			return false;
		}
	}
}

int main(){
// #ifndef ONLINE_JUDGE
// 	freopen("input.txt","r",stdin);
// 	freopen("output.txt","w",stdout);
// #endif
	explainPair();
	explainVector();
	explainList();
	explainDeque();
	explainStack();
	explainQueue();
	explainPriorityQueue();
	explainBinarySearch();
	explainAlgorithms();
}#include <bits/stdc++.h>
using namespace std;
int n;
vector<int> v;

/*-----Notes Start from here-----*/

void explainPair(){
	pair<int,int> p1 = {1,4};
	cout<<p1.first<<" "<<p1.second<<endl;

	pair<int,pair<int,int>> p2 = {1,{4,5}};
	cout<<p2.first<<" "<<p2.second.first<<" "<<p2.second.second<<endl;

	//also use as datatype of array
	pair<int,int> arr[] = {{1,3},{2,4},{4,5}};
	cout<<arr[1].first<<" "<<arr[2].second<<endl;
}

void explainVector(){
	vector<int> v;			//{}
	v = {10,20,30,40};
	v.push_back(1);			//{1}
	v.emplace_back(2);		//{1,2}

	vector<pair<int,int>> vp;
	vp.push_back({1,3});	//Must put braces 
	vp.emplace_back(1,2);	//automatically put braces 
	
	for(auto it : vp){
		cout<<it.first<<" "<<it.second<<endl;
	}

	//already filled vector
	vector<int> valready(10,100);	//{100,100,...10times }
	
	//copy vector in another vector
	vector<int> vcopy(valready);

	vector<int>::iterator it1 = vcopy.begin();	//consider it as a pointer
	vector<int>::iterator it2 = vcopy.end();	//it points to the next of last index
	//   10 20 30 40
	//   |           |
	//  begin       end

	//Get value with iterator
	cout<<*it1<<*(it1++)<<endl;

	// vector<int>::iterator it3 = vcopy.rend();	//reverse-end
	// vector<int>::iterator it4 = vcopy.rbegin(); //reverse-begin
	//     10 20 30 40
	//   |           |
	//   rend      rbegin      rbegin++ = 30

	cout<<v.front()<<" "<<v.back()<<endl;

	for(vector<int>::iterator it5 = v.begin(); it5!=v.end(); it5++){
		cout<<*it5<<" ";
	}
	cout<<endl;

	// auto helps to auto assign the datatype
	// auto it = v.begin();  auto assigns as iterator
	// auto s = "karan";     auto assigns as string

	for(auto it5 = v.begin(); it5!=v.end(); it5++){
		cout<<*it5<<" ";
	}
	cout<<endl;

	for(auto it : v){
		cout<< it<<" ";
	}
	cout<<endl;


	//Erase / Delete 
	v.erase(v.begin()+1);	//{10,30,40,1,2}
	v.erase(v.begin()+1,v.begin()+3);	//{10,1,2}   [start,end)

	//Insert 

	v.insert(v.begin()+2,199);	//{10,1,199,2} (it,Element)
	v.insert(v.begin()+1,3,99);	//{10,99,99,99,1,199,2}  (it,NoOfTimes,Element) 

	v.pop_back();	//{10,99,99,99,1,199}	
	v.clear();	//{}
	cout<<v.size()<<endl;	//0

	cout<<v.empty()<<endl;	//1-true 0-false
}

void explainList(){
	//list is same as vector but it gives to add from front.
	//work like DLL
	list<int> l;
	l.push_back(1);
	l.emplace_back(2);

	l.push_front(4);
	l.emplace_front(3); //{3,4,1,2}
	l.pop_back();
	l.pop_front();
	for(int x : l){
		cout << x << " ";
	}
	cout << endl;
	// rest are same as vector
	// begin, end, rbegin, rend, clear, insert, size, swap
}

void explainDeque(){
	//exactly same as list and vector
	deque<int> q;
	// push_back,emplace_back,push_front,emplace_front,pop_back,pop_front
	// rest are same as vector
	// begin, end, rbegin, rend, clear, insert, size, swap
}

void explainStack(){
	stack<int> s;	//LIFO - jo last m aaya wahi first jaega 
	s.push(1);
	s.push(2);
	s.emplace(3);
	cout << s.top() << endl;
	s.pop();
	cout << s.top() << endl;	//top of stack
	cout << s.empty() << endl;	//true or false

	stack<int> s1,s2;
	s1.push(1);
	s2.push(2);
	s1.swap(s2);	//copy stack
	cout << s1.top() << " " << s2.top() << endl;

	//all operations take O(1)
}

void explainQueue(){
	queue<int> q;	//FIFO
	q.push(1);
	q.push(2);
	q.emplace(3);

	cout << q.back() << endl;	//3
	cout << q.front() << endl;	//1

	q.pop();	// 2 3
	cout << q.front() << endl;	//2

	//size swap empty same as stack
	//all operations take O(1)
}

void explainPriorityQueue(){
	priority_queue<int> pq;		// Max Heap - Max at top
	pq.push(1);
	pq.push(2);
	pq.emplace(3);

	cout << pq.top() << endl;
	pq.pop();
	cout << pq.top() << endl;

	//size swap empty same as stack

	priority_queue<int, vector<int>, greater<int>> minheap;
	minheap.push(1);
	minheap.push(2);
	cout << minheap.top() << endl;

	// push - logn
	// pop - logn
	// top - O(1)
}

void explainSet(){
	// sorted + unique elements
	set<int> s;
	s.insert(1);
	s.insert(2);
	s.insert(3);
	s.emplace(3);

	// Functionality of insert in vector can be used also,
	// that only increases efficiency
	// begin,end,rbegin,rend,size,empty,swap are same as above

	auto it = s.find(5); 	// s.end()
	it = s.find(3);
	s.erase(1);		// (element)
	s.erase(it);	// (iterator)
	// s.erase(it + 3, it + 6); 	// [start,end)
	int cnt = s.count(2);

}

void explainBinarySearch(){
	vector<int> v = {1, 3, 4, 4, 5, 5, 5, 5, 5, 8, 9};
	cout << binary_search(v.begin(), v.end(), 3) << endl;
	cout << binary_search(v.begin(), v.end(), 5) << endl;

	auto low =  lower_bound(v.begin(), v.end(), 4)  ;
	cout << low - v.begin() << endl;
	auto up = upper_bound(v.begin(), v.end(), 4);
	cout << up - v.begin() << endl;
}

void explainMultiset(){
	// Sorted + NotUnique
	multiset<int> ms;
	ms.insert(1);	// {1}
	ms.insert(1);	// {1,1}
	ms.insert(1);	// {1,1,1}
	ms.insert(1);	// {1,1,1,1}
	ms.insert(2);	// {1,1,1,1,2}
	ms.insert(3);	// {1,1,1,1,2,3}
	ms.insert(3);	// {1,1,1,1,2,3,3}

	ms.erase(1);	// erase all the 1's erased
	ms.erase(ms.find(2));	// only single value is erased
	int cnt = ms.count(1);	// 0
	ms.erase(ms.find(1), ms.find(2));	// [startiterator,enditerator)

	// rest all are same as set
}

void explainUnorderedSet(){
	// Unsorted + Unique
	unordered_set<int> us;
	us.insert(1);
	us.insert(2);

	us.erase(1);
	us.erase(us.find(2));

	// LowerBound and UpperBound function doesn't work
	// Because it is not sorted

	// All operation in O(1) 99%
	// 1% it takes in O(N)
}

void explainMap(){
	// Unique keys + Sorted		<key,pair> 
	map<int, int> mp;
	mp[1] = 2;	// {1,2}
	mp.emplace(3, 1);	// {1,2},{3,1}
	mp.insert({2, 4});	// {1,2},{2,4},{3,1}

	for(auto it: mp){
		//     ---key---           --value--
		cout << it.first << " " << it.second << endl;
	}

	auto it = mp.find(1);
	cout << (*it).second << endl;	// 2

	it = mp.upper_bound(1);
	it = mp.lower_bound(2);

	// erase, swap, size, empty are same as above
}

void explainMultiMap(){
	multimap<int, int> mp;
	// everything is same as map but it can store duplicated keys with sorted in nature;
	// only mp[key] can't be use here, instead you can use insert and emplace
}

void explainUnorderedMap(){
	unordered_map<int, int> mp;

	// all operations work in constant time;
	// 1 out of 100 case, it shows O(N); 
}

void explainAlgorithms(){
	int a[n];
	sort(a, a + n);
	sort(v.begin(), v.end());
	sort(a + 2, a + 4);

	sort(v.begin(), v.end(), greater<int>());

	pair<int, int> a[] = {{1, 3}, {2, 3}};
	// default it sort according to first element
	// but if want to sort according to second element
	sort(a, a + n, comp);

	int num = 7;
	//counts the set bits in num
	// 7 = 000000000111    --32bit number
	int count = __builtin_popcount(num);	// 3
	long long num = 2;
	count = __builtin_popcountll(num);	// 1

	string s = "123";
	sort(s.begin(), s.end());	//if want to print all the permutations, then ensure item must be sorted

	reverse(s.begin(), s.end()); 	//reverse the array

	while(next_permutation(s.begin(),s.end())){
		cout << s << endl;
	}

	auto it = max_element(a, a + n);	// return iterator of max element
	cout << *it << endl;
	it = min_element(a, a + n);		//return iterator of min element
	cout << *it << endl;
}

// Comparator function must have return type 'bool'
// In Leetcode, Use "static bool" rather than "bool"
bool comp(pair<int,int> p1, pair<int,int> p2){
	if(p1.second < p2.second){
		return true;
	}
	else if(p1.second > p2.second){
		return false;
	}
	else if(p1.second == p2.second){
		if(p1.first <= p2.first){
			return true;
		}
		else{
			return false;
		}
	}
}

int main(){
	explainPair();
	explainVector();
	explainList();
	explainDeque();
	explainStack();
	explainQueue();
	explainPriorityQueue();
	explainBinarySearch();
	explainAlgorithms();
}
