---
layout: post
title: "About enums"
date: 2023-05-16
tags:
 - [languages]
 - [enums]
 - [php]
published: true
---

Some links:

- xxxx - https://github.com/Crell/enum-comparison
- Larry garfield -
```
Comparison with enums in differents languages
```

2022 - https://peakd.com/hive-168588/@crell/on-the-use-of-enums
- Larry garfield -

2022 - https://peakd.com/hive-168588/@crell/much-ado-about-null
- Larry garfield -
```
#Interesting approach to use enums for check result of a functions (bottom post)

$product = getProduct($someInt);

match ($product) {
   RepositoryError::NoRecordFound => /* error handling */,
   RepositoryError::ProductNotYetReleased => /* error handling */,
   default => /* It's a Product, the success case */
};

```

2022 - https://www.linkedin.com/pulse/designing-php-81-enumeration-stefano-fago?trk=public_post
- Stefano Fago - 
```
Many way to use enums in php 
```
2021 - https://slides.com/girgias/reflection-algebraic-data-types-for-mortals#/4/4
- girgias - 
```
Sum type examples Enumerations, aka Enums Pattern matching
```

2022 - https://www.infoq.com/articles/php8-classes-enums/
- Deepak Vohra - 

2020 - https://externals.io/message/112417 - [RFC] Enumerations
2020 - https://externals.io/message/112626 - [RFC] Enumerations, Round 2 
- Php groups -
```
# Enums without enum keyword
final class Heart {}
final class Clubs {}
final class Spades {}
final class Diamond {}

final class Suit {
public function __construct(private Heart|Clubs|Spades|Diamond $value) {}
public function value() { return $this->value; }
}
```

2020 - https://wiki.php.net/rfc/enumerations
- Larry garfield -


Various:
- Stateful enums are called tagged unions,

