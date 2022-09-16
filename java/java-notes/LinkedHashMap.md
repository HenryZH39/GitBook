# LinkedHashMap
- <a href = "https://leetcode.com/problems/lru-cache/">146. LRU Cache </a>

LinkedHashMap  = HashMap + Double LinkedList
super(capacity, 0.75F, true);

>0.75F means 0.75 Load Factor

The Load factor is a measure that decides when to **increase** the HashMap capacity to maintain the get() and put() operation complexity of **O(1)**. The default load factor of HashMap is **0.75f** (75% of the map size).