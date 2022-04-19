# FuzzCoupons

A list of common coupon codes for fuzzing checkout pages.

Had a need to fuzz a promo code field for valid inputs recently, and was surprised that I couldn't find an existing list. So I generated this one.

Based off of [CouponShare's 100 Most Common Coupon Codes](https://www.slideshare.net/CouponFollow/top-100-most-common-coupon-code-phrases), which looks to have been published in 2011. I've also added a significant chunk of promo codes from my own experience and some light research on coupon sharing websites. Holidays, buzzwords, etc. Suffixes range from the year 1900 to 2100 (i.e. `Xmas1998`).

Included are the hashcat rules I used to generate the list. Hashcat will add two and four digit years, and also permute letter casing for the enitre word and the first letter.

To regenerate the list, in the `files` directory:
* `hashcat -r luc.rule -r year.rule --stdout words.txt -o fuzzcoupons.txt`

You should also add bare years (like `1980` or `2007`) with this simple `seq`:
* `seq 1900 2100 >> fuzzcoupons.txt`