  
![](https://ads-servebom-com.cdn.ampproject.org/i/s/ads.servebom.com/serve_cdn/amp/amp_placeholder.png)

[How-To Geek](https://www.howtogeek.com/)[](https://www-howtogeek-com.cdn.ampproject.org/v/s/www.howtogeek.com/854749/little-known-excel-functions-that-are-actually-useful/amp/?amp_js_v=0.1#menu)[](https://www-howtogeek-com.cdn.ampproject.org/v/s/www.howtogeek.com/854749/little-known-excel-functions-that-are-actually-useful/amp/?amp_js_v=0.1#menu)

We select and review products independently. When you purchase through our links we may earn a commission. [Learn more.](https://www.howtogeek.com/about/)

# 11 Little-Known Excel Functions That Are Very Useful

![](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/thumbcache/100/100/6448fb0292691c32cc5e02a8375d270d/wp-content/uploads/2020/10/SWrittenhouse500.jpg)-   [SANDY WRITTENHOUSE](https://www.howtogeek.com/author/sandywrittenhouse/)  [@sandystachowiak](https://twitter.com/@sandystachowiak)
   
-   January 18, 2023, 12:00pm EDT

![Microsoft Excel logo on a green background](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2021/09/microsoft_excel_hero_1200x675.jpg?width=398&trim=1,1&bg-color=000&pad=1,1)

Microsoft Excel offers [hundreds of functions](https://www.howtogeek.com/761846/how-to-find-the-function-you-need-in-microsoft-excel/). So, there’s bound to be at least a handful you don’t know exist. These unique functions have specific purposes that you’ll be thrilled to learn about and use.

ADVERTISEMENT

**RELATED:** [**_12 Basic Excel Functions Everybody Should Know_**](https://www.howtogeek.com/765624/basic-excel-functions-everybody-should-know/)

## FLOOR and CEILING for Rounding

You can use the FLOOR and CEILING math [functions for rounding](https://www.howtogeek.com/820086/how-to-use-the-round-functions-in-microsoft-excel/) towards or away from zero by a specified multiple. Use FLOOR to round down and CEILING to round up.

ADVERTISEMENT

The syntax for each is `FLOOR(value, multiple)` and `CEILING(value, multiple)`where both arguments are required.

ADVERTISEMENT

To round 4.4 down to the nearest multiple of 2, you’d use the following formula:

=FLOOR(4.4,2)

![](data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http%3A//www.w3.org/2000/svg' xmlns%3Axlink='http%3A//www.w3.org/1999/xlink' viewBox='0 0 14 4'%3E%3Cfilter id='b' color-interpolation-filters='sRGB'%3E%3CfeGaussianBlur stdDeviation='.5'%3E%3C/feGaussianBlur%3E%3CfeComponentTransfer%3E%3CfeFuncA type='discrete' tableValues='1 1'%3E%3C/feFuncA%3E%3C/feComponentTransfer%3E%3C/filter%3E%3Cimage filter='url(%23b)' x='0' y='0' height='100%25' width='100%25' xlink%3Ahref='data%3Aimage/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAECAIAAAAxsZngAAAAh0lEQVQImU2MywrDIBAA/f//CkVLCGlD1dakYn1FjSZUcu7iqcMysCyziFK6Nqy1QgittffeOaeUMuMw9/3rSuQ46PsNSSlTSjFEOC/vBYLYgNhz5hl19AE2T446fDmOPYQ4fySXYmLThrvd2VJKCAEMj8BQIkzI2VhzhDHRn/ULa6313znnH9dAloEXUSKvAAAAAElFTkSuQmCC'%3E%3C/image%3E%3C/svg%3E)![FLOOR function in Excel](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/Floor-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

To round 5.6 up to the nearest multiple of 2, you’d use this formula:

=CEILING(5.6,2)

![](data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http%3A//www.w3.org/2000/svg' xmlns%3Axlink='http%3A//www.w3.org/1999/xlink' viewBox='0 0 14 4'%3E%3Cfilter id='b' color-interpolation-filters='sRGB'%3E%3CfeGaussianBlur stdDeviation='.5'%3E%3C/feGaussianBlur%3E%3CfeComponentTransfer%3E%3CfeFuncA type='discrete' tableValues='1 1'%3E%3C/feFuncA%3E%3C/feComponentTransfer%3E%3C/filter%3E%3Cimage filter='url(%23b)' x='0' y='0' height='100%25' width='100%25' xlink%3Ahref='data%3Aimage/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAECAIAAAAxsZngAAAAjElEQVQImT2M2QrDIBRE/f8fS7CQUNKaBTFG3OKKVXzupQ+dh8PMvcwgQsj9k9aaUiqlBG+MEUKo5XnO04FH4DVPiHMeQvDOW2vZyZRS3nvnHBTssdtt1eRtViJXggY8ppTgx+S1c7psr4SHrFXOGY5AGCqlwBDCD1xr7b27FO7kpTO9fiC21v4ExRi/zAOWYz6aUGAAAAAASUVORK5CYII='%3E%3C/image%3E%3C/svg%3E)![CEILING function in Excel](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/Ceiling-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

## MODE.SNGL for Finding Repetitive Values

Originally simply the [MODE function](https://support.microsoft.com/en-us/office/mode-function-e45192ce-9122-4980-82ed-4bdc34973120), Microsoft created a newer version of this statistical function for improved accuracy. Use MODE.SNGL to find a single frequently recurring number in an array or cell range.

THE BEST TECH NEWSLETTER ANYWHERE

Join **425,000** subscribers and get a daily digest of features, articles, news, and trivia.

Sign Me Up!

By submitting your email, you agree to the [Terms of Use](https://www.howtogeek.com/terms-of-use) and [Privacy Policy](https://www.howtogeek.com/privacy-policy).

ADVERTISEMENT

The syntax is `MODE.SNGL(array1, array2, ...)` where only the first argument is required. You can use numbers, names, arrays, or references that contain numbers. Use the optional argument(s) for additional cell ranges.

ADVERTISEMENT

Here, we look for the repetitive number that appears the most in cells A1 through A5.

=MODE.SNGL(A1:A5)

![](data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http%3A//www.w3.org/2000/svg' xmlns%3Axlink='http%3A//www.w3.org/1999/xlink' viewBox='0 0 11 5'%3E%3Cfilter id='b' color-interpolation-filters='sRGB'%3E%3CfeGaussianBlur stdDeviation='.5'%3E%3C/feGaussianBlur%3E%3CfeComponentTransfer%3E%3CfeFuncA type='discrete' tableValues='1 1'%3E%3C/feFuncA%3E%3C/feComponentTransfer%3E%3C/filter%3E%3Cimage filter='url(%23b)' x='0' y='0' height='100%25' width='100%25' xlink%3Ahref='data%3Aimage/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAAFCAIAAAAcxIEBAAAAcElEQVQImXWKywqAIBQF/f9f64W0qkgNMTUfLQR1odDFoF3DZRguBzHGrLVaa8751VDbegwdHB97MWO0rMt+UHEKYwxMnXMQ3ntosJQSUUprrTFFcGm88TrnjAghpZYY/xcDntRtFNuzd6kB388hhAcydJnTVCtkmwAAAABJRU5ErkJggg=='%3E%3C/image%3E%3C/svg%3E)![MODE.SNGL function for one array](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/ModeSnglArray-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

ADVERTISEMENT

To find a recurring number in A1 through A5 and C1 through C5, you’d use this formula:

=MODE.SNGL(A1:A5, C1:C5)

![MODE.SNGL function for two arrays](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/ModeSnglArrays-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

## CONVERT for Converting From One Measurement to Another

For a useful engineering function, you can [use CONVERT](https://www.howtogeek.com/819208/how-to-convert-almost-any-unit-in-microsoft-excel/) to change a value from one measurement system to another.

**RELATED:** [**_How to Convert Almost Any Unit in Microsoft Excel_**](https://www.howtogeek.com/819208/how-to-convert-almost-any-unit-in-microsoft-excel/)

The syntax is `CONVERT(value, from, to)`where you’ll need all three arguments. For the `from` and `to` arguments, you’ll use an abbreviation. Check the [Microsoft Support site for the abbreviations](https://support.microsoft.com/en-us/office/convert-function-d785bef1-808e-4aac-bdcd-666c810f9af2) you need for weight and mass, distance, time, pressure, force, energy, power, magnetism, temperature, volume, area, information, and speed.

ADVERTISEMENT

To convert the value in cell A1 from Celsius to Fahrenheit, you would use this formula:

=CONVERT(A1,"C","F")

![CONVERT function for Celsius to Fahrenheit](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/ConvertTemp-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

To convert the value in cell B1 from centimeters to inches, use this formula:

=CONVERT(B1,"cm","in")

![CONVERT function for centimeters to inches](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/ConvertLength-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

## DELTA for Testing Equal or Not Equal Values

Another engineering function that’s useful is DELTA. With it, you’ll use the [Kronecker delta](https://mathworld.wolfram.com/KroneckerDelta.html)function to test whether two values are equal. Different than the [EXACT function](https://support.microsoft.com/en-us/office/exact-function-d3087698-fc15-4a15-9631-12575cf29926), the result is either 1 (true) or 0 (false).

ADVERTISEMENT

The syntax is `DELTA(value1, value2)` where only the first argument is required and can be a number or cell reference. If you leave the second argument blank, Excel assumes zero.

ADVERTISEMENT

To test the values in cells A1 and B1, you would enter this formula:

=DELTA(A1,B1)

![DELTA function using cell references](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/DeltaCells-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

To test the values 2 and -2, use this formula:

=DELTA(2,-2)

![DELTA function using numbers](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/DeltaNumber-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

## GESTEP for Testing Greater Than or Equal To a Threshold

One more engineering function you may find useful is GESTEP which allows you to test values that are [greater than or equal to](https://www.howtogeek.com/800546/google-sheets-comparison-operators/) a step (threshold). The result is either 1 (true) or 0 (false).

ADVERTISEMENT

The syntax is `GESTEP(value, step)` where only the first argument is required and can be a number or cell reference. If you leave the second argument blank, Excel uses zero.

ADVERTISEMENT

To test the value in cell A1 against step 4, you’d use this formula:

=GESTEP(A1,4)

![GESTEP function using a cell references](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/GestepCell-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

ADVERTISEMENT

To test a value of 10 against step 12, use this formula:

=GESTEP(10,12)

![GESTEP function using a number](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/GestepNumbers-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

## ADDRESS for Finding the Location of a Cell

Let’s move on to a lookup function in Excel. To find the exact address of a cell, you can use the ADDRESS function. This is convenient if you want an error-free [reference to a cell](https://www.howtogeek.com/426633/how-to-cross-reference-cells-between-microsoft-excel-spreadsheets/).

**RELATED:** [**_How to Cross Reference Cells Between Microsoft Excel Spreadsheets_**](https://www.howtogeek.com/426633/how-to-cross-reference-cells-between-microsoft-excel-spreadsheets/)

The syntax is `ADDRESS(row, column, type, style, name)` where only the first two arguments are required. Enter the row number for the first argument and the column number for the second.

ADVERTISEMENT

The optional arguments are as follows:

-   **Type**: The type of reference to return. Use blank or 1 for absolute, 2 for absolute row and relative column, 3 for relative row and absolute column, or 4 for relative.
-   **Style**: Use TRUE for the A1 or FALSE for the R1C1 [cell reference style](https://www.howtogeek.com/227178/how-to-change-the-cell-reference-style-in-excel/).
-   **Name**: The sheet name to use for an external reference. If blank, Excel assumes the currently active sheet.

To find the address of the cell in row 2, column 3, you’d use this formula:

=ADDRESS(2,3)

![ADDRESS function in Excel](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/AddressFunction-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

ADVERTISEMENT

To find the address of the same cell using an absolute row and relative column, you’d use this formula:

=ADDRESS(2,3,2)

![ADDRESS function with an argument in Excel](https://www-howtogeek-com.cdn.ampproject.org/i/s/www.howtogeek.com/wp-content/uploads/2022/12/AddressFunctionArgument-ExcelFunctionsLittleKnown.png?trim=1,1&bg-color=000&pad=1,1)

To find the address of the same cell in the sheet named Sheet2, use the following formula. Note that the commas represent the blank arguments `type` and `style`.

=ADDRESS(2,3,,,"Sheet2")

## PI for the Value of Pi

If you need to use the value of pi for equations in your sheet, you can obtain it with the PI function.

ADVERTISEMENT

The syntax is simply `PI()` with no arguments. You can add more [elements to the formula](https://www.howtogeek.com/798325/excel-formula-structure-basics/) if you want to use the value for a calculation.

ADVERTISEMENT

To return the value of pi, simply use the function’s formula including the parentheses:

=PI()

To multiply the value of pi by 10, you’d use this formula:

=PI()*10

## ARABIC and ROMAN for Converting Numerals

Another math function you may find handy is for converting to and from [Arabic](https://en.wikipedia.org/wiki/Arabic_numerals) and [Roman numerals](https://en.wikipedia.org/wiki/Roman_numerals).

ADVERTISEMENT

The syntax for each is `ARABIC(text)` and `ROMAN(value, form)` where the first argument is required for each.

ADVERTISEMENT

The optional argument for the ROMAN function specifies the type of Roman numeral from Classic to Simplified. Enter the number 0, word TRUE, or omit the argument for Classic. Use a 1, 2, or 3 for a more concise result. Or, enter the number 4 or the word FALSE for Simplified.

To convert the Roman numeral MMIM to an Arabic number, use this formula making sure to include the text in quotes:

=ARABIC("MMIM")

ADVERTISEMENT

To convert 2,999 to a Roman numeral, you’d use this formula:

=ROMAN(2999)

ADVERTISEMENT

To convert the same number in Simplified form, use one of these formulas:

=ROMAN(2999,4)

=ROMAN(2999,FALSE)

## REPT for Entering Repeating Text

If you want to add a series of characters, symbols, or text as a placeholder or for a visual effect, use the REPT [text function](https://www.howtogeek.com/791554/excel-functions-for-text/).

**RELATED:** [**_9 Useful Microsoft Excel Functions for Working With Text_**](https://www.howtogeek.com/791554/excel-functions-for-text/)

The syntax is `REPT(text, number)` where both arguments are required. Enter the text argument within quotes and then the number of times to repeat that text.

ADVERTISEMENT

To repeat the word Excel 10 times in a cell, you’d use this formula:

=REPT("Excel",10)

ADVERTISEMENT

To repeat an asterisk 20 times, you’d use this formula:

=REPT("*",20)

We’ve covered many [Excel functions](https://www.howtogeek.com/794192/excel-date-and-time-functions/) at How-To Geek and try to walk you through using the most common options. Hopefully one of these out-of-the-ordinary functions is exactly what you need for math, engineering, statistical, lookup, or textual data.

**RELATED:** [**_13 Essential Excel Functions for Data Entry_**](https://www.howtogeek.com/791838/excel-functions-data-entry/)

[](https://www.howtogeek.com/author/sandywrittenhouse/ "Sandy Writtenhouse")[SANDY WRITTENHOUSE](https://www.howtogeek.com/author/sandywrittenhouse/)   
With her B.S. in Information Technology, Sandy worked for many years in the IT industry as a Project Manager, Department Manager, and PMO Lead. She learned how technology can enrich both professional and personal lives by using the right tools. And, she has shared those suggestions and how-tos on many websites over time. With thousands of articles under her belt, Sandy strives to help others use technology to their advantage.[READ FULL BIO »](https://www.howtogeek.com/author/sandywrittenhouse/)

  

[](https://www.howtogeek.com/)

[

Facebook



](https://facebook.com/howtogeek)[

Twitter



](https://www.twitter.com/howtogeek)[

LinkedIn



](https://www.linkedin.com/company/howtogeek/)[

Instagram



](https://www.instagram.com/howtogeeksite)

The Best Free Tech Newsletter Anywhere

 

-   [ABOUT US](https://www.howtogeek.com/about/)
-   [CONTACT US](https://www.howtogeek.com/contact/)
-   [JOIN OUR TEAM](https://www.howtogeek.com/345703/we-are-hiring/)
-   [ADVERTISING](https://www.lifesavvymedia.com/sponsorship.php)
-   [PRIVACY POLICY](https://www.howtogeek.com/privacy-policy/)
-   [TERMS OF USE](https://www.howtogeek.com/terms-of-use/)
-   [ACCESSIBILITY](https://www.howtogeek.com/accessibility/)

[© 2023 How-To Geek, LLC. All Rights Reserved](https://www.howtogeek.com/)

[](https://amp.trackonomics.net/)