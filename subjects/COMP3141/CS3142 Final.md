# CS3142 Final

1. wuef

2. evr

   1. `[a] -> [a]`

   2. ```haskell
      f [1,5,7] []
      f (1:[5,7]) [] = f [5,7] (1:[])
      f (5:[7]) [1] = f [7] (5:[1])
      f (7:[]) [5,1] = f [] (7:[5,1])
      f [] [7,5,1] = [7,5,1]
      ```

   3. rg

   4. ```haskell
      reverse [] = []
      reverse (x:xs) = reverse xs ++ [x]
      
      f xs ys = reverse xs ++ ys
      ```

      1. Alvin
      2. `xs == (k:ks)`
         
         1. ```haskell
            f (k:ks) ys = reverse (k:ks) ++ ys
            ```
         
         2. ```haskell
            f (k:ks) ys = reverse (k:ks) ++ ys
            			= reverse 
            ```
         
         3. 

