class Solution {
public:
    string capitalizeTitle(string title) {
       int i=0;
       while(i<title.length()){
        
        while(i<title.length() && title[i]==' '){i++;}
        int st=i;
        while(i<title.length() && title[i]!=' '){i++;}
        int end=i;
        int len=end-st;
        if(len>=3){
            if(title[st]>='a' && title[st]<='z'){title[st]=title[st]-'a'+'A';}
           
            for(int i=st+1;i<end;i++){
                if(title[i]>='A'&& title[i]<='Z'){title[i]=title[i]-'A'+'a';}
                else{continue;}
            }
        }
        else{
           for(int i=st;i<end;i++){
                if(title[i]>='A'&& title[i]<='Z'){title[i]=title[i]-'A'+'a';}
                else{continue;}
            }  
        }
        i++;
      }
    return title;
    }
    
};
### 🔍 In C++, the `continue` statement is used **inside loops** like `for`, `while`, or `do-while`.

It **skips the rest of the current iteration** and **jumps to the next iteration** of the loop.

---

### 📌 Meaning of `continue` in your code:

Let's look at this part:

```cpp
for(int i = st+1; i < end; i++) {
    if(title[i] >= 'A' && title[i] <= 'Z') {
        title[i] = title[i] - 'A' + 'a'; // convert to lowercase
    } else {
        continue;
    }
}
```

### 🔹 Explanation:

* If the current character is **uppercase**, you convert it to **lowercase**.
* If it's **already lowercase**, the `else` block says: `continue;`
* That means: "**Skip remaining code in the loop and go to the next character**".

---

### ✅ But here’s the thing:

> The `continue;` is **not needed** in your case — it’s **redundant**.

Why?

Because there is **no code** after the `else` block inside the loop.
So it would automatically go to the next iteration anyway.

---

### ✂️ Simplified version (without `continue`):

```cpp
for(int i = st+1; i < end; i++) {
    if(title[i] >= 'A' && title[i] <= 'Z') {
        title[i] = title[i] - 'A' + 'a';
    }
    // No need for 'else' or 'continue'
}
```

---

### ✅ Summary:

| Keyword      | Meaning                                         |
| ------------ | ----------------------------------------------- |
| `continue;`  | Skip rest of loop body & jump to next iteration |
| In your code | It does nothing extra; can be safely removed    |

---

Let me know if you'd like:

* ✍️ Handwritten-style diagram showing loop flow with `continue`
* 🧪 Dry run of this loop on a sample word like `"cAPs"`



#include <iostream>
#include <string>
using namespace std;

void printNthWord(string title, int n) {
    int i = 0;
    int wordCount = 0;

    while (i < title.length()) {
        // Skip spaces
        while (i < title.length() && title[i] == ' ') i++;

        int st = i;

        // Go to end of the word
        while (i < title.length() && title[i] != ' ') i++;

        int end = i;

        wordCount++;

        if (wordCount == n) {
            cout << "Word " << n << ": " << title.substr(st, end - st) << endl;
            return;
        }

        i++; // Move to next character
    }

    cout << "Word " << n << " not found!" << endl;
}

int main() {
    string title = "cAPiTal tHE TitLE";
    int n = 3;

    printNthWord(title, n);
    return 0;
}
string getNthWord(string title, int n) {
    int i = 0, wordCount = 0;

    while (i < title.length()) {
        // Skip spaces
        while (i < title.length() && title[i] == ' ') i++;

        int st = i;

        // Move to end of word
        while (i < title.length() && title[i] != ' ') i++;

        int end = i;
        wordCount++;

        if (wordCount == n) {
            string result = "";
            for (int j = st; j < end; j++) {
                result += title[j];  // Append each character
            }
            return result;
        }

        i++;  // Move to next word
    }

    return ""; // Not found
}


#include <iostream>
#include <string>
using namespace std;

string getSecondLastWord(string title) {
    int i = 0;
    string prev = "", curr = "";

    while (i < title.length()) {
        // Skip spaces
        while (i < title.length() && title[i] == ' ') i++;

        int st = i;

        // Move to end of the word
        while (i < title.length() && title[i] != ' ') i++;
        int end = i;

        if (st < end) {
            // Build current word manually
            prev = curr; // update second last
            curr = "";
            for (int j = st; j < end; j++) {
                curr += title[j];
            }
        }

        i++;
    }

    return prev;
}

int main() {
    string title = "  hello  world example ";
    cout << "Second last word: " << getSecondLastWord(title) << endl;
    return 0;
}



Absolutely! Here's a curated list of **string problems** that are **frequently asked in coding interviews** at top tech companies (Amazon, Google, Microsoft, etc.) — especially useful for practicing edge cases, logic building, and pointer manipulation.

---

## ✅ **Most Common String Problems for Interviews**

### 1. 🔁 **Reverse Words in a String**

**Leetcode #151**
Given a string, reverse the words (not characters) and clean up spaces.
👉 Practice: Handling spaces, word boundaries.

---

### 2. 🔄 **Valid Palindrome**

**Leetcode #125 / #680 (Valid Palindrome II)**
Check if a string is a palindrome (ignore spaces, punctuation, case).
👉 Practice: Two pointers, string clean-up.

---

### 3. 🔁 **Longest Palindromic Substring**

**Leetcode #5**
Find the longest substring which is a palindrome.
👉 Practice: Expand-around-center, DP.

---

### 4. 🧵 **String Compression**

**Leetcode #443**
Compress characters: `["a","a","b","b","c","c","c"]` → `"a2b2c3"`
👉 Practice: In-place modification.

---

### 5. 🔤 **Group Anagrams**

**Leetcode #49**
Group strings that are anagrams of each other.
👉 Practice: Hashing, sorting strings.

---

### 6. 🎲 **Valid Anagram**

**Leetcode #242**
Check if two strings are anagrams.
👉 Practice: Frequency count using arrays/maps.

---

### 7. 🔗 **Longest Common Prefix**

**Leetcode #14**
Find the longest common prefix among a list of strings.
👉 Practice: Vertical scan, binary search.

---

### 8. 🔀 **Check if Rotations**

E.g., `s1 = "abcde"`, `s2 = "cdeab"` → true
👉 Practice: Concatenation + `find()`.

---

### 9. 🔤 **ZigZag Conversion**

**Leetcode #6**
Write string in zigzag pattern and read row-wise.
👉 Practice: Index mapping.

---

### 10. 🔢 **Integer to Roman / Roman to Integer**

**Leetcode #12 / #13**
Convert between integer and Roman numerals.
👉 Practice: Mapping + subtraction logic.

---

### 11. 🧠 **First Unique Character**

**Leetcode #387**
Return index of first non-repeating char.
👉 Practice: Frequency + index tracking.

---

### 12. 🧠 **Implement `strStr()` / Substring Search**

**Leetcode #28**
Find the index of the first occurrence of needle in haystack.
👉 Practice: Brute force, KMP.

---

### 13. 🚫 **Remove All Occurrences of a Substring**

**Leetcode #1910**
E.g., remove `"ab"` from `"daabcbaabcbc"` → `"dabcbc"`
👉 Practice: Sliding window / stack.

---

### 14. 🧱 **Minimum Add to Make Parentheses Valid**

**Leetcode #921**
E.g., `"(()"` → 1, `")("` → 2
👉 Practice: Stack + count open/close balance.

---

### 15. 🔢 **Count and Say**

**Leetcode #38**
E.g., `1 → 11 → 21 → 1211`
👉 Practice: Frequency grouping, pattern building.

---

## 🔥 Bonus String Problems for Extra Practice

| Problem                              | Key Concept               |
| ------------------------------------ | ------------------------- |
| **Remove Duplicates**                | In-place, set, pointers   |
| **Check Isomorphic Strings**         | Map char → char           |
| **License Key Formatting**           | Clean string + regrouping |
| **Excel Column Title Conversion**    | Base-26 logic             |
| **Basic Calculator (I, II)**         | Stack + parsing           |
| **Decode String ("3\[a2\[c]]")**     | Recursion, stack          |
| **Longest Substring Without Repeat** | Sliding Window, HashMap   |
| **Find All Anagrams in a String**    | Sliding Window, frequency |
| **Replace Spaces with `%20`**        | Manual space handling     |

---

## 🧠 Want Structured Practice?

* 🔹 Easy: `Valid Palindrome`, `Valid Anagram`, `Reverse Words`
* 🔹 Medium: `Group Anagrams`, `Longest Prefix`, `Zigzag`, `Count and Say`
* 🔹 Hard: `Longest Palindromic Substring`, `Decode String`, `Calculator`

---

Great! You're now working with a **correct version** of the `reverseWords()` function. Here's a full breakdown of the **corrections** and **notes** made step-by-step from the **initial code to the final working version**:

---

### ✅ 🔁 Initial Code (Buggy Version)

```cpp
while (i > 0) {
    while (i > 0 && s[i] == ' ') i--;
    end = i;
    while (i > 0 && s[i] != ' ') i--;
    st = i;
    for (int i = st; i <= end; i++) {
        str += s[i];
    }
    i--;
}
```

### ❌ Problems in Initial Code:

| 🔴 Issue                     | 🔍 Explanation                                                                          |
| ---------------------------- | --------------------------------------------------------------------------------------- |
| `while(i > 0)`               | Skips `s[0]` (first character), missing the first word. Should be `i >= 0`.             |
| `st = i;`                    | This includes a space before the word. Correct is `st = i + 1`.                         |
| `for(int i = st...)`         | Reuses loop variable `i` (outer loop's `i` gets overwritten). Leads to **logic error**. |
| No space between words       | All words are concatenated with **no space**.                                           |
| No check for multiple spaces | Doesn't handle leading/trailing/multiple spaces properly.                               |

---

### ✅ Changes We Made — Step-by-Step:

#### 1. **Fix Loop Condition:**

```diff
- while(i > 0)
+ while(i >= 0)
```

**Why:** We must also process the character at index `0`.

---

#### 2. **Correct Start Index (`st`) of Word:**

```diff
- st = i;
+ st = i + 1;
```

**Why:** After inner loop ends, `i` points to the space before the word. We need to start **1 step ahead**.

---

#### 3. **Avoid Variable Shadowing:**

```diff
- for(int i = st; i <= end; i++)
+ for(int j = st; j <= end; j++)
```

**Why:** Using `int i` again overwrites the main loop’s `i`. That causes wrong navigation in the outer loop.

---

#### 4. **Add Space Between Words (Using Flag):**

```cpp
bool firstWord = true;
...
if (!firstWord) {
    str += ' ';
}
...
firstWord = false;
```

**Why:** So we don’t add a space before the first word, but do for the rest.

---

#### 5. **Optional Cleanup (Not Always Needed):**

```cpp
if (!str.empty() && str.back() == ' ') {
    str.pop_back();
}
```

**Why:** Just in case a trailing space sneaks in. But not needed if space logic is handled perfectly.

---

### ✅ Final Working Code:

```cpp
class Solution {
public:
    string reverseWords(string s) {
        string str = "";
        int st, end;
        int i = s.length() - 1;
        bool firstWord = true;

        while (i >= 0) {
            while (i >= 0 && s[i] == ' ') i--;
            end = i;
            if (i < 0) break;
            while (i >= 0 && s[i] != ' ') i--;
            st = i + 1;

            if (!firstWord) str += ' ';
            for (int j = st; j <= end; j++) {
                str += s[j];
            }
            firstWord = false;
            i--;
        }
        if (!str.empty() && str.back() == ' ') {
            str.pop_back();
        }

        return str;
    }
};
```

---

### ✅ Example Input & Output:

#### Input:

```cpp
"  hello   world  "
```

#### Output:

```cpp
"world hello"
```

---

### 🧠 Summary of All Key Fixes:

| Fix                       | Description                                    |
| ------------------------- | ---------------------------------------------- |
| ✅ Loop condition `i >= 0` | To include all characters                      |
| ✅ Correct `st = i + 1`    | To start exactly at word                       |
| ✅ Avoid shadowing `i`     | Use `j` in inner loop                          |
| ✅ Add space between words | Use `firstWord` flag                           |
| ✅ Clean, reliable logic   | Handles multiple, trailing, and leading spaces |

---




# Remove All Occurrences of a Substring

#include <iostream>
#include <string>
using namespace std;

string removeOccurrences(string s, string part) {
    while (!s.empty() && s.find(part) < s.length()) {
        // Find the first position where 'part' occurs
        int pos = s.find(part);

        // Remove 'part' from that position
        s.erase(pos, part.length());
    }
    return s;
}

int main() {
    string s = "daabcbaabcbc";
    string part = "abc";

    string result = removeOccurrences(s, part);
    cout << "Result: " << result << endl;  // Output: dab

    return 0;
}


1. while (!s.empty() && s.find(part) < s.length())
Loop continues as long as:

String s is not empty, and

part is found in s

✅ s.find(part) returns:

The starting index if found

string::npos (a big number) if not found

So s.find(part) < s.length() → checks if it's valid.

2. int pos = s.find(part);






---

# ✅ Question: permutation in string 

> Given two strings `s1` and `s2`, return `true` if `s2` contains a **permutation** of `s1`, else return `false`.

---

# ✅ Your Code:

```cpp
class Solution {
public:
    bool issamefreq(int freq1[], int freq2[]) {
        for (int i = 0; i < 26; i++) {
            if (freq1[i] != freq2[i]) {
                return false;
            }
        }
        return true;
    }

    bool checkInclusion(string s1, string s2) {
        int freq[26] = {0};
        for (int i = 0; i < s1.length(); i++) {
            freq[s1[i] - 'a']++;
        }

        int winsize = s1.length();

        for (int i = 0; i < s2.length(); i++) {
            int windfreq[26] = {0};
            int idx = i;
            int winidx = 0;

            while (winidx < winsize && idx < s2.length()) {
                windfreq[s2[idx] - 'a']++;
                idx++;
                winidx++;
            }

            if (issamefreq(freq, windfreq)) {
                return true;
            }
        }

        return false;
    }
};
```

---

# ✅ Explanation

### 🧠 Idea:

* A **permutation** of `s1` must have the **same frequency** of characters.
* So, slide a **window of size `s1.length()`** over `s2`, and compare character frequencies.

---

### 🔄 Step-by-step:

1. **Count frequency of all characters** in `s1` → `freq[26]`.

2. Use a **loop on `s2`**, and for each index `i`, do:

   * Create a **new frequency array `windfreq[26]`** for window of size `winsize`.
   * Use a nested loop (`while`) to collect frequency of current window substring starting at `i`.

3. After creating `windfreq`, call `issamefreq()` to compare with `s1`'s frequency.

4. If match found → return `true`.

5. If loop finishes with no match → return `false`.

---

## ⚠️ Drawbacks in Your Code

| Issue                                                                     | Why it matters                                       |
| ------------------------------------------------------------------------- | ---------------------------------------------------- |
| `windfreq[26]` recreated in every iteration                               | O(n×26) extra memory repeatedly                      |
| Not using true sliding window                                             | Less efficient: recalculating whole window each time |
| Outer loop runs till `s2.length()` instead of `s2.length() - winsize + 1` | May check incomplete windows at the end              |

---

# ⏱ Time and Space Complexity

## ✅ Time Complexity:

```cpp
O((n - m + 1) × 26) = O(n × 26) ≈ O(n)
```

* `n = s2.length()`
* `m = s1.length()`
* For each starting index `i` in `s2`, you:

  * create a fresh frequency array of size 26 → O(26)
  * compare with original → O(26)

### So: `O(n × 26)` → **efficient in practice**

---

## ✅ Space Complexity:

```cpp
O(26 × 2) = O(1)
```

* 2 frequency arrays of size 26: `freq[26]`, `windfreq[26]`
* All fixed-size → space is constant

---

# ✅ Example Walkthrough

```cpp
s1 = "ab", s2 = "eidbaooo"

→ freq = [1 for a, 1 for b]

→ Slide window of size 2 over s2:
   - "ei" → freq mismatch ❌
   - "id" → ❌
   - "db" → ❌
   - "ba" → ✅ match → return true
```

---

# ✅ Summary

| Aspect             | Value                                                      |
| ------------------ | ---------------------------------------------------------- |
| ✅ Correctness      | Yes                                                        |
| ✅ Time Complexity  | O(n × 26) = O(n)                                           |
| ✅ Space Complexity | O(1)                                                       |
| ⚠️ Optimization    | Could avoid recalculating window freq using sliding window |

---




# String Compression




Great work! You've implemented the **String Compression** problem as asked in **Leetcode 443**.

Let’s now:

1. ✅ Explain your code step-by-step
2. ✅ Show an example
3. ✅ Give time and space complexity
4. ✅ Suggest small improvements if needed

---

## ✅ Problem Statement:

> Given a vector of characters `chars`, compress it **in-place** by replacing groups of repeated characters with the character followed by the count (if >1), and return the new length.

---

## ✅ Your Code (Well-Written):

```cpp
class Solution {
public:
    int compress(vector<char>& chars) {
        int idx = 0; // position to write compressed result
        int i = 0;   // pointer to scan input

        while (i < chars.size()) {
            int ch = chars[i]; // current character
            int count = 0;

            // count how many times ch is repeated
            while (i < chars.size() && ch == chars[i]) {
                count++;
                i++;
            }

            chars[idx] = ch; // write the character
            idx++;

            if (count > 1) {
                string str = to_string(count); // convert count to string
                for (auto it : str) {
                    chars[idx] = it; // write each digit of count
                    idx++;
                }
            }
        }

        chars.resize(idx); // remove extra chars
        return idx;
    }
};
```

---

## 🔍 Example Dry Run

**Input:**

```cpp
chars = ['a','a','b','b','c','c','c']
```

**Steps:**

| Current Char | Count | Output so far               |
| ------------ | ----- | --------------------------- |
| `'a'`        | 2     | `['a','2']`                 |
| `'b'`        | 2     | `['a','2','b','2']`         |
| `'c'`        | 3     | `['a','2','b','2','c','3']` |

**Return:** `6`
**Modified Vector:** `['a','2','b','2','c','3']`

---

## ✅ Time & Space Complexity

| Metric     | Value                                          |
| ---------- | ---------------------------------------------- |
| Time (TC)  | **O(n)** — One pass through the input          |
| Space (SC) | **O(1)** — In-place (ignoring output resizing) |

---

## ✅ Improvements (Minor)

1. **Use `char ch = chars[i];`** instead of `int ch = chars[i];` — avoid unnecessary promotion.
2. `chars.resize(idx);` is optional if question doesn’t require shrinking vector size.

### Modified line:

```cpp
char ch = chars[i];  // instead of int ch
```

---

## ✅ Final Thoughts

* Your logic is **correct** ✅
* Your code is **clean and efficient** ✅
* Used `to_string(count)` + digit-wise insertion correctly ✅










Got it 👍 You want **short notes / explanations** for all the questions you asked so far.
Here’s a clean collection of **problem + solution approach notes** for revision.

---

## **1. Count frequency of characters in array**

**Problem:**
Given a char array, count occurrences of each character.

**Key Points:**

* Use `unordered_map<char,int>` for frequency.
* Must include `<unordered_map>` (not `<map>`).
* Output of `unordered_map` is unsorted; use `map` if sorted output is required.

**Code Sketch:**

```cpp
unordered_map<char,int> mp;
for(char c: arr) mp[c]++;
for(auto it: mp) cout << it.first << " :: " << it.second << endl;
```

---

## **2. Remove all occurrences of `'a'` from char array**

**Problem:**
Given `arr = {a,a,b,c,d,a,a,e,f,a,a}`, remove all `'a'` in-place (no extra space).

**Key Points:**

* Use **two-pointer technique**:

  * `i` = read pointer
  * `j` = write pointer
* Copy non-`a` characters forward.
* Null-terminate (`'\0'`) at new end.

**Code Sketch:**

```cpp
int j=0;
for(int i=0; arr[i]!='\0'; i++)
    if(arr[i] != 'a') arr[j++] = arr[i];
arr[j] = '\0';
```

---

## **3. Your swap-based approach (remove `'a'`)**

**Problem:**
You wanted to solve it with `swap`.

**Key Points:**

* Keep `j` as the position for valid characters.
* Whenever `arr[i] != 'a'`, swap with `arr[j]`, then increment `j`.
* Works but order may change slightly.

**Code Sketch:**

```cpp
int j=0;
for(int i=0; arr[i]!='\0'; i++)
    if(arr[i] != 'a') swap(arr[i], arr[j++]);
arr[j] = '\0';
```

---

## **4. Partition int array with condition (>25 first)**

**Problem:**
Given `arr = {120, 23, 4, 32, 19, 43, 10, 8}`, bring numbers >25 to front.

**Key Points:**

* Same two-pointer idea.
* If `arr[i] > 25`, swap it forward to index `j`.
* After loop, all `>25` values are at the start.

**Code Sketch:**

```cpp
int j=0;
for(int i=0;i<n;i++)
    if(arr[i] > 25) swap(arr[i], arr[j++]);
```

---

## **5. Remove elements ≤ 25 from int array**

**Problem:**
Instead of rearranging, completely remove numbers ≤25.

**Key Points:**

* Use overwrite method instead of swap.
* Keep only elements satisfying the condition.
* New size = `j`.

**Code Sketch:**

```cpp
int j=0;
for(int i=0;i<n;i++)
    if(arr[i] > 25) arr[j++] = arr[i];
```

---

### 🔑 General Concepts Learned

* **Two-pointer technique** is the go-to approach for *removal without extra space*.
* **Swap method** partitions the array (good for separating values).
* **Overwrite method** compacts the array (good for deletion).
* Strings (`char[]`) need `'\0'` termination; integer arrays don’t.
* `unordered_map` vs `map`: unordered → fast but unsorted; map → sorted.

---

Would you like me to make these notes in a **tabular format (Problem | Approach | Key Code)** so it’s even easier for quick revision?
