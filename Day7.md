# 哈希表 part 2
## 454.四数相加II
同样使用map解决，因为需要同时记录元素和其出现的次数

### 小技巧
可以通过 `getOrDefault`方法来快速解决需要先判断`containsKey`再`put`的情况，例如：

```
if (map.containsKey(key)) {
    map.put(key, map.get(key) + 1);
} else {
    map.put(key, 1);
}
```

可以简化为：

```
map.put(key, map.getOrDefault(key, 0) + 1);
```

## 383.赎金信
以下是我的解法：

```
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        Map<String, Integer> chars = new HashMap<>();
        for (int i=0; i < magazine.length(); i++){
            String s = String.valueOf(magazine.charAt(i));
            chars.put(s, chars.getOrDefault(s, 0) + 1);
        }
        for (int j=0; j<ransomNote.length(); j++){
            String note = String.valueOf(ransomNote.charAt(j));
            if(chars.getOrDefault(note, 0) - 1 < 0){
                return false;
            } else{
                chars.put(note, chars.getOrDefault(note, 0) - 1);
            }
        }
        return true;
    }
}
```

为何map不是最优解：

其实在本题的情况下，使用map的空间消耗要比数组大一些的，因为map要维护红黑树或者哈希表，而且还要做哈希函数，是费时的！数据量大的话就能体现出来差别了。 所以数组更加简单直接有效！

## 15.三数之和
更适合用双指针法，因为哈希法难以去重。
难点在于去重的逻辑判断。

## 18.四树之和
在三数之和的基础上在增加一段循环来遍历第四个数，难点在于剪枝和去重。