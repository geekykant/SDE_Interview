# Recursion - Basic Notes

Recursion is a function which calls itself. It's added up in memory as stacks and is generally used to write codes that has loops.
DP & Backtracking makes use of recusion as the fundamentals to proceed with solutions.

**Tail-Recursive** - is said when the recursive call is the last in the function. This means the parent function control need not be handled back after recursion from child.
- **Tail call elimation** is used where the recusion is replaced with **goto** and **start* keywords as modified loop.

#1. Count from N to 1 (Tail Recursive)

```cpp
void fun(int n) {
	if (n == 0) return;

	cout << n;
	fun(n - 1);
}
```

**After Tail Elimination**
```cpp
void dec(int n) {
start:
	if (n == 0) return;

	cout << n;
	n = n - 1;
	goto start;
}
```

#2. Count from 1 to N

```cpp
void fun(int n) {
	if (n == 0) return;

	fun(n - 1);
	cout << n;
}
```
**Better code (with T-Elimination)**
```cpp
void fun(int n, int k = 1) {
	if (n == 0) return;

	cout << k;
	fun(n - 1, k + 1);
}
```

#3. Factorial of a number

```cpp
int fact(int n, int val = 1) {
	if (n == 0) 
		return val;

	return fact(n - 1, n * val);
}
```

#4. Check for palindrome

```cpp
bool isPalindrome(string s, int start, int end) {
	if (start >= end) return true;

	if (s[start] != s[end])
		return false;

	return isPalindrome(s, start + 1, end - 1);
}
```

#5. Sum of digits of Number - Recursion 
```cpp
int digitsSum(int num, int sum = 0) {
	if (num == 0)
		return sum;

	return digitsSum(num / 10, num % 10 + sum);
}
```

#6. Find nCr

```cpp
float ncr(float n, float c) {
	if (c == 1) 
		return n;
	return n * ncr(n - 1, c - 1) / c;
}
```
