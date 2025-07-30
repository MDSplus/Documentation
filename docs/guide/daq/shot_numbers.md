
# Shot numbers

You will need to "design" your shot numbers. Whatever scheme you decide will be used for all shots of your experiment and is incredibly difficult to change once begun. It can be useful to encode the date into your shot number for easy reference, however this is not required. Examples:

* For CMOD, shot numbers looked like `210731123`, which corresponds to 2021-07-31 #123.
* Alternatively you can simply increment (00001, 00002, etc.), which will require you to keep track separately of when shots occurred. 

Be warned: shot numbers are 32-bit signed integers and all negative shots will be interpreted as the model. 2,147,483,647 (`MAX_INT32`) is the maximum shot number you can have. If you try to encode the date with the four-digit year into it, you'll see that it won't fit (20220731123 or 20,220,731,123 > 2,147,483,647.)

You can also make up some other scheme that makes sense to you.
