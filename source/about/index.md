---
title: About Free Monad
date: 2019-11-14 00:02:39
widgets:
---

# Free Monad

Free monad allows us to construct a monad from a functor:
```haskell
data Free f r = Free (f (Free f r)) | Pure r
```

```haskell
instance (Functor f) => Monad (Free f) where
  return = Pure
  Pure a >>= k = k a
  Free m >>= k = Free ((>>= k) <$> m)
```

> Free Monad gives you a free monad for a given functor.
