# FuzzCoupons
A list of common coupon codes for fuzzing checkout pages.

Had a need to fuzz a promo code field for valid inputs recently, and was surprised that I couldn't find an existing list. So I generated this one.

Not based off of any analytics or other data, just coupons I've seen around the net over the years. Holidays, buzzwords, etc. Suffixes range from the year 1900 to 2100 (i.e. `Xmas1998`).

Included are the hashcat rules I used to generate the list. If you add any buzzwords to either list (`coupons_noyear.txt` only gets permuted to upper/lower/title casing, `coupons_addyear.txt` gets two- and four-digit years appended to the end as well as permuted casing), you will need to regenerate the list.

To regenerate the list, in the `files` directory:
* `hashcat -r luc.rule -r year.rule --stdout coupons_addyear.txt >> temp.txt`
* `hashcat -r luc.rule --stdout coupons_noyear.txt >> temp.txt`
* `cat temp.txt | sort -u > fuzzcoupons.txt`

