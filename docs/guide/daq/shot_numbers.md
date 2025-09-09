# Shot numbers

You will need to "design" your shot numbers. Take time to carefully think through this topic because whatever scheme you decide upon will be used for all shots of your experiment and it is incredibly difficult to change once you have begun saving shots. It can be useful to encode the date into your shot number for easy reference, however this is not required. Examples:

* For CMOD, shot numbers looked like `210731123`, which corresponds to 2021-07-31 Shot #123.
* Alternatively you can simply increment shots numbers (00001, 00002, etc.), which will require you to separately keep track of date and time information.

Important notes:
* shot numbers are 32-bit signed integers
* Any negative shot numbers will be interpreted as the model.
* The maximum shot number you can have is 2,147,483,647 (`MAX_INT32`). If you try to encode the date with the four-digit year into it, you will see that this will not fit (20210731123 or 20,210,731,123 > 2,147,483,647), so your scheme will need to work around this limitation.

You can also make up some other numbering scheme that makes sense for your specific situation.
