Below are **Two Pointer problems in C++** with:

✔ **Brute Force (BF)**
✔ **Optimized using pattern**
✔ **Further optimization (if possible)**
✔ **Proper Time Complexity (TC) & Space Complexity (SC)**
✔ **Short form complexity counting (for loop based)**

---

# 1️⃣ Two Sum (Sorted Array)

## 🔴 Brute Force

Check all pairs.

```cpp
vector<int> twoSum(vector<int>& nums, int target)
{
    for(int i = 0; i < nums.size(); i++)          // runs n times
    {
        for(int j = i+1; j < nums.size(); j++)    // runs n times
        {
            if(nums[i] + nums[j] == target)
                return {i,j};
        }
    }
    return {};
}
```

### TC calculation

outer loop → n
inner loop → n

Total:

```
n * n = n²
```

TC = **O(n²)**
SC = **O(1)**

---

## 🟢 Optimized Two Pointer

```cpp
vector<int> twoSum(vector<int>& nums, int target)
{
    int l = 0;
    int r = nums.size()-1;

    while(l < r)     // runs at most n times
    {
        int sum = nums[l] + nums[r];

        if(sum == target)
            return {l,r};

        else if(sum < target)
            l++;

        else
            r--;
    }

    return {};
}
```

### TC calculation

while loop runs at most n times

TC = **O(n)**
SC = **O(1)**

---

## 🔵 Further optimization (unsorted array)

```cpp
vector<int> twoSum(vector<int>& nums, int target)
{
    unordered_map<int,int> mp;

    for(int i=0;i<nums.size();i++)   // n
    {
        int x = target - nums[i];

        if(mp.count(x))
            return {mp[x], i};

        mp[nums[i]] = i;
    }

    return {};
}
```

TC:

```
single loop → n
hashmap lookup → O(1)
```

TC = **O(n)**
SC = **O(n)**

---

# 2️⃣ Container With Most Water

## 🔴 Brute Force

```cpp
int maxArea(vector<int>& h)
{
    int ans = 0;

    for(int i=0;i<h.size();i++)        // n
    {
        for(int j=i+1;j<h.size();j++)  // n
        {
            int area =
            min(h[i],h[j])*(j-i);

            ans=max(ans,area);
        }
    }

    return ans;
}
```

TC calculation:

```
n * n = n²
```

TC = **O(n²)**
SC = **O(1)**

---

## 🟢 Optimized Two Pointer

```cpp
int maxArea(vector<int>& h)
{
    int l=0;
    int r=h.size()-1;

    int ans=0;

    while(l<r)   // n
    {
        int ht=min(h[l],h[r]);

        ans=max(ans, ht*(r-l));

        if(h[l]<h[r])
            l++;
        else
            r--;
    }

    return ans;
}
```

TC:

```
single loop → n
```

TC = **O(n)**
SC = **O(1)**

---

# 3️⃣ Palindrome Check

## 🔴 Brute Force

```cpp
bool isPalindrome(string s)
{
    string rev=s;

    reverse(rev.begin(),rev.end()); // n

    return s==rev;  // n
}
```

TC calculation:

```
reverse → n
compare → n

n + n = 2n
remove constant → n
```

TC = **O(n)**
SC = **O(n)** (extra string)

---

## 🟢 Two Pointer Optimized

```cpp
bool isPalindrome(string s)
{
    int l=0;
    int r=s.size()-1;

    while(l<r)   // n/2
    {
        if(s[l]!=s[r])
            return false;

        l++;
        r--;
    }

    return true;
}
```

TC:

```
n/2 → remove constant
```

TC = **O(n)**
SC = **O(1)**

Better space optimization ✔

---

# 4️⃣ Merge Sorted Array

## 🔴 Brute Force

```cpp
void merge(vector<int>& a,int m,
           vector<int>& b,int n)
{
    for(int i=0;i<n;i++)   // n
        a[m+i]=b[i];

    sort(a.begin(),a.end());  // n log n
}
```

TC calculation:

```
copy → n
sort → n log n

total → n log n
```

TC = **O(n log n)**
SC = **O(1)**

---

## 🟢 Two Pointer Optimized

```cpp
void merge(vector<int>& a,int m,
           vector<int>& b,int n)
{
    int i=m-1;
    int j=n-1;
    int k=m+n-1;

    while(j>=0)   // n
    {
        if(i>=0 && a[i]>b[j])
        {
            a[k]=a[i];
            i--;
        }
        else
        {
            a[k]=b[j];
            j--;
        }

        k--;
    }
}
```

TC:

```
single loop → n
```

TC = **O(n)**
SC = **O(1)**

---

# Quick Complexity Pattern Recognition

| pattern        | loops   | TC          |
| -------------- | ------- | ----------- |
| nested loop    | n × n   | n²          |
| single loop    | n       | n           |
| half loop      | n/2     | n           |
| sorting        | n log n | n log n     |
| hashmap lookup | 1       | constant    |
| recursion tree | 2ⁿ      | exponential |

---

# Short Trick to Calculate TC in interview

### for loop

```
for(i=0;i<n;i++)
```

→ O(n)

### nested loop

```
for(i)
   for(j)
```

→ O(n²)

### while(l<r)

pointer moves once each iteration

→ O(n)

---


