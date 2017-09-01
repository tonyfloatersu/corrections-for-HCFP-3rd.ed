# corrections-for-HCFP-$3^{rd}$.ed

Correction for HCFP 3rd edition's Chinese translation:

I think **ONLY CHINESE READERS** may need this patch file, so the following part will all be **CHINESE EXPLANATION**.

PLEASE NOTE THAT `GITHUB` DO NOT SUPPORT `mathjax.js` FOR MATH FORMULA, SO PLEASE USE THE `README.pdf` FOR CORRECTION.

- `P78`, `4.22习题`, "有一个以上的值为0"，根据英文版本应该是"有一个及以上"。

   （虽然也能做，根据我的[解题记录](https://github.com/tonyfloatersu/solution-haskell-craft-of-FP/blob/master/Chapter_4_my_note.hs)里面的函数似乎是可以办到的）

   ```haskell
   boolTestingStructure :: (Integer -> Integer) -> Integer -> Integer -> Bool
   boolTestingStructure tf bd1 bd2
       | zeroCounter tf bd1 bd2 > 1    = True
       | otherwise                     = False
     where
       zeroCounter :: (Integer -> Integer) -> Integer -> Integer -> Integer
       zeroCounter tf' bd1' bd2'
           | bd1' > bd2'     = zeroCounter tf' bd2' bd1'
           | bd1' == bd2'    = judger tf' bd1'
           | otherwise       = judger tf' bd1' + zeroCounter tf' (bd1' + 1) bd2'
         where
           judger :: (Integer -> Integer) -> Integer -> Integer
           judger tempf bd
               | tempf bd == 0      = 1
               | otherwise          = 0
   ```

- ​`P94`, `data People = People Name Age`  :arrow_right:  `data People = Person Name Age` 

   构造类型的构造函数名写错

   否则和同页的`Person "Ronnie" 14` 相矛盾

- `P149`, `7.22习题`, "函数取一个列表作为参数", 但是根据代码, 这里应该是取一个列表二元组。

   ```Haskell
   zip' :: ([a], [b]) -> [(a, b)]
   zip' (xs, ys)    = zip xs ys
   ```

- `P215`, `11.12习题`, `filter (>).map (+ 1)` 肯定是有误，因为 `filter` 的函数签名是

   ```haskell
   filter :: (a -> Bool) -> [a] -> [a]
   ```

   所以输入`filter`的函数只能有一个变量输入, `(>)` 是不合适的。

- `P218`, 页顶的`unzip` 写错了，函数签名应为

   ```Haskell
   unzip :: [(a, b)] -> ([a], [b])
   ```

   却写成  

   ````haskell
   unzip :: ([a, b]) -> ([a], [b])
   ````

- `P433`, 页顶

   ```haskell
   newtype MP ab = MP { mp :: (Parse a b) }
   ```

   应为

   ```haskell
   newtype MP a b = MP { mp :: (Parse a b) }
   ```

- `P434`, 页顶

   ```haskell
   instance Monad Identity where
       (Identity x) >>= f      = f x -- x >>= f = f x
   ```

   ​

