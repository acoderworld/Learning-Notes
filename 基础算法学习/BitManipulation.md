### 二进制奇淫技巧：

1、[快速判断是否为2的次方](https://leetcode.com/problems/power-of-two/description/)
*解题思路：列举2的次方并转为二进制，如：2=10，4=100，8=1000...
观察可发现一个数若为2的次方，转为二进制时，所有bit上只会存在一个1.
n & (n - 1) 消除最后一位1 如：4(100) & 3(11) = 0*

```
	public boolean isPowerOfTwo(int n) {
       return num > 0 && (num & (num - 1)) == 0;
    }
```
2、[快速判断是否为4的次方](https://leetcode.com/problems/power-of-two/description/)
**解题思路：***列举4的次方并转为二进制，如：4=100，16=10000，64=1000000...*
*观察可发现一个数若为4的次方，转为二进制时，所有bit上有且只有1个1，并且末尾跟随偶数为0，故可在判断为2的次方上，再判断末尾是否存在偶数位0即可.*

```
    public boolean isPowerOfFour(int num) {
	    if (num <= 0) {
	        return false;
	    }
	    if ((num & (num - 1)) != 0) {
	        return false;
	    }
	    int count = 0;
	    num = num - 1;
	    while (num != 0) {
	        count ++;
	        num = num & (num - 1);
	    }
	    return count % 2 == 0;
	}
```
**优化：***判断是否存在偶数为0，也可使用 num & 0x55555555(1010101010101010101010101010101) != 0判断*

```
	public boolean isPowerOfFour(int num) {
        return num > 0 && (num & (num - 1)) == 0 && (num & 0x55555555) != 0;
    }
```


