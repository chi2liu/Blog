# 题目
在数据结构中，哈希函数是用来将一个字符串（或任何其他类型）转化为小于哈希表大小且大于等于零的整数。一个好的哈希函数可以尽可能少地产生冲突。一种广泛使用的哈希函数算法是使用数值33，假设任何字符串都是基于33的一个大整数，比如：
hashcode("abcd") = (ascii(a) * 333 + ascii(b) * 332 + ascii(c) *33 + ascii(d)) % HASH_SIZE 
                              = (97* 333 + 98 * 332 + 99 * 33 +100) % HASH_SIZE
                              = 3595978 % HASH_SIZE
其中HASH_SIZE表示哈希表的大小(可以假设一个哈希表就是一个索引0 ~ HASH_SIZE-1的数组)。
给出一个字符串作为key和一个哈希表的大小，返回这个字符串的哈希值。

**样例**
对于key="abcd" 并且 size=100， 返回 78

# 代码
```
class Solution {
    /**
     * @param key: A String you should hash
     * @param HASH_SIZE: An integer
     * @return an integer
     */
    public int hashCode(char[] key,int HASH_SIZE) {
        // write your code here
         int len = key.length;
        long hashcode = 0;
        long base = 1;
        for(int i=len-1;i>=0;i--){
            hashcode = hashcode  + Integer.valueOf(key[i])*base % HASH_SIZE;
            base = base *33% HASH_SIZE;
        }
        return (int)hashcode%HASH_SIZE;
    }
};
```

```
class Solution {
    /**
     * @param key: A String you should hash
     * @param HASH_SIZE: An integer
     * @return an integer
     */
    public int hashCode(char[] key,int HASH_SIZE) {
        // write your code here
        long ans = 0;
        for(int i = 0; i < key.length;i++) {
            ans = (ans * 33 + (int)(key[i])) % HASH_SIZE; 
        }
	return (int)ans;
    }
};
```
