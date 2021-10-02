# CS3141 19T2 Sample Exam

## Part 1

1. A partial function is a function which does not account for all types which can be passed in while a partial application is where less than the maximum number of defined arguments for a certain function are passed in.
2. Functions coverage checks how many of the defined functions have been used within use of the program. Line coverage is checking how many lines of the source code have been tested. They differ as function coverage will not check lines of code which are not used.
3. Multi-argument functions are modelled in Haskell using 'currying' which takes in one argument and returns a tupled function which can be again passed to a tupled function which can accept further arguments. This method is implicit as the brackets are made redundant with the right associativity.
4. The defined `getChar` is not a pure function as the IO type cannot guarantee that there will be no external effects.
   - `getChar` is not impure, it is not a function at all. It is instead an IO procedure.
5. The functional correctness specification is the set of properties that capture all requirements for a program. 
6. Performance is important for abstract models which are used when testing as incomputable or slow implementations will heavily affect tests run on main code and therefore not be suitable.
7. Termination is necessary for Curry-Howard correspondence otherwise we have the risk of inconsistent logic which enables false things to be proved.
8. Any correlation between a list of Stock and prices is implicit and therefore unsafe to use. A better implementation of Report is to instead be a list of tuples with types (Stock, Price) which allows the explicit coupling of Stock to price.

## Part 2

1. `[Bool] -> [Bool]`

2. The specified command takes in (:) which is a function of type (a -> b -> b), [] which is an empty list, and [1,2] which a list of two Integers.

   ```haskell
   -- foldr (:) [] [1,2]
   
   foldr (:) [] (1 : [2]) = (:) 1 (foldr (:) [] [2])
   					   = 1 : foldr (:) [] [2]
   
   foldr (:) [] (2 : [ ]) = (:) 2 (foldr (:) [])
   					   = 1 : 2 : foldr (:) [] []
   
   foldr (:) [] [] 	   = []
   					   = 1 : 2 : []
   					   = [1,2]
   ```

3. `foldr (:) []` is the identity function for lists.

4. ```haskell
   -- foldr (:) xs ys == ys ++ xs
   
   -- i.
   foldr (:) xs [] = [] : xs
   				= xs
   
   -- ii.
   {-    a) where ys = (k : ks)
   	Inductive Hypothesis about ks is foldr (:) xs ks == ks ++ xs
   -}
   --    b) prove using equational reasoning
   foldr (:) xs (k:ks) = (:) k (foldr (:) xs ks)
   					= k : foldr (:) xs ks
   					= k : (ks ++ xs)
   					= (k : ks) ++ xs
   					= ys ++ xs
   -- This is proved for ks and thus proved for ys, proving the initial statement of foldr (:) xs ys == ys ++ xs
   ```

5. $O(n)$
6. $O(n^2)$

## Part 3

1. 

   1. Each tuple element within the list must have an Integer paired with a float and the highest integer value within the tuples of this list is less than or equal to the first Integer argument given.

   2. `SV 1 [(1, 2.0), (2, 3.0)]` and `SV 3 [(0, 4.3), (2, 1.1), (2, 2.0)]`

   3. ```haskell
      wellformed :: SVec -> Bool
      wellformed SV 0 [] = True
      wellformed SV n xs = len && dups
      	where
      		len    = all (\(i,f) -> i >= 0 && i < n) xs
      		dups   = length $ nub $ map fst xs == length xs
      ```

   4. ```haskell
      vsmA :: [Float] -> Float -> [Float]
      vsmA fs f = map (* f) fs
      ```

   5. ```haskell
      vsm :: SVec -> Float -> SVec
      
      wellformed xs => wellformed (vsm xs s)
      
      expand (vsm xs s) == vsmA (expand xs) s
      ```

## Part 4

1. ```haskell
   data Role = Staff | Supplier | Customer
   newtype Person (x :: Role) = . . .
   name :: Person r -> String
   salary :: Person Staff -> String
   fire :: Person Staff -> IO ()
   company :: Person Supplier -> String
   ```

2. ```haskell
   data Vec (n :: Nat) a where
   	VNil :: Vec Z a
   	VCons :: a -> Vec n a -> Vec (S n) a
   
   zip :: Vec Nat a -> Vec Nat b -> Vec (a,b)
   zipV VNil ys = VNil
   zipV xs VNil = VNil
   zipV (VCons x xs) (VCons y ys) = VCons (x,y) (zipV xs ys)
   ```

3. 

