both [![Build Status][build-status]][build-log]
====

The Monoid instance for Maybe behaves like so:

~~~~{.haskell}
instance Monoid a => Monoid (Maybe a) where
  mappend (Just x) (Just y) = Just $ x <> y
  mappend (Just x) Nothing  = Just x
  mappend Nothing  (Just y) = Just y
  mappend Nothing  Nothing  = Nothing

  mempty = Nothing
~~~~

Both is a newtype wrapper around Maybe providing this instance:

~~~~{.haskell}
instance Monoid a => Monoid (Both a) where
  mappend (Just x) (Just y) = Just $ x <> y
  mappend _ _ = Nothing

  mempty = Just mempty
~~~~

The documentation of the latest developmental version is
[available online][docs].

Contributing
------------

Bug reports, pull requests, and comments are very welcome!

Feel free to contact me on GitHub, through IRC (#haskell on freenode),
or email (mike@barrucadu.co.uk).

[build-status]: https://travis-ci.org/barrucadu/both.svg?branch=master
[build-log]:    https://travis-ci.org/barrucadu/both
[docs]:         https://docs.barrucadu.co.uk/both
