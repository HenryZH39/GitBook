# GCD(greatest common divisor)
```java
// Greatest common divisor of an array
 private int gcd(int[] nums) {
	int out = nums[0];
	
	for(int num : nums) {
		out = gcd(out, num);
	}
	return out;
}
//greatest common divisor of 2 numbers
private int gcd(int a, int b) {
	if (a == 0) {
		return b;
	}
	return gcd(b % a, a);
}
```