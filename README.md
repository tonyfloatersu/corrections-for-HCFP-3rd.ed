# Corrections For HCFP (the third edition)

Correction for HCFP 3rd edition's Chinese translation:

I think **ONLY CHINESE READERS** may need this patch file, so the following part will all be **CHINESE EXPLANATION**.

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

- `P94`, `data People = People Name Age`  应该是 `data People = Person Name Age` 

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

- `P320`, 页顶, "visibe" 应为 "visible"

- `P348`, 页末, “4.5节介绍的仿真例子” 应为 ”14.5节介绍的仿真例子“

- `P349`, 页中, ”此时一个Qutemss被生成“ 应为 ”此时一个Outmess被生成”

- `P355`, 页中

   ```Haskell
   rightSub (Node -- t2) = t2
   ```

   应为

   ```haskell
   rightsub (Node _ _ t2) = t2
   ```


- `P358`, 页中

   ```haskell
   inNil t = error "indexT"
   ```

   应为

   ```haskell
   isNil t = error "indexT"
   ```

- `P359`, 页末, ”重新实现10.8的索引系统” 应为 “重新实现12.5的索引系统”

- `P362`, 页中

   ```haskell
   inter :: Ord a => Set a -> Set a -> Set a
   inter (Set xs) (Set ys) = Set (int xs ys)
   ```

   出现了两遍

- `P392`, 页末

   ```haskell
   data Expr = Lit Int | Var Var | Op Ops Expr Expr
   ```

   改为

   ```haskell
   data Expr = Lit Int | Var | Op Ops Expr Expr
   ```

- `P394`, 页末

   ```haskell
   alt :: Parse a b -> Parse a b -> Parse a b
   alt p1 p2inp = p1 inp ++ p2 inp
   ```

   改为

   ```haskell
   alt :: Parse a b -> Parse a b -> Parse a b
   alt p1 p2 inp = p1 inp ++ p2 inp
   ```

- `P396`, 页中

   ```haskell
   [] ++ [(2, "34")]
   ```

   改为

   ```haskell
   [] ++ [('2', "34")]
   ```

- `P396`, 页中

   ```haskell
   (>*>) :: Parse a b -> Parse a c -> Pare (b, c)
   ```

   改为

   ```haskell
   (>*>) :: Parse a b -> Parse a c -> Parse (b, c)
   ```

- `P430`, 页顶

   ```haskell
   (>>=) :: ma -> (a -> mb) -> mb
   ```

   改为

   ```haskell
   (>>=) :: m a -> (a -> m b) -> m b
   ```

- `P430`, 页末 “显式分隔符’:‘” 应该改为 “显式分隔符’;‘” 


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
       (Identity x) >>= f      = f x -- x >>= f = fx
   ```

   更正为

   ```haskell
   instance Monad Identity where
       (Identity x) >>= f      = f x -- x >>= f = f x
   ```

   ​


目前检查到chapter 18结束，还余下chapter 19/20。