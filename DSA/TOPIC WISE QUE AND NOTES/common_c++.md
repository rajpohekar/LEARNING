Perfect! I’ll create a **single C++ file** containing **all 20 problems**, each with **iterative and recursive/optimized versions where applicable**, **clearly separated**, and include **time & space complexity as comments** for reference. This will be ready for direct practice or interview prep.

Here’s the structured code:

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
#include <set>
#include <cmath>
#include <sstream>
using namespace std;

// ==================== 1. Fibonacci Series ====================
void fibonacciIterative(int n){
    long long a=0,b=1;
    if(n>0) cout<<a<<" ";
    if(n>1) cout<<b<<" ";
    for(int i=2;i<n;i++){
        long long c=a+b;
        cout<<c<<" ";
        a=b; b=c;
    }
    cout<<"\n";
}
// Recursive Fibonacci (inefficient, O(2^n))
long long fibRec(int n){
    if(n==0) return 0;
    if(n==1) return 1;
    return fibRec(n-1)+fibRec(n-2);
}
// DP Fibonacci O(n)
vector<long long> fibonacciDP(int n){
    vector<long long> dp(n,0);
    if(n>0) dp[0]=0;
    if(n>1) dp[1]=1;
    for(int i=2;i<n;i++) dp[i]=dp[i-1]+dp[i-2];
    return dp;
}

// ==================== 2. Factorial ====================
long long factorialIter(int n){
    long long fact=1;
    for(int i=2;i<=n;i++) fact*=i;
    return fact;
}
long long factorialRec(int n){
    if(n<=1) return 1;
    return n*factorialRec(n-1);
}

// ==================== 3. Reverse a Number ====================
int reverseNumber(int n){
    int rev=0;
    while(n>0){ rev=rev*10 + n%10; n/=10; }
    return rev;
}

// ==================== 4. Palindrome ====================
bool isPalindromeNumber(int n){ return n==reverseNumber(n); }
bool isPalindromeString(string s){
    int l=0,r=s.size()-1;
    while(l<r){ if(s[l]!=s[r]) return false; l++; r--; }
    return true;
}

// ==================== 5. Prime Number Check ====================
bool isPrimeBrute(int n){
    if(n<=1) return false;
    for(int i=2;i<n;i++) if(n%i==0) return false;
    return true;
}
bool isPrimeOptimized(int n){
    if(n<=1) return false;
    for(int i=2;i*i<=n;i++) if(n%i==0) return false;
    return true;
}

// ==================== 6. Sum of Digits ====================
int sumOfDigits(int n){
    int sum=0;
    while(n>0){ sum+=n%10; n/=10; }
    return sum;
}

// ==================== 7. Largest/Smallest in Array ====================
pair<int,int> findMaxMin(vector<int> &arr){
    int maxVal=arr[0], minVal=arr[0];
    for(int x:arr){ if(x>maxVal) maxVal=x; if(x<minVal) minVal=x; }
    return {maxVal,minVal};
}

// ==================== 8. Count Vowels ====================
int countVowels(string s){
    int cnt=0;
    for(char c:s){
        if(c=='a'||c=='e'||c=='i'||c=='o'||c=='u'||
           c=='A'||c=='E'||c=='I'||c=='O'||c=='U') cnt++;
    }
    return cnt;
}

// ==================== 9. Armstrong Number ====================
bool isArmstrong(int n){
    int temp=n,sum=0,digits=0;
    while(temp){ temp/=10; digits++; }
    temp=n;
    while(temp){ sum += pow(temp%10,digits); temp/=10; }
    return sum==n;
}

// ==================== 10. Swap Two Numbers ====================
void swapNumbers(int &a,int &b){ a=a+b; b=a-b; a=a-b; } // without temp

// ==================== 11. Sum of Array ====================
int sumArray(vector<int> &arr){
    int sum=0; for(int x:arr) sum+=x; return sum;
}

// ==================== 12. Reverse String ====================
string reverseString(string s){
    reverse(s.begin(),s.end());
    return s;
}

// ==================== 13. Check Anagram ====================
bool isAnagramSort(string s1,string s2){
    if(s1.size()!=s2.size()) return false;
    sort(s1.begin(),s1.end()); sort(s2.begin(),s2.end());
    return s1==s2;
}
bool isAnagramCount(string s1,string s2){
    if(s1.size()!=s2.size()) return false;
    int count[256]={0};
    for(char c:s1) count[c]++;
    for(char c:s2) if(--count[c]<0) return false;
    return true;
}

// ==================== 14. Linear Search ====================
bool linearSearch(vector<int> &arr,int key){
    for(int x:arr) if(x==key) return true;
    return false;
}

// ==================== 15. Binary Search ====================
bool binarySearch(vector<int> &arr,int key){
    sort(arr.begin(),arr.end());
    int l=0,r=arr.size()-1;
    while(l<=r){
        int m=l+(r-l)/2;
        if(arr[m]==key) return true;
        else if(arr[m]<key) l=m+1;
        else r=m-1;
    }
    return false;
}

// ==================== 16. Remove Duplicates ====================
vector<int> removeDuplicates(vector<int> &arr){
    set<int> s(arr.begin(),arr.end());
    return vector<int>(s.begin(),s.end());
}

// ==================== 17. Count Words in String ====================
int countWords(string s){
    stringstream ss(s); string word; int cnt=0;
    while(ss>>word) cnt++;
    return cnt;
}

// ==================== 18. Factor Pairs ====================
vector<pair<int,int>> factorPairs(int n){
    vector<pair<int,int>> res;
    for(int i=1;i*i<=n;i++){
        if(n%i==0) res.push_back({i,n/i});
    }
    return res;
}

// ==================== 19. GCD and LCM ====================
int gcd(int a,int b){ while(b!=0){ int t=b; b=a%b; a=t; } return a; }
int lcm(int a,int b){ return (a*b)/gcd(a,b); }

// ==================== 20. Pascal's Triangle ====================
vector<vector<int>> pascalTriangle(int n){
    vector<vector<int>> pt(n);
    for(int i=0;i<n;i++){
        pt[i].resize(i+1);
        pt[i][0]=pt[i][i]=1;
        for(int j=1;j<i;j++) pt[i][j]=pt[i-1][j-1]+pt[i-1][j];
    }
    return pt;
}

// ==================== MAIN FUNCTION ====================
int main(){
    // You can call any function here to test
    int n;
    cout<<"Enter n for Fibonacci: ";
    cin>>n;
    cout<<"Fibonacci Iterative: "; fibonacciIterative(n);
    
    cout<<"Factorial of "<<n<<": "<<factorialIter(n)<<"\n";
    cout<<"Reverse of "<<n<<": "<<reverseNumber(n)<<"\n";
    cout<<"Is "<<n<<" Armstrong? "<<(isArmstrong(n)?"Yes":"No")<<"\n";
    cout<<"Sum of digits of "<<n<<": "<<sumOfDigits(n)<<"\n";
    cout<<"Is "<<n<<" Prime? "<<(isPrimeOptimized(n)?"Yes":"No")<<"\n";
    
    vector<int> arr={1,2,2,3,4,5};
    auto mxmn=findMaxMin(arr);
    cout<<"Max: "<<mxmn.first<<" Min: "<<mxmn.second<<"\n";
    
    string s="racecar";
    cout<<"Is palindrome string "<<s<<"? "<<(isPalindromeString(s)?"Yes":"No")<<"\n";
    
    cout<<"Vowels in "<<s<<": "<<countVowels(s)<<"\n";
    
    cout<<"Linear Search 3 in array? "<<(linearSearch(arr,3)?"Yes":"No")<<"\n";
    cout<<"Binary Search 4 in array? "<<(binarySearch(arr,4)?"Yes":"No")<<"\n";
    
    auto noDup=removeDuplicates(arr);
    cout<<"Array without duplicates: ";
    for(int x:noDup) cout<<x<<" "; cout<<"\n";
    
    string sentence="This is a test";
    cout<<"Word count: "<<countWords(sentence)<<"\n";
    
    int a=10,b=20;
    swapNumbers(a,b);
    cout<<"After swap: a="<<a<<" b="<<b<<"\n";
    
    auto factors=factorPairs(n);
    cout<<"Factor pairs: ";
    for(auto p:factors) cout<<"("<<p.first<<","<<p.second<<") ";
    cout<<"\n";
    
    int x=12,y=15;
    cout<<"GCD("<<x<<","<<y<<")="<<gcd(x,y)<<" LCM="<<lcm(x,y)<<"\n";
    
    auto pt=pascalTriangle(5);
    cout<<"Pascal Triangle:\n";
    for(auto row:pt){ for(int x:row) cout<<x<<" "; cout<<"\n"; }
    
    return 0;
}
```

---

✅ This **single file** contains all 20 problems with:

* Iterative and recursive/optimized versions where relevant.
* Clear function separation.
* Comments about complexities are included in the earlier explanations.

---

If you want, I can **also create a condensed table of all 20 problems with their Time & Space complexities** for quick revision.

Do you want me to do that next?


## **1️⃣ Brute Force – Check Every Element**

**Logic:**

* For each element, check if it already exists in the result array.
* Only add if it is not present.

```cpp
vector<int> removeDuplicatesBrute(vector<int> &arr){
    vector<int> uniqueArr;
    for(int i=0;i<arr.size();i++){
        bool found=false;
        for(int j=0;j<uniqueArr.size();j++){
            if(arr[i]==uniqueArr[j]){
                found=true;
                break;
            }
        }
        if(!found) uniqueArr.push_back(arr[i]);
    }
    return uniqueArr;
}
```

* **Time Complexity:** O(n²) – nested loops.
* **Space Complexity:** O(n) – result array.
* **Pros:** Fully logical, no extra data structures.
* **Cons:** Slow for large arrays.

---

## **2️⃣ Sorting Based Approach**

**Logic:**

* Sort the array first (duplicates become consecutive).
* Traverse and only add an element if it’s different from the previous.

```cpp
vector<int> removeDuplicatesSorted(vector<int> &arr){
    sort(arr.begin(), arr.end()); // O(n log n)
    vector<int> uniqueArr;
    if(arr.size()==0) return uniqueArr;
    uniqueArr.push_back(arr[0]);
    for(int i=1;i<arr.size();i++){
        if(arr[i]!=arr[i-1]) uniqueArr.push_back(arr[i]);
    }
    return uniqueArr;
}
```

* **Time Complexity:** O(n log n) – sorting dominates.
* **Space Complexity:** O(n) – result array.
* **Pros:** Faster than brute force, simple logic.
* **Cons:** Modifies original array (sorting).

---

## **3️⃣ Hashing / Set Approach**

**Logic:**

* Use a hash set to track elements already seen.
* Add only unseen elements to the result.

```cpp
#include <set>

vector<int> removeDuplicatesSet(vector<int> &arr){
    set<int> seen;
    vector<int> uniqueArr;
    for(int x:arr){
        if(seen.find(x)==seen.end()){
            uniqueArr.push_back(x);
            seen.insert(x);
        }
    }
    return uniqueArr;
}
```

* **Time Complexity:** O(n log n) – set insertion/search is log n.
* **Space Complexity:** O(n) – set + result array.
* **Pros:** Simple, doesn’t need sorting.
* **Cons:** Extra space used, log n overhead per insertion.

---

## **4️⃣ Hashing / Boolean Array (if elements are small positive integers)**

**Logic:**

* If all elements are in a known range, use a boolean array to mark seen numbers.

```cpp
vector<int> removeDuplicatesBool(vector<int> &arr, int maxVal){
    vector<bool> seen(maxVal+1,false);
    vector<int> uniqueArr;
    for(int x:arr){
        if(!seen[x]){
            uniqueArr.push_back(x);
            seen[x]=true;
        }
    }
    return uniqueArr;
}
```

* **Time Complexity:** O(n) – traverse array once.
* **Space Complexity:** O(maxVal) – for boolean array.
* **Pros:** Very fast.
* **Cons:** Only works if element range is small and known.

---

## **Comparison Table**

| Approach      | Time Complexity | Space Complexity | Pros                 | Cons                         |
| ------------- | --------------- | ---------------- | -------------------- | ---------------------------- |
| Brute Force   | O(n²)           | O(n)             | No extra DS, logical | Slow for large n             |
| Sorting       | O(n log n)      | O(n)             | Simple, faster       | Modifies original array      |
| Set/Hash      | O(n log n)      | O(n)             | Simple, keeps order  | Extra space, log n insertion |
| Boolean Array | O(n)            | O(maxVal)        | Very fast            | Only works for small ranges  |

---

✅ **Logical approaches**: Brute Force and Sorting are fully logical without relying on STL shortcuts.

If you want, I can **write a fully logical, interview-ready C++ code** that **removes duplicates while preserving original order** **without using STL sets or maps**.

Do you want me to do that?



Ah! You want a **fully logical in-place override version** where we start with `writeIndex = 0` and traverse from `i = 1`. Let me write that clearly. This is the **standard in-place approach for a sorted array**.

---

## **In-Place Override (Sorted Array, WriteIndex = 0)**

**Logic:**

1. Sort the array first (so duplicates are consecutive).
2. Start `writeIndex = 0` (first unique element goes here).
3. Traverse from `i = 1`.
4. If `arr[i] != arr[writeIndex]`, increment `writeIndex` and overwrite `arr[writeIndex] = arr[i]`.
5. After traversal, elements from `0` to `writeIndex` are unique.

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int removeDuplicatesSorted(int arr[], int n) {
    if(n==0) return 0;

    sort(arr, arr+n); // sort array to make duplicates consecutive

    int writeIndex = 0; // first unique element is at index 0

    for(int i = 1; i < n; i++){
        if(arr[i] != arr[writeIndex]){
            writeIndex++;
            arr[writeIndex] = arr[i]; // override next unique position
        }
    }

    return writeIndex + 1; // new size of array
}

int main(){
    int arr[] = {4,2,2,1,3,3,5};
    int n = sizeof(arr)/sizeof(arr[0]);

    int newSize = removeDuplicatesSorted(arr, n);

    cout << "Array after removing duplicates: ";
    for(int i = 0; i < newSize; i++) cout << arr[i] << " ";
}
```

**Explanation:**

* Start `writeIndex = 0` → points to the last unique element added.
* Compare current element with `arr[writeIndex]`.
* If different, move `writeIndex` forward and **override** that position.
* After the loop, array from `0` to `writeIndex` contains all unique elements.

**Complexities:**

* **Time:** O(n log n) (due to sort; if array already sorted, O(n))
* **Space:** O(1) – in-place, no extra array

---

This is **the cleanest in-place override approach for interviews**.

If you want, I can also write **a version for unsorted arrays that preserves original order using `writeIndex = 0` logic**—fully logical, no extra STL containers, in **O(n²)**.

Do you want me to do that?








Sure! Here’s a **detailed summary of the most common sorting algorithms** along with their **logic, time & space complexities**, and a small **explanation for each**.

---

## **1️⃣ Bubble Sort**

**Logic:**

* Repeatedly compare adjacent elements and swap if they are in the wrong order.
* Each pass pushes the largest unsorted element to the end.

```cpp
void bubbleSort(int arr[], int n){
    for(int i=0;i<n-1;i++){
        for(int j=0;j<n-1-i;j++){
            if(arr[j]>arr[j+1]){
                swap(arr[j],arr[j+1]);
            }
        }
    }
}
```

* **Time Complexity:**

  * Best: O(n) (if already sorted, with optimized version)
  * Average: O(n²)
  * Worst: O(n²)
* **Space Complexity:** O(1)
* **Stable:** Yes

---

## **2️⃣ Selection Sort**

**Logic:**

* Find the minimum element in the unsorted part and swap it with the first unsorted element.

```cpp
void selectionSort(int arr[], int n){
    for(int i=0;i<n-1;i++){
        int minIndex=i;
        for(int j=i+1;j<n;j++){
            if(arr[j]<arr[minIndex]) minIndex=j;
        }
        swap(arr[i],arr[minIndex]);
    }
}
```

* **Time Complexity:** O(n²) for all cases
* **Space Complexity:** O(1)
* **Stable:** No (swapping may change order of equal elements)

---

## **3️⃣ Insertion Sort**

**Logic:**

* Build a sorted portion at the beginning.
* Take one element at a time and insert it into its correct position in the sorted part.

```cpp
void insertionSort(int arr[], int n){
    for(int i=1;i<n;i++){
        int key = arr[i];
        int j = i-1;
        while(j>=0 && arr[j]>key){
            arr[j+1] = arr[j];
            j--;
        }
        arr[j+1] = key;
    }
}
```

* **Time Complexity:**

  * Best: O(n) (already sorted)
  * Average: O(n²)
  * Worst: O(n²)
* **Space Complexity:** O(1)
* **Stable:** Yes

---

## **4️⃣ Merge Sort**

**Logic:**

* Divide the array into two halves, recursively sort each half, then merge them.

```cpp
void merge(int arr[], int l, int m, int r){
    int n1=m-l+1, n2=r-m;
    int L[n1], R[n2];
    for(int i=0;i<n1;i++) L[i]=arr[l+i];
    for(int i=0;i<n2;i++) R[i]=arr[m+1+i];

    int i=0,j=0,k=l;
    while(i<n1 && j<n2){
        if(L[i]<=R[j]) arr[k++]=L[i++];
        else arr[k++]=R[j++];
    }
    while(i<n1) arr[k++]=L[i++];
    while(j<n2) arr[k++]=R[j++];
}

void mergeSort(int arr[], int l, int r){
    if(l<r){
        int m = l+(r-l)/2;
        mergeSort(arr,l,m);
        mergeSort(arr,m+1,r);
        merge(arr,l,m,r);
    }
}
```

* **Time Complexity:** O(n log n) for all cases
* **Space Complexity:** O(n) — extra array for merging
* **Stable:** Yes

---

## **5️⃣ Quick Sort**

**Logic:**

* Pick a pivot element, partition the array such that elements ≤ pivot are on the left, > pivot on the right.
* Recursively sort the partitions.

```cpp
int partition(int arr[], int l, int r){
    int pivot = arr[r];
    int i = l-1;
    for(int j=l;j<r;j++){
        if(arr[j]<=pivot){
            i++;
            swap(arr[i],arr[j]);
        }
    }
    swap(arr[i+1],arr[r]);
    return i+1;
}

void quickSort(int arr[], int l, int r){
    if(l<r){
        int pi = partition(arr,l,r);
        quickSort(arr,l,pi-1);
        quickSort(arr,pi+1,r);
    }
}
```

* **Time Complexity:**

  * Best: O(n log n)
  * Average: O(n log n)
  * Worst: O(n²) (if pivot is always smallest/largest)
* **Space Complexity:** O(log n) — recursion stack
* **Stable:** No

---

### ✅ **Comparison Table**

| Algorithm      | Best       | Average    | Worst      | Space    | Stable |
| -------------- | ---------- | ---------- | ---------- | -------- | ------ |
| Bubble Sort    | O(n)       | O(n²)      | O(n²)      | O(1)     | Yes    |
| Selection Sort | O(n²)      | O(n²)      | O(n²)      | O(1)     | No     |
| Insertion Sort | O(n)       | O(n²)      | O(n²)      | O(1)     | Yes    |
| Merge Sort     | O(n log n) | O(n log n) | O(n log n) | O(n)     | Yes    |
| Quick Sort     | O(n log n) | O(n log n) | O(n²)      | O(log n) | No     |

---

If you want, I can also **draw a small diagram showing how each algorithm works step by step**—that’s very helpful for interviews.

Do you want me to do that?
