# HashMap (Hashing) – Complete DSA Notes

# 1️⃣ What is a HashMap?
A HashMap (Dictionary in Python) is a data structure that stores data in key → value pairs.
It allows:
* Insert → O(1)
* Search → O(1)
* Delete → O(1)
# 2️⃣ Why Do We Use HashMap?
We use HashMap when we need:
* Fast lookup
* Frequency counting
* Checking duplicates
* Storing indices
* Tracking prefix sums
* Grouping similar items
Instead of scanning the entire array repeatedly (O(n)),
we store information once and reuse it in O(1).
# 3️⃣ Basic Operations in Python
### Insert
d[key] = value

### Access
value = d[key]

### Safe Access
value = d.get(key, default_value)

### Check Existence
if key in d:

### Delete
del d[key]

# 4️⃣ Common HashMap Patterns in DSA
# 🔹 Pattern 1: Frequency Counting
Used when:
* Count occurrences
* Find duplicates
* Majority element
* Anagram problems
### template:

freq = {}
for num in nums:
    freq[num] = freq.get(num, 0) + 1
### Example
Input:
nums = [1,2,2,3,1,1]
Output:
{1:3, 2:2, 3:1}

# 🔹 Pattern 2: Seen Before (Lookup Pattern)
Used when:
* Two Sum
* Contains Duplicate
* Check if pair exists
### template:

seen = {}
for i, num in enumerate(nums):
    complement = target - num
    if complement in seen:
        return [seen[complement], i]
    seen[num] = i

Key Idea:
Store what you've seen so far.

# 🔹 Pattern 3: Prefix Sum + HashMap (VERY IMPORTANT)
Used in:
* Subarray sum equals k
* Longest subarray with sum k
* Count subarrays divisible by k
### Core Logic
If:
current_prefix - previous_prefix = k
Then:
previous_prefix = current_prefix - k
So we store prefix sums.

### template
prefix = 0
count = 0
hashmap = {0: 1}
for num in nums:
    prefix += num
    if prefix - k in hashmap:
        count += hashmap[prefix - k]
    hashmap[prefix] = hashmap.get(prefix, 0) + 1
return count

Important:
We initialize `{0:1}` to handle cases where prefix itself equals k.

# 🔹 Pattern 4: Sliding Window + HashMap
Used when:
* Longest substring without repeating characters
* At most K distinct elements
* Minimum window substring
### Template
left = 0
seen = set()
for right in range(len(s)):
    while s[right] in seen:
        seen.remove(s[left])
        left += 1
    seen.add(s[right])

Key Idea:
HashMap tracks elements inside current window.

# 🔹 Pattern 5: Grouping (Bucket Pattern)
Used when:
* Group anagrams
* Group similar elements
### Template

from collections import defaultdict
groups = defaultdict(list)
for word in strs:
    key = "".join(sorted(word))
    groups[key].append(word)
return list(groups.values())

Key Idea:
Create a key that represents similarity.

# 5️⃣ HashSet vs HashMap
| Use Case               | Use  |
| ---------------------- | ---- |
| Only existence matters | set  |
| Need frequency / index | dict |

# 6️⃣ Time & Space Complexity

| Operation | Average Time |
| --------- | ------------ |
| Insert    | O(1)         |
| Search    | O(1)         |
| Delete    | O(1)         |

Worst case (rare collisions): O(n)
Space Complexity:
O(n)

# 7️⃣ Common Interview Mistakes

❌ Forgetting to initialize `{0:1}` in prefix sum
❌ Using sliding window when array contains negatives
❌ Recomputing sum repeatedly (O(n²))
❌ Not updating hashmap frequency correctly

# 8️⃣ How To Identify HashMap Problems
If question says:
* “Count”
* “Frequency”
* “Duplicate”
* “Pair”
* “Subarray sum”
* “Distinct”
* “Group”
* “Lookup”
→ Think HashMap.

# 9️⃣ Summary
HashMap helps to:
* Avoid repeated work
* Reduce O(n²) → O(n)
* Store past information
* Track frequencies
* Solve prefix sum problems
Hashing is one of the most important topics in DSA and appears in almost every coding interview.

Tell me what you want next for your GitHub repo 🚀
