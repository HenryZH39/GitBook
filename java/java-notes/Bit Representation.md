# Bit Representation
### 1. Basic
- [Reference Read](https://www.cs.uaf.edu/courses/cs301/2014-fall/notes/bits-bitwise/)
- Tips for [32 bit representation](https://www.geeksforgeeks.org/swap-all-odd-and-even-bits/#:~:text=The%20number%200xAAAAAAAA%20is%20a,Right%20shift%20all%20even%20bits.) :
  - Initialize variable even_bits with bitwise and of N with 0xAAAAAAAA(32 bit number with all even bits set as 1 and all odd bits as 0). 
  - Initialize variable odd_bits with bitwise and of N with 0x55555555. The number 0x55555555 is a 32 bit number with all odd bits set as 1 and all even bits as 0. 
### 2. Operations
- 最左一位是符号位(most significant bit) 0: positive 1 : negative
	<br>3 :  0011
	<br>-3 : 取反 + 1
	<br>1100 + 1 = 1101 --- (-3)

- &  and: 保留相同的部分
	<br>n & (n – 1) 消除n二进制中最后一个1 also check is power of 2 or not
	<br>n & 1

- ^  xor: 保留不同的部分
	<br>int x = -1;  y = 2;
	<br>x ^ y = (1101 in bitwise) -3

- << left shift 右侧补0
	<br>3 : 0011
	<br>X = 3 << 2  (001100) = 3 * 2 * 2 = 12

-  *>>* right shift 正数在左侧补0， 负数在左侧补1
	<br>3 : 0011
	<br>X = 3 >> 2 (0000 ~~11~~)  = 0

- ~ not : 取反 1 -> 0, 0 -> 1
	<br>X = 3 (0011)
	<br>~ x = (1100)

- | or : keep all 1
	<br>2 | 1 == 3
	<br>0010 | 0001 = 0011
