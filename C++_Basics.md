# 目录
- [哈希表(hash table)](#哈希表)
- [字符串(string)](#字符串)
- [动态数组(vector)](#动态数组)
- [常用常数](#常用常数)
- [栈(stack)](#栈)
- [堆(heap)](#堆)

# 哈希表
**hash table**
### unordered_map
创建：
``` cpp
#include <unordered_map>

unordered_map<string,int> mp; //string是key，int是value
```

初始化：
``` cpp
unordered_map<string,int> mp{
	{"Tom" , 10} , {"Alice" , 20} , {"Jack" , 30}
};
```

插入/修改：
``` cpp
mp["Tom"] = 95;
```

判断key是否存在：
``` cpp
if (mp.find("Tom") != mp.end())
{
	cout << "exist" << endl;
}
```

删除：
``` cpp
mp.erase("Tom")
```

遍历：
``` cpp
for (auto& p : mp)
{
	cout << p.first << ":" << p.second << endl;
	// 此处p.first是key，p.second是value
}
```

获取大小:
``` cpp
mp.size();
```

检查是否为空：
``` cpp
mp.empty();
```

安全读取：
``` cpp
mp.at(key)
// 如果key不存在会直接报错。如果是mp[key]，不存在会自动创建key为0。
```

### unordered_set
创建:
``` cpp
#include <unordered_set>

unordered_set<int> st;
unordered_set<int> st = {1,2,3,4};
unordered_set<string> words;
```

插入元素：
``` cpp
unordered_set<int> st;

st.insert(1);
st.insert(2);
st.insert(3);
// 重复插入不会报错，但只有一个
```

判断元素是否存在：
``` cpp
if (st.find(2) != st.end()) {
    cout << "Found";
}

if (st.find(5) == st.end()) {
    cout << "Not Found";
}
```

删除元素：
``` cpp
st.erase(2);
```

获取元素个数：
``` cpp
unordered_set<int> st = {1,2,3};

cout << st.size(); // 3
```

判断是否为空：
``` cpp
st.empty();
```

清空：
``` cpp
st.clear();
```

遍历：
``` cpp
for (int x : st) {
    cout << x << " ";
}
```

转换为vector：
``` cpp
vector<int> nums(st.begin(), st.end());
```

# 字符串
**string**

创建：
``` cpp
#include <string>

string s = "hello";
```

修改字符：
``` cpp
s[0] = 'H'; // 注意用单引号是字符，双引号是字符串
```

获取长度：
``` cpp
s.length();
s.size();
```

拼接字符串：
``` cpp
string a = "hello";
string b = "world";
string c = a + b;
c = a + " " + b; //添加空格
```

遍历字符串：
``` cpp
for (int i = 0; i < s.length(); i++)
{
	cout << s[i] << endl;
}

for (char c : s)
{
	cout << c << endl;
}
```

添加/删除字符：
``` cpp
s.push_back('a');
s.pop_back();
```

检查是否为空：
``` cpp
s.empty();
```

清空字符串：
``` cpp
s.clear();
```

取子串：
``` cpp
string s = "abcdef";
cout << s.substr(2,3); // 从下标2开始，长度3。会得到cde
```

查找字符串：
``` cpp
if (s.find("abc") != string::npos); // 说明找到了
```

替换：
``` cpp
string s = "hello";
s.replace(1,2,"xx"); // 从下标1开始，长度2。得到hxxlo
```

反转字符串：
``` cpp
reverse(s.begin(), s.end());
```

排序字符串：
``` cpp
sort(s.begin(), s.end());
```

字符串转数字：
``` cpp
int num = stoi(s);
```

# 动态数组
**vector**

创建&初始化：
``` cpp
vector<int> v;
vector<int> v(5); //初始化长度，数值默认为0
vector<int> v(5,7); //初始化长度和数值
vector<int> v = {1,2,3,4};
vector<pair<int,int>> v(5); //初始化为[(0,0), (0,0), (0,0), (0,0), (0,0)]
```

长度：
``` cpp
v.size();
```

尾部添加/删除：
``` cpp
v.push_back();
v.pop_back();
```

访问元素：
``` cpp
v[i];
v.at(i);
v.front();
v.back();
```

修改元素：
``` cpp
v[2] = 100;
```

遍历：
``` cpp
// 普通
for(int i = 0; i < v.size(); i++){cout << v[i];}

// 范围for
for(int x:v){cout << x;}

// 如果要修改，需要加&
for(int& x:v){x++;}
```

清空：
``` cpp
v.clear();
```

判空：
``` cpp
if(v.empty());
```

插入：
``` cpp
v.insert(v.begin(), 1); // 往开头插一个数
v.insert(v.begin()+2, 100); // 位置，数值，获得 1 2 100 3 4
v.insert(v.begin(), 5, 1); // 位置，个数，数值
```

删除：
``` cpp
v.erase(v.begin()+2); // 删除一个
v.erase(v.begin()+1, v.begin()+4); //删除一些，注意是左闭右开:[1,4)
```

排序：
``` cpp
sort(v.begin(), v.end()); // 升序
sort(v.begin(), v.end(), greater<int>()); // 降序
```

反转：
``` cpp
reverse(v.begin(), v.end());
```

查找：
``` cpp
auto it = find(v.begin(), v.end(), 5); // 5是target
if(it != v.end()) {
	// 说明找到了
	int position = it - v.begin();
}
```

# 常用常数
**const**

整数范围：
``` cpp
#include <climits>

INT_MAX      // 2147483647
INT_MIN      // -2147483648

LONG_MAX
LONG_MIN

LLONG_MAX
LLONG_MIN
```

浮点范围：
``` cpp
#include <cfloat>

DBL_MAX
DBL_MIN

FLT_MAX
FLT_MIN
```

无穷大：
``` cpp
const int INF = 1e9;
const long long INF = 1e18;
```

数学常数：
``` cpp
#include <cmath>

M_PI      // π
M_E       // e
```

空指针：
``` cpp
nullptr // 不要用NULL
```

# 栈
**stack**

创建：
``` cpp
#include <stack>

stack<int> st;
stack<char> st;
stack<pair<int,int>> st;
```

出入栈：
``` cpp
st.push(x);
st.push({3,4});
st.pop();
```

查看栈顶：
``` cpp
x = st.top(); 

// 注意.top()返回的是引用，可以修改例如 st.top += 1;
```

判空：
``` cpp
st.empty();
```

元素个数：
``` cpp
st.size();
```

# 堆
**heap**

创建大根堆：
``` cpp
priority_queue<int> pq; // 堆顶是最大值
```

创建小根堆：
``` cpp
priority_queue<
	int,
	vector<int>,
	greater<int>
> pq;
```

加入元素：
``` cpp
pq.push(x);
```

查看堆顶：
``` cpp
pq.top();
```

删除堆顶：
``` cpp
pq.pop();
```

判空：
``` cpp
pq.empty();
```

判断大小：
``` cpp
pq.size();
```

存pair：
``` cpp
priority_queue<pair<int,int>> pq; // 先比较第一位，在比较第二位
pq.push({5,2});
```

取：
``` cpp
pq.top().first
pq.top().second
```
