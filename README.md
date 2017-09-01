# corrections-for-HCFP-$3^{rd}$.ed

Correction for HCFP 3rd edition's chinese translation:

I think **ONLY CHINESE READERS** may need this patch file, so the following part will all be **CHINESE EXPLANATION**.

PLEASE NOTE THAT `GITHUB` DO NOT SUPPORT `mathjax.js` FOR MATH FORMULA, SO PLEASE USE THE `README.pdf` FOR CORRECTION.

- P78, `4.22习题`, "有一个以上的值为0"，根据英文版本应该是"有一个及以上"。

   （虽然也能做，根据我的[解题记录](https://github.com/tonyfloatersu/solution-haskell-craft-of-FP/blob/master/Chapter_4_my_note.hs)里面的函数

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

   似乎是可以办到的）

- P94, `data People = People Name Age` $\to$ `data People = Person Name Age` 

   构造类型的构造函数名写错

   否则和同页的`Person "Ronnie" 14` 相矛盾

- P149, 7.22习题, "函数取一个列表作为参数", 但是根据代码, 这里应该是取一个列表二元组。

