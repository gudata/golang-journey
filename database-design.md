# Coupons Client

## Case 1
Our application generates a code.

The code will be random.

We generate : 12001031034{VALIDATION_NUMBERS}
And have simple checksum to check that we have validated the code (out of scope)
We have to make sure that each code will be used only once.

Solutions:

used_promocodes
----------------
code string
order_id

## Case 2

We have to print 10000 codes.
Each code can be used only one time

codes
----------------
code string
status bool
order_id


## Case 3

We have to print 10000 codes.
Each code can be used only one time but only with registered users
Each user can use one code one time!

codes
----------------
code string
user_id
used_at datetime
order_id

users
----------------

## Case 4

We have to print 10000 codes.
Each code can be used 3 times by the same registered user.

codes
----------------
code string
user_id (cached)
count byte (cached)

code_users
----------------
user_id
code_id
order_id
used_at datetime

users
----------------

Events
-----------
code_id
user_id
created_at
state (wrong code, success, fail)
description .....
