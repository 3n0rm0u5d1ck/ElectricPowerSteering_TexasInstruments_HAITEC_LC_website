---
layout: default
title: Interpolation_Design_MDD
nav_order: 3
parent: Nexteer Library
---
{% raw %}
[1 Variable X Variable Y 2D Table Lookup function (with interpolation)
2](#variable-x-variable-y-2d-table-lookup-function-with-interpolation)

[1.1 Requirement 2](#requirement)

[1.2 Implementation: 2](#implementation)

[1.2.1 Unsigned X, Unsigned Y 4](#unsigned-x-unsigned-y)

[1.2.2 Signed X, Unsigned Y 5](#signed-x-unsigned-y)

[1.2.3 Signed X, Signed Y 7](#signed-x-signed-y)

[1.2.4 Unsigned X, Signed Y 8](#unsigned-x-signed-y)

[2 Fixed X Variable Y 2D Table Lookup function (with interpolation)
11](#fixed-x-variable-y-2d-table-lookup-function-with-interpolation)

[2.1 Requirement 11](#requirement-1)

[2.2 Implementation: 11](#implementation-1)

[2.2.1 Unsigned X, Unsigned Y 11](#unsigned-x-unsigned-y-1)

[2.2.2 Signed X, Unsigned Y 13](#signed-x-unsigned-y-1)

[2.2.3 Signed X, Signed Y 14](#signed-x-signed-y-1)

[2.2.4 Unsigned X, Signed Y 16](#unsigned-x-signed-y-1)

[3 Single X Multiple Y (Bilinear Interpolation)
17](#single-x-multiple-y-bilinear-interpolation)

[3.1 Implementation: 17](#implementation-2)

[3.1.1 Syntax: BilinearXYM_s16_u16Xs16YM_Cnt (BS, input, \*BSTbl, BSize,
\*XTbl, \*YMTbl, Xsize)
17](#syntax-bilinearxym_s16_u16xs16ym_cnt-bs-input-bstbl-bsize-xtbl-ymtbl-xsize)

[3.1.2 Syntax: BilinearXYM_u16_u16Xu16YM_Cnt(BS, input, \*BSTbl, BSsize,
\*XTbl, \*YMTbl, Xsize)
20](#syntax-bilinearxym_u16_u16xu16ym_cntbs-input-bstbl-bssize-xtbl-ymtbl-xsize)

[3.1.3 Syntax: BilinearXYM_s16_s16Xs16YM_Cnt (BS, input, \*BSTbl, BSize,
\*XTbl, \*YMTbl, Xsize)
23](#syntax-bilinearxym_s16_s16xs16ym_cnt-bs-input-bstbl-bsize-xtbl-ymtbl-xsize)

[3.1.4 Syntax: BilinearXYM_u16_s16Xu16YM_Cnt(BS, input, \*BSTbl, BSsize,
\*XTbl, \*YMTbl, Xsize)
26](#syntax-bilinearxym_u16_s16xu16ym_cntbs-input-bstbl-bssize-xtbl-ymtbl-xsize)

[4 Multiple X Multiple Y (Bilinear Interpolation)
29](#multiple-x-multiple-y-bilinear-interpolation)

[4.1 Implementation 29](#implementation-3)

[4.1.1 Syntax: BilinearXMYM_u16_u16XMu16YM_Cnt( BS, input, \*BSTbl,
BSsize, \*XMTbl, \*YMTbl, Xsize)
29](#syntax-bilinearxmym_u16_u16xmu16ym_cnt-bs-input-bstbl-bssize-xmtbl-ymtbl-xsize)

[4.1.2 Syntax: BilinearXMYM_s16_u16XMs16YM_Cnt(BS, input, \*BSTbl,
BSsize, \*XMTbl, \*YMTbl, Xsize)
32](#syntax-bilinearxmym_s16_u16xms16ym_cntbs-input-bstbl-bssize-xmtbl-ymtbl-xsize)

[4.1.3 Syntax: BilinearXMYM_u16_s16XMu16YM_Cnt( BS, input, \*BSTbl,
BSsize, \*XMTbl, \*YMTbl, Xsize)
40](#syntax-bilinearxmym_u16_s16xmu16ym_cnt-bs-input-bstbl-bssize-xmtbl-ymtbl-xsize)

[5 UnitTesting Range: Linear and Bilinear Interpolation
44](#unittesting-range-linear-and-bilinear-interpolation)

[6 Revision Control Log 44](#revision-control-log)

# Variable X Variable Y 2D Table Lookup function (with interpolation)

## Requirement

The Variable X Variable Y 2D table has the Variable X as the input
(independent variable) and the Variable Y as the output (dependent
variable). The lookup function with interpolation is used to interpolate
the values of Y corresponding to the input value for X. This is
implemented using the straight-line equation as given below:

$$y = (\frac{y_{n + 1} - y_{n}}{x_{n + 1} - x_{n}}) \ast (x - x_{n}) + y_{n}$$

where,

n = index into the independent and dependent variable tables

n+1 = next consecutive index into the tables.

(y~n+1~ - y~n~) = interval in the dependent table within which the
interpolated output is calculated.

(x~n+1~ - x~n~) = interval in the independent table within which the
input lies.

y = interpolated output (dependent variable)

x = input (independent variable)

Note that y~n+1~ \< y~n~ or y~n+1~ \> y~n~, for negative or positive
slopes and x~n+1~ \> x~n~.

The index n and n+1, are determined using Straight-Forward Search
method. Using the indices, the values of x~n+1~, x~n~, y~n+1~ and y~n~
are determined.

The difference (y~n+1~ - y~n~) is held in a signed variable to ensure
that the interpolation can handle both positive and negative slopes.

The Variable X VariableY interpolation function is defined as a function
with the input x value and table name passed as parameters. The function
will return the interpolated output y as its output.

## Implementation:

Note: Straight Forward Search method is used for calculating the index
n.

### Unsigned X, Unsigned Y

Syntax : IntplVarXY_u16_u16Xu16Y_Cnt ( \*TableX, \*TableY, Size, input)

Arguments:

> 1\) TableX: - The Variable X 2D table (independent table)
>
> 2\) TableY: - The Variable Y 2D table (dependent table)
>
> 3\) Size: - Size of the table
>
> 4\) input: - The input to the table

output: The output from the table.

**Pseudo Code :**

UINT16 input, output, Size

UINT16 index = 0

SINT16 tmpout2, sOutput

SINT32 diffY, diffX, diffXinput, tmpout1

const UINT16 TableX = \[ x1, x2, x3, x4, x5,….. \]

const UINT16 TableY = \[ y1, y2, y3, y4, y5,….. \]

/\* Check for Range \*/

if ( input \<= TableX\[0\] )

return TableY\[0\]

else if ( input \>= TableX\[size-1\] )

return TableY\[size-1\]

endif

/\* In range. Get Index \*/

while ( TableX\[index + 1\] \< input )

index = index + 1

endwhile

/\* Interpolate and get the output \*/

diffY = TableY\[index+1\] - TableY\[index\]

diffX = TableX\[index+1\] - TableX\[index\]

diffXinput = input - TableX\[index\]

/\* Product in 32 bit \*/

tmpout1 = diffY\* diffXinput

/\* Check if Divide by zero \*/

if (diffX == 0)

tmpout2 = 0

else

/\* Here, the lower 16 bits are assigned to tmpout2 \*/

tmpout2 = tmpout1 / diffX

endif

output = tmpout2 + TableY\[index\]

return output

end

### Signed X, Unsigned Y

Syntax : IntplVarXY_u16_s16Xu16Y_Cnt (\*TableX, \*TableY, Size, input)

Arguments:

> 1\) TableX: - The Variable X 2D table (independent table)
>
> 2\) TableY: - The Variable Y 2D table (dependent table)
>
> 3\) Size: - Size of the table
>
> 4\) input: - The input to the table

output: The output from the table.

**Pseudo Code :**

SINT16 input

UINT16 output, Size

UINT16 index = 0

SINT16 tmpout2, sOutput

SINT32 diffY, diffX, diffXinput, tmpout1

const SINT16 TableX = \[ x1, x2, x3, x4, x5,….. \]

const UINT16 TableY = \[ y1, y2, y3, y4, y5,….. \]

/\* Check for Range \*/

if ( input \<= TableX\[0\] )

return TableY\[0\]

else if ( input \>= TableX\[size-1\] )

return TableY\[size-1\]

endif

/\* In range. Get Index \*/

while ( TableX\[index + 1\] \< input )

index = index + 1

endwhile

/\* Interpolate and get the output \*/

diffY = TableY\[index+1\] - TableY\[index\]

diffX = TableX\[index+1\] - TableX\[index\]

diffXinput = input - TableX\[index\]

/\* Product in 32 bit \*/

tmpout1 = diffY \* diffXinput

/\* Check if Divide by zero \*/

if (diffX == 0)

tmpout2 = 0

else

/\* Here, the lower 16 bits are assigned to tmpout2 \*/

tmpout2 = tmpout1 / diffX

endif

output = tmpout2 + TableY\[index\]

return output

end

### Signed X, Signed Y

Syntax : IntplVarXY_s16_s16Xs16Y_Cnt (\*TableX, \*TableY, Size, input)

Arguments:

> 1\) TableX: - The Variable X 2D table (independent table)
>
> 2\) TableY: - The Variable Y 2D table (dependent table)
>
> 3\) Size: - Size of the table
>
> 4\) input: - The input to the table

output: The output from the table.

**Pseudo Code :**

SINT16 input, output

UINT16 Size

UINT16 index = 0

SINT16 tmpout2

SINT32 diffY, diffX, diffXinput, tmpout1

const SINT16 TableX = \[ x1, x2, x3, x4, x5,….. \]

const SINT16 TableY = \[ y1, y2, y3, y4, y5,….. \]

/\* Check for Range \*/

if ( input \<= TableX\[0\] )

return TableY\[0\]

else if ( input \>= TableX\[size-1\] )

return TableY\[size-1\]

endif

/\* In range. Get Index \*/

while ( TableX\[index + 1\] \< input )

index = index + 1

endwhile

/\* Interpolate and get the output \*/

diffY = TableY\[index+1\] - TableY\[index\]

diffX = TableX\[index+1\] - TableX\[index\]

diffXinput = input - TableX\[index\]

/\* Product in 32 bit \*/

tmpout1 = diffY \* diffXinput

/\* Check if Divide by zero \*/

if (diffX == 0)

tmpout2 = 0

else

/\* Here, the lower 16 bits are assigned to tmpout2 \*/

tmpout2 = tmpout1 / diffX

endif

output = tmpout2 + TableY\[index\]

return output

end

### Unsigned X, Signed Y

Syntax : IntplVarXY_s16_u16Xs16Y_Cnt (\*TableX, \*TableY, Size, input)

Arguments:

> 1\) TableX: - The Variable X 2D table (independent table)
>
> 2\) TableY: - The Variable Y 2D table (dependent table)
>
> 3\) Size: - Size of the table
>
> 4\) input: - The input to the table

output: The output from the table.

**Pseudo Code :**

UINT16 input, Size

SINT16 output

UINT16 index = 0

SINT16 tmpout2

SINT32 diffY, diffX, diffXinput, tmpout1

const UINT16 TableX = \[ x1, x2, x3, x4, x5,….. \]

const SINT16 TableY = \[ y1, y2, y3, y4, y5,….. \]

/\* Check for Range \*/

if ( input \<= TableX\[0\] )

return TableY\[0\]

else if ( input \>= TableX\[size-1\] )

return TableY\[size-1\]

endif

/\* In range. Get Index \*/

while ( TableX\[index + 1\] \< input )

index = index + 1

endwhile

/\* Interpolate and get the output \*/

diffY = TableY\[index+1\] - TableY\[index\]

diffX = TableX\[index+1\] - TableX\[index\]

diffXinput = input - TableX\[index\]

/\* Product in 32 bit \*/

tmpout1 = diffY \* diffXinput

/\* Check if Divide by zero \*/

if (diffX == 0)

tmpout2 = 0

else

/\* Here, the lower 16 bits are assigned to tmpout2 \*/

tmpout2 = tmpout1 / diffX

endif

output = tmpout2 + TableY\[index\]

return output

end

# Fixed X Variable Y 2D Table Lookup function (with interpolation)

## Requirement

The Fixed X Variable Y 2D table has the Fixed X as the input
(independent variable) and the Variable Y (dependent variable) as the
output. The interpolation function is used to interpolate the values of
Y corresponding to the input value for X. It is assumed that the
independent axis (X) will always start from 0. This is implemented using
the straight-line equation as given below:

$$y = (\frac{y_{n + 1} - y_{n}}{\Delta x}) \ast (x - x_{n}) + y_{n}$$

where,

n = index into the Table

(y~n+1~ - y~n~) = interval in the dependent table within which the
interpolated output is calculated.

∆x = fixed X interval within which the input lies.

y = interpolated output

x = input

Determine the value of n, i.e the index into the table, n = truncate ( x
/ ∆x ). Using this index n, determine the values of x~n~, y~n~ and
y~n+1~. The output y can then be calculated based on the straight line
given above.

## Implementation:

### Unsigned X, Unsigned Y

Syntax : IntplFxdX_u16_u16Xu16Y_Cnt (DeltaX, \*TableY, Size, input)

Arguments:

> 1\. DeltaX: - The Fixed X interval
>
> 2\. TableY: - The Variable Y 2D table (dependent table)
>
> 3\. Size: - Size of the table
>
> 4\. input: - The input to the table

output: The output from the table.

**Pseudo Code :**

UINT16 input, output, Size

UINT16 index = 0

SINT16 tmpout2, sOutput

SINT32 diffY, diffXinput, tmpout1

const UINT16 TableY = \[ y1, y2, y3, y4, y5,….. \]

if (DeltaX == 0)

/\* Cannot do interpolation. Return Y0 \*/

return TableY\[0\]

endif

/\* Check for Range \*/

if ( input \<= 0 )

return TableY\[0\]

else if ( input \>= DeltaX \* (size-1) )

return TableY\[size-1\]

endif

/\* In range. Get Index \*/

index = truncate (input / DeltaX)

/\* Interpolate and get the output \*/

diffY = TableY\[index+1\] - TableY\[index\]

diffXinput = input - DeltaX \* index

/\* Product in 32 bit \*/

tmpout1 = diffY \* diffXinput

/\* Here, the lower 16 bits are assigned to tmpout2 \*/

tmpout2 = tmpout1 / DeltaX

output = tmpout2 + TableY\[index\]

return output

end

### Signed X, Unsigned Y

Syntax : IntplFxdX_u16_s16Xu16Y_Cnt (DeltaX, \*TableY, Size, input)

Arguments:

> 1\. DeltaX: - The Fixed X interval
>
> 2\. TableY: - The Variable Y 2D table (dependent table)
>
> 3\. Size: - Size of the table
>
> 4\. input: - The input to the table

output: The output from the table.

**Pseudo Code :**

SINT16 input

UINT16 output, Size

UINT16 index = 0

SINT16 tmpout2, sOutput

SINT32 diffY, diffXinput , tmpout1

const UINT16 TableY = \[ y1, y2, y3, y4, y5,….. \]

if (DeltaX == 0)

/\* Cannot do interpolation. Return Y0 \*/

return TableY\[0\]

endif

/\* Check for Range \*/

if ( input \<= 0 )

return TableY\[0\]

else if ( input \>= DeltaX \* (size-1) )

return TableY\[size-1\]

endif

/\* In range. Get Index \*/

index = truncate (input / DeltaX)

/\* Interpolate and get the output \*/

diffY = TableY\[index+1\] - TableY\[index\]

diffXinput = input - DeltaX \* index

/\* Product in 32 bit \*/

tmpout1 = diffY \* diffXinput

/\* Here, the lower 16 bits are assigned to tmpout2 \*/

tmpout2 = tmpout1 / DeltaX

output = tmpout2 + TableY\[index\]

return output

end

### Signed X, Signed Y

Syntax: IntplFxdX_s16_s16Xs16Y_Cnt (DeltaX, \*TableY, Size, input)

Arguments:

> 1\. DeltaX: - The Fixed X interval
>
> 2\. TableY: - The Variable Y 2D table (dependent table)
>
> 3\. Size: - Size of the table
>
> 4\. input: - The input to the table

output: The output from the table.

**Pseudo Code :**

SINT16 input, output

UINT16 Size

UINT16 index = 0

SINT16 tmpout2

SINT32 diffY, diffXinput , tmpout1

const SINT16 TableY = \[ y1, y2, y3, y4, y5,….. \]

if (DeltaX == 0)

/\* Cannot do interpolation. Return Y0 \*/

return TableY\[0\]

endif

/\* Check for Range \*/

if ( input \<= 0 )

return TableY\[0\]

else if ( input \>= DeltaX \* (size-1) )

return TableY\[size-1\]

endif

/\* In range. Get Index \*/

index = truncate (input / DeltaX)

/\* Interpolate and get the output \*/

diffY = TableY\[index+1\] - TableY\[index\]

diffXinput = input - DeltaX \* index

/\* Product in 32 bit \*/

tmpout1 = diffY \* diffXinput

/\* Here, the lower 16 bits are assigned to tmpout2 \*/

tmpout2 = tmpout1 / DeltaX

output = tmpout2 + TableY\[index\]

return output

end

### Unsigned X, Signed Y

Syntax: IntplFxdX_s16_u16Xs16Y_Cnt (DeltaX, \*TableY, Size, input)

Arguments:

> 1\. DeltaX: - The Fixed X interval
>
> 2\. TableY: - The Variable Y 2D table (dependent table)
>
> 3\. Size: - Size of the table
>
> 4\. input: - The input to the table

output: The output from the table.

**Pseudo Code :**

UINT16 input, Size

SINT16 output

UINT16 index = 0

SINT16 tmpout2

SINT32 diffY, diffXinput, tmpout1

const SINT16 TableY = \[ y1, y2, y3, y4, y5,….. \]

if (DeltaX == 0)

/\* Cannot do interpolation. Return Y0 \*/

return TableY\[0\]

endif

/\* Check for Range \*/

if ( input \<= 0 )

return TableY\[0\]

else if ( input \>= DeltaX \* (size-1) )

return TableY\[size-1\]

endif

/\* In range. Get Index \*/

index = truncate (input / DeltaX)

/\* Interpolate and get the output \*/

diffY = TableY\[index+1\] - TableY\[index\]

diffXinput = input - DeltaX \* index

/\* Product in 32 bit \*/

tmpout1 = diffY \* diffXinput

/\* Here, the lower 16 bits are assigned to tmpout2 \*/

tmpout2 = tmpout1 / DeltaX

output = tmpout2 + TableY\[index\]

return output

end

# Single X Multiple Y (Bilinear Interpolation)

## Implementation:

### Syntax: BilinearXYM_s16_u16Xs16YM_Cnt (BS, input, \*BSTbl, BSize, \*XTbl, \*YMTbl, Xsize)

Arguments:

1.  BS:- Bilinear Selector

2.  Input:-The input to the table

3.  BSTbl:- Bilinear Selector Table 2D

4.  BSize:- Bilinear Selector Table Size

5.  XTbl:- Table X 2D

6.  YMTbl:- Table Y with MxN dimension

7.  Xsize:- Size of XTbl

Output:- The output from the table

**Pseudo Code:**

> UINT16 BSindex, Xindex
>
> UINT16 ArrayIndex1, ArrayIndex2, ArrayIndex3, ArrayIndex4
>
> SINT32 BSinputDiff, XInputDiff
>
> FLOAT32 Numerator_f32, Denominator_f32, Output_f32
>
> SINT16 Output_s16
>
> Const UINT16 BSTbl = \[z1,z2,z3,z4,…..\]
>
> Const UINT16 XTbl = \[x1,x2,x3,x4,…...\]
>
> Const SINT16 YMTbl\[mxn\] = \[(y1,y2,y3…),(y4,y5,y6….),….\]
>
> **If** (BS \<= BSTbl\[0\])
>
> BSindex = 0
>
> BS = BSTbl\[0\]

**Else if** (BS \>= BSTbl\[BSize-1\])

BSindex = BSsize -2

BS = BSTbl\[BSsize -1\]

**While** ((BSTbl\[BSindex\] = = BSTbl\[BSindex + 1\] && (BSindex \>
0)))

BSindex = BSindex - 1

**Wend**

**Else**

BSindex = 0

**While** ( BSTbl\[BSindex +1\] \< BS)

BSindex = BSindex + 1

**Wend**

**Endif**

**If** (input \<= XTbl\[0\])

Xindex = 0

Input = XTbl\[0\]

**Else if** (input \>= XTbl\[XSize – 1\])

Xindex = Xsize – 2

Input = XTbl\[Xsize -1\]

**Else**

Xindex = 0

**While** ( XTbl\[Xindex +1\] \< input)

Xindex = Xindex+1

**Wend**

**Endif**

ArrayIndex1 = (BSindex \* Xsize) + Xindex

ArrayIndex2 = (BSindex \* Xsize) + Xindex + 1

ArrayIndex3 = ((BSindex + 1) \* Xsize) + Xindex

ArrayIndex4 = ((BSindex + 1) \* Xsize) + Xindex + 1

BSInputDiff = BS – BSTbl\[BSindex\]

XInputDiff = input – XTbl\[Xindex\]

> **Numerator_f32** = ( YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]) \*
> ((BSTbl\[BSindex+1\] – BSTbl\[BSindex\]) \* XInputDiff) +

(YMTbl\[ArrayIndex3\] – YMTbl\[ArrayIndex1\]) \*

(BSInputDiff \* (XTbl\[Xindex+1\] – XTbl\[Xindex\])) +

(XInputDiff \* BSInputDiff ) \*

> ((YMTbl\[ArrayIndex4\]) – (YMTbl\[ArrayIndex3\]) –
> (YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]))
>
> **Denominator_f32** = (BSTbl\[BSindex +1\] – BSTbl\[BSindex\]) \*
> (XTbl\[Xindex+1\] – XTbl\[Xindex\])

**If** (Denominator_f32 \<= FLT_EPSILON)

Output_f32 = YMTbl\[ArrayIndex1\]

**Else**

Output_f32 = YMTbl\[ArrayIndex1\] + Numerator_f32 / Denominator_f32

**Endif**

**If** (Output_f32 \>= 0)

Output_f32 = Output_f32 + 0.5

**Else**

Output_f32 =Output_f32 – 0.5

**Endif**

/\*Float to SINT16 typecast\*/

Output_s16 = Output_f32

return Output_s16

End

### Syntax: BilinearXYM_u16_u16Xu16YM_Cnt(BS, input, \*BSTbl, BSsize, \*XTbl, \*YMTbl, Xsize)

Arguments

1.  BS:- Bilinear Selector

2.  input:-The input to the table

3.  BSTbl:- Bilinear Selector Table 2D

4.  BSize:- Bilinear Selector Table Size

5.  XTbl:- Table X 2D

6.  YMTbl:- Table Y with MxN dimension

7.  Xsize:- Size of XTbl

Output:- The output from the table

Pseudo Code:

> UINT16 BSindex, Xindex
>
> UINT16 ArrayIndex1, ArrayIndex2, ArrayIndex3, ArrayIndex4
>
> SINT32 BSInputDiff, XInputDiff
>
> FLOAT32 Numerator_f32, Denominator_f32
>
> UINT16 Output_u16

Const UINT16 BSTbl = \[z1,z2,z3,z4,…..\]

Const UINT16 XTbl = \[x1,x2,x3,x4,…...\]

Const UINT16 YMTbl\[mxn\] = \[(y1,y2,y3…),(y4,y5,y6….),….\]

> **If** (BS \<= BSTbl\[0\])
>
> BSindex = 0
>
> BS = BSTbl\[0\]
>
> **Else if** (BS \>= BSTbl\[BSsize – 1\])
>
> BSindex = BSsize -2
>
> BS = BSTbl \[ BSsize – 1\]
>
> **While** (( BSTbl \[BSindex\] == BSTbl \[ BSindex+1\] && (BSindex \>
> 0)))
>
> BSindex = BSindex – 1
>
> **Wend**
>
> **Else**
>
> BSindex = 0
>
> **While** (BSTbl\[BSindex +1\]\<BS)
>
> BSindex = BSindex +1
>
> **Wend**
>
> **Endif**
>
> **If** (input \<= XTbl\[0\])
>
> Xindex = 0
>
> Input = XTbl\[0\]
>
> **Else if** (input \>= XTbl\[XSize -1\])
>
> Xindex = Xsize -2
>
> input = XTbl\[Xsize -1\]

**Else**

Xindex = 0

**While** ( XTbl\[Xindex + 1\] \< input)

Xindex= Xindex + 1

**Wend**

**Endif**

ArrayIndex1 = (BSindex \* Xsize) + Xindex

ArrayIndex2 = (BSindex \* Xsize) + Xindex + 1

ArrayIndex3 = ((BSindex + 1)\* Xsize) + Xindex

ArrayIndex4 = ((BSindex + 1)\* Xsize) + Xindex + 1

BSInputDiff = BS – BSTbl\[BSindex\]

XInputDiff = input – XTbl\[Xindex\]

**Numerator_f32** = ( YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]) \*

((BSTbl \[ BSindex + 1\] – BSTbl\[BSindex\]) \* XInputDiff) +

(YMTbl \[ ArrayIndex3\] – YMTbl\[ArrayIndex1\]) \*

(BSInputDiff \* (XTbl\[Xindex+1\] – XTbl\[Xindex\])) +

(XInputDiff \* BSInputDiff) \*

> ((YMTbl\[ArrayIndex4\]) – (YMTbl\[ArrayIndex3\]) –
> (YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]))
>
> **Denominator_f32** = (BSTbl\[BSindex+1\] – BSTbl\[BSindex\]) \*
> (XTbl\[Xindex+1\] – XTbl\[Xindex\])

**If** (Denominator_f32 \<= FLT_EPSILON) Output_u16 =
YMTbl\[ArrayIndex1\] + 0.5

**Else**

> Output_u16 = YMTbl\[ArrayIndex1\] + (Numerator_f32 /
> Denominator_f32) + 0.5

**Endif**

return Output_u16

end

### Syntax: BilinearXYM_s16_s16Xs16YM_Cnt (BS, input, \*BSTbl, BSize, \*XTbl, \*YMTbl, Xsize)

Arguments:

1.  BS:- Bilinear Selector

2.  Input:-The input to the table

3.  BSTbl:- Bilinear Selector Table 2D

4.  BSize:- Bilinear Selector Table Size

5.  XTbl:- Table X 2D

6.  YMTbl:- Table Y with MxN dimension

7.  Xsize:- Size of XTbl

Output:- The output from the table

**Pseudo Code:**

> UINT16 BSindex, Xindex
>
> UINT16 ArrayIndex1, ArrayIndex2, ArrayIndex3, ArrayIndex4
>
> SINT32 BSinputDiff, XInputDiff
>
> FLOAT32 Numerator_f32, Denominator_f32, Output_f32
>
> SINT16 Output_s16
>
> Const UINT16 BSTbl = \[z1,z2,z3,z4,…..\]
>
> Const UINT16 XTbl = \[x1,x2,x3,x4,…...\]
>
> Const SINT16 YMTbl\[mxn\] = \[(y1,y2,y3…),(y4,y5,y6….),….\]
>
> **If** (BS \<= BSTbl\[0\])
>
> BSindex = 0
>
> BS = BSTbl\[0\]

**Else if** (BS \>= BSTbl\[BSize-1\])

BSindex = BSsize -2

BS = BSTbl\[BSsize -1\]

**While** ((BSTbl\[BSindex\] = = BSTbl\[BSindex + 1\] && (BSindex \>
0)))

BSindex = BSindex - 1

**Wend**

**Else**

BSindex = 0

**While** ( BSTbl\[BSindex +1\] \< BS)

BSindex = BSindex + 1

**Wend**

**Endif**

**If** (input \<= XTbl\[0\])

Xindex = 0

Input = XTbl\[0\]

**Else if** (input \>= XTbl\[XSize – 1\])

Xindex = Xsize – 2

Input = XTbl\[Xsize -1\]

**Else**

Xindex = 0

**While** ( XTbl\[Xindex +1\] \< input)

Xindex = Xindex+1

**Wend**

**Endif**

ArrayIndex1 = (BSindex \* Xsize) + Xindex

ArrayIndex2 = (BSindex \* Xsize) + Xindex + 1

ArrayIndex3 = ((BSindex + 1) \* Xsize) + Xindex

ArrayIndex4 = ((BSindex + 1) \* Xsize) + Xindex + 1

BSInputDiff = BS – BSTbl\[BSindex\]

XInputDiff = input – XTbl\[Xindex\]

> **Numerator_f32** = ( YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]) \*
> ((BSTbl\[BSindex+1\] – BSTbl\[BSindex\]) \* XInputDiff) +

(YMTbl\[ArrayIndex3\] – YMTbl\[ArrayIndex1\]) \*

(BSInputDiff \* (XTbl\[Xindex+1\] – XTbl\[Xindex\])) +

(XInputDiff \* BSInputDiff ) \*

> ((YMTbl\[ArrayIndex4\]) – (YMTbl\[ArrayIndex3\]) –
> (YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]))
>
> **Denominator_f32** = (BSTbl\[BSindex +1\] – BSTbl\[BSindex\]) \*
> (XTbl\[Xindex+1\] – XTbl\[Xindex\])

**If** (Denominator_f32 \<= FLT_EPSILON) Output_f32 =
YMTbl\[ArrayIndex1\]

**Else**

Output_f32 = YMTbl\[ArrayIndex1\] + Numerator_f32 / Denominator_f32

**Endif**

**If** (Output_f32 \>= 0)

Output_f32 = Output_f32 + 0.5

**Else**

Output_f32 =Output_f32 – 0.5

**Endif**

/\*Float to SINT16 typecast\*/

Output_s16 = Output_f32

return Output_s16

End

### Syntax: BilinearXYM_u16_s16Xu16YM_Cnt(BS, input, \*BSTbl, BSsize, \*XTbl, \*YMTbl, Xsize)

Arguments

1.  BS:- Bilinear Selector

2.  input:-The input to the table

3.  BSTbl:- Bilinear Selector Table 2D

4.  BSize:- Bilinear Selector Table Size

5.  XTbl:- Table X 2D

6.  YMTbl:- Table Y with MxN dimension

7.  Xsize:- Size of XTbl

Output:- The output from the table

Pseudo Code:

> UINT16 BSindex, Xindex
>
> UINT16 ArrayIndex1, ArrayIndex2, ArrayIndex3, ArrayIndex4
>
> SINT32 BSInputDiff, XInputDiff
>
> FLOAT32 Numerator_f32, Denominator_f32
>
> UINT16 Output_u16

Const UINT16 BSTbl = \[z1,z2,z3,z4,…..\]

Const UINT16 XTbl = \[x1,x2,x3,x4,…...\]

Const UINT16 YMTbl\[mxn\] = \[(y1,y2,y3…),(y4,y5,y6….),….\]

> **If** (BS \<= BSTbl\[0\])
>
> BSindex = 0
>
> BS = BSTbl\[0\]
>
> **Else if** (BS \>= BSTbl\[BSsize – 1\])
>
> BSindex = BSsize -2
>
> BS = BSTbl \[ BSsize – 1\]
>
> **While** (( BSTbl \[BSindex\] == BSTbl \[ BSindex+1\] && (BSindex \>
> 0)))
>
> BSindex = BSindex – 1
>
> **Wend**
>
> **Else**
>
> BSindex = 0
>
> **While** (BSTbl\[BSindex +1\]\<BS)
>
> BSindex = BSindex +1
>
> **Wend**
>
> **Endif**
>
> **If** (input \<= XTbl\[0\])
>
> Xindex = 0
>
> Input = XTbl\[0\]
>
> **Else if** (input \>= XTbl\[XSize -1\])
>
> Xindex = Xsize -2
>
> input = XTbl\[Xsize -1\]

**Else**

Xindex = 0

**While** ( XTbl\[Xindex + 1\] \< input)

Xindex= Xindex + 1

**Wend**

**Endif**

ArrayIndex1 = (BSindex \* Xsize) + Xindex

ArrayIndex2 = (BSindex \* Xsize) + Xindex + 1

ArrayIndex3 = ((BSindex + 1)\* Xsize) + Xindex

ArrayIndex4 = ((BSindex + 1)\* Xsize) + Xindex + 1

BSInputDiff = BS – BSTbl\[BSindex\]

XInputDiff = input – XTbl\[Xindex\]

**Numerator_f32** = ( YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]) \*

((BSTbl \[ BSindex + 1\] – BSTbl\[BSindex\]) \* XInputDiff) +

(YMTbl \[ ArrayIndex3\] – YMTbl\[ArrayIndex1\]) \*

(BSInputDiff \* (XTbl\[Xindex+1\] – XTbl\[Xindex\])) +

(XInputDiff \* BSInputDiff) \*

> ((YMTbl\[ArrayIndex4\]) – (YMTbl\[ArrayIndex3\]) –
> (YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]))
>
> **Denominator_f32** = (BSTbl\[BSindex+1\] – BSTbl\[BSindex\]) \*
> (XTbl\[Xindex+1\] – XTbl\[Xindex\])

**If** (Denominator_f32 \<= FLT_EPSILON) Output_u16 =
YMTbl\[ArrayIndex1\] + 0.5

**Else**

> Output_u16 = YMTbl\[ArrayIndex1\] + (Numerator_f32 /
> Denominator_f32) + 0.5

**Endif**

return Output_u16

end

# Multiple X Multiple Y (Bilinear Interpolation)

## Implementation

### Syntax: BilinearXMYM_u16_u16XMu16YM_Cnt( BS, input, \*BSTbl, BSsize, \*XMTbl, \*YMTbl, Xsize)

Arguments:

1.  BS:- Bilinear Selector

2.  input:-The input to the table

3.  BSTbl:- Bilinear Selector Table 2D

4.  BSize:- Bilinear Selector Table Size

5.  XTbl:- Table X with \[MxN\] dimension

6.  YMTbl:- Table Y with \[MxN\] dimension

7.  Xsize:- Size of XTbl

Output:- The output from the table

Pseudo Code:

UINT16 BSindex, X1index, X2index,

UINT16 ArrayIndex1, ArrayIndex2, ArrayIndex3, ArrayIndex4

SINT32 BSInputDiff, XInputDiff1, XInputDiff2

SINT32 Mult1_s32, Mult2_s32

FLOAT32 Numerator_f32, Denominator_f32

UINT16 Output_u16

SINT32 Den1_s32, Den2_s32, Den3_s32

UINT16 input2 = input

Const UINT16 BSTbl = \[z1,z2,z3,z4,…..\]

Const UINT16 XTbl\[mxn\] = \[(x1,x2,x3…),(x4,x5,x6….),….\]

Const UINT16 YMTbl\[mxn\] = \[(y1,y2,y3…),(y4,y5,y6….),….\]

**If** ( BS \<= BSTbl\[0\] )

BSindex = 0

BS = BSTbl \[0\]

**Else if** (BS \>= BSTbl\[BSsize -1\])

BSindex = BSsize – 2

BS = BSTbl \[ BSsize-1\]

**while** (BSTbl\[BSindex\] == BSTbl\[BSindex+1\] && (BSindex \> 0))

BSindex = BSindex -1

**wend**

**Else**

BSindex = 0

**while** ( BSTbl \[ BSindex +1\] \< BS)

BSindex = BSindex +1

**wend**

**Endif**

**If** ( input \<= XMTbl \[ BSindex \* Xsize\])

X1index = 0

Input = XMTbl \[BSindex \* Xsize\]

**Else if** (input \>= XMTbl \[ (BSindex \* Xsize) + Xsize -1\])

X1index = Xsize – 2

> input = XMTbl \[ (BSindex \* Xsize) + Xsize – 1\]
>
> **while** ((XMTbl\[(BSindex \* Xsize)+X1index\] == XMTbl\[(BSindex \*
> Xsize) + X1index +1\]) && (X1index \>0))
>
> X1index = X1index – 1
>
> **wend**

**Else**

X1index = 0

**while** (XMTbl\[(BSindex \* Xsize)+X1index+1\] \<input)

X1index = X1index + 1

**wend**

**Endif**

**If** (input2 \<= XMTb1 \[(BSindex+1) \* Xsize\])

X2index = 0

input2 = XMTbl\[(BSindex + 1) \* Xsize \]

**Else if** (input2 \>= XMTbl \[ ((BSindex +1) \* Xsize) + Xsize -1\])

X2index = Xsize -2

input2 = XMTbl\[((BSindex +1)\*Xsize) + Xsize -1\]

**while**
((XMTbl\[((BSindex+1)\*Xsize)+X2index\]==XMTbl\[((BSindex+1)\*Xsize)+X2index+1\])
&& (X2index \>0))

X2index = X2index – 1

**wend**

**Else**

X2index = 0

**while** ( XMTbl\[((BSindex+1)\*Xsize)+X2index+1\]\<input2)

X2index = X2index +1

**wend**

**Endif**

ArrayIndex1 = (BSindex \* Xsize) + X1index

ArrayIndex2 = (BSindex \* Xsize) + X1index + 1

ArrayIndex3 = ((BSindex +1)\* Xsize) + X2index

ArrayIndex4 = ((BSindex +1)\*Xsize)+X2index+1

XInputDiff1 = input – XMTbl\[ArrayIndex1\]

XInputDiff2 = input2 – XMTbl\[ArrayIndex3\]

BSInputDiff = BS – BSTbl\[BSindex\]

Mult1_s32 = XInputDiff1 \* (XMTbl\[ArrayIndex4\] – XMTbl\[ArrayIndex3\])

Mult2_s32 = BSInputDiff \* (XMTbl\[ArrayIndex2\] – XMTbl\[ArrayIndex1\])

Den1_s32 = (XMTbl\[ArrayIndex4\]-XMTbl\[ArrayIndex3\])

Den2_s32 = (XMTbl\[ArrayIndex2\] – XMTbl\[ArrayIndex1\])

Den3_s32 = (BSTbl\[BSindex +1\]-BSTbl\[BSindex\])

**Numerator_f32** = Mult1_s32 \* (BSTbl\[BSindex+1\]-BS) \*

(YMTbl\[ArrayIndex2\]-YMTbl\[ArrayIndex1\]) +

Mult2_s32\*(XMTbl\[ArrayIndex4\] – XMTbl\[ArrayIndex3\]) \*

(YMTbl\[ArrayIndex3\] – YMTbl\[ArrayIndex1\]) +

Mult2_s32 \* XInputDiff2\*(YMTbl\[ArrayIndex4\] – YMTbl\[ArrayIndex3\])

**Denominator_f32** = (Den1_s32 \* Den2_s32) \* Den3_s32

If (Denominator_f32 \<= FLT_EPSILON)

Output_u16 = YMTbl\[ArrayIndex1\] + 0.5

Else

> Output_u16 = YMTbl\[ArrayIndex1\] + (Numerator_f32 /
> Denominator_f32) + 0.5

Endif

return Output_u16

end

### Syntax: BilinearXMYM_s16_u16XMs16YM_Cnt(BS, input, \*BSTbl, BSsize, \*XMTbl, \*YMTbl, Xsize)

Arguments:

1.  BS:- Bilinear Selector

2.  input:-The input to the table

3.  BSTbl:- Bilinear Selector Table 2D

4.  BSize:- Bilinear Selector Table Size

5.  XTbl:- Table X with \[MxN\] dimension

6.  YMTbl:- Table Y with \[MxN\] dimension

7.  Xsize:- Size of XTbl

Output:- The output from the table

Pseudo Code:

UINT16 BSindex, X1index, X2index

UINT16 ArrayIndex1, ArrayIndex2, ArrayIndex3, ArrayIndex4

SINT32 BSInputDiff, XInputDiff1, XInputDiff2

SINT32 Mult1_s32, Mult2_s32

FLOAT32 Numerator_f32, Denominator_f32

SINT16 Output_s16

SINT32 Den1_s32, Den2_s32, Den3_s32

UINT16 input2 = input

FLOAT32 Output_f32

Const UINT16 BSTbl = \[z1,z2,z3,z4,…..\]

Const UINT16 XTbl\[mxn\] = \[(x1,x2,x3…),(x4,x5,x6….),….\]

Const SINT16 YMTbl\[mxn\] = \[(y1,y2,y3…),(y4,y5,y6….),….\]

**If** ( BS \<= BSTbl\[0\])

BSindex = 0

BS = BSTbl\[0\]

**Else if** (BS \>= BSTbl\[BSsize -1\])

BSindex = BSsize – 2

BS = BSTbl \[ BSsize – 1\]

**While** ( BSTbl\[BSindex\] == BSTbl\[BSindex + 1\] && (BSindex \>0))

BSindex = BSindex – 1

**Wend**

**Else**

BSindex = 0

**While** (BSTbl\[BSindex +1\] \< BS)

BSindex = BSindex +1

**Wend**

**Endif**

**If** (input \<= XMTbl\[BSindex \* Xsize \] )

X1index =0

input = XMTbl\[BSindex \* Xsize\]

**else if** (input \>= XMTbl\[(BSindex \* Xsize) + Xsize -1\])

X1index = Xsize -2

input = XMTbl\[(BSindex \* Xsize) + Xsize -1\]

**while** (( XMTbl\[(BSindex \* Xsize) + X1index\] == XMTbl\[(BSindex \*
Xsize) +X1index+1\]) && (X1index \> 0))

X1index =X1index – 1

**Wend**

**Else**

X1index = 0

**While** (XMTbl\[(BSindex \* Xsize)+X1index+1\] \< input)

X1index = X1index +1

**Wend**

**Endif**

**If** (input2 \<= XMTbl\[(BSindex+1) \* Xsize\])

X2index =0

Input2 = XMTbl\[(BSindex+1)\* Xsize\]

**Else if** (input2 \>= XMTbl\[(BSindex+1) \* Xsize) + XSize-1\])

X2index = Xsize – 2

input2 = XMTbl\[((BSindex +1)\*Xsize)+Xsize – 1\]

**while** ((XMTbl\[((BSindex+1)\*Xsize)+X2index\] == XMTbl\[((BSindex+1)
\* Xsize)+X2index+1\]) && (X2index \>0))

X2index = X2index – 1

**Wend**

**Else**

X2index =0

**While** (XMTbl\[((Bsindex+1)\* Xsize) + X2index +1\] \< input2)

X2index= X2index+1

**Wend**

**Endif**

ArrayIndex1 = (BSindex \* Xsize) + X1index

ArrayIndex2 = (BSindex \* Xsize) + X1index + 1

ArrayIndex3 = ((BSindex+1)\*Xsize)+X2index

ArrayIndex4 = ((BSindex + 1)\*Xsize) + X2index+1

XInputDiff1 = input – XMTbl\[ArrayIndex1\]

XInputDiff2 = input2 – XMTbl\[ArrayIndex3\]

BSInputDiff = BS – BSTbl\[BSindex\]

Mult1_s32 = XInputDiff1 \* (XMTbl\[ArrayIndex4\] – XMTbl\[ArrayIndex3\])

Mult2_s32 = BSinputDiff \* (XMTbl\[ArrayIndex2\] – XMTbl\[ArrayIndex1\])

Den1_s32 = (XMTbl\[ArrayIndex4\] - XMTbl\[ArrayIndex3\])

Den2_s32 = (XMTbl\[ArrayIndex2\] – XMTbl\[ArrayIndex1\])

Den3_s32 = (BSTbl\[BSindex+1\] – BSTbl\[BSindex\])

**Numerator_f32** = Mult1_s32 \* ((BSTbl\[BSindex+1\]-BS) \*
(YMTbl\[ArrayIndex2\] – YMTbl\[ArrayIndex1\]) +

Mult2_s32 \* (XMTbl\[ArrayIndex4\]-XMTbl\[ArrayIndex3\])\*

YMTbl\[ArrayIndex3\] – YMTbl\[ArrayIndex1\]) +

Mult2_s32\*XInputDiff2\*(YMTbl\[ArrayIndex4\]-YMTbl\[ArrayIndex3\])

**Denominator_f32** = (Den1_s32 \* Den2_s32) \* Den3_s32

**If** (Denominator_f32 \<= FLT_EPSILON)

Output_f32 = YMTbl\[ArrayIndex1\]

**Else**

Output_f32 = YMTbl\[ArrayIndex1\]+Numerator_f32/Denominator_f32

**Endif**

**If** (Output_f32 \>= 0)

Output_f32 = Output_f32 +0.5

**Else**

Output_f32 = Output_f32 -0.5

**Endif**

/\*float to SINT16 typecasting\*/

Output_s16 = Output_f32

return Output_s16

**end**

**4.1.3 Syntax:** BilinearXMYM_s16_s16XMs16YM_Cnt(BS, input, \*BSTbl,
BSsize, \*XMTbl, \*YMTbl, Xsize)

Arguments:

1.  BS:- Bilinear Selector

2.  input:-The input to the table

3.  BSTbl:- Bilinear Selector Table 2D

4.  BSize:- Bilinear Selector Table Size

5.  XTbl:- Table X with \[MxN\] dimension

6.  YMTbl:- Table Y with \[MxN\] dimension

7.  Xsize:- Size of XTbl

Output:- The output from the table

Pseudo Code:

UINT16 BSindex, X1index, X2index

UINT16 ArrayIndex1, ArrayIndex2, ArrayIndex3, ArrayIndex4

SINT32 BSInputDiff, XInputDiff1, XInputDiff2

SINT32 Mult1_s32, Mult2_s32

FLOAT32 Numerator_f32, Denominator_f32

SINT16 Output_s16

SINT32 Den1_s32, Den2_s32, Den3_s32

SINT16 input2 = input

FLOAT32 Output_f32

Const UINT16 BSTbl = \[z1,z2,z3,z4,…..\]

Const SINT16 XTbl\[mxn\] = \[(x1,x2,x3…),(x4,x5,x6….),….\]

Const SINT16 YMTbl\[mxn\] = \[(y1,y2,y3…),(y4,y5,y6….),….\]

**If** (BS \<= BSTbl\[0\])

BSindex = 0

BS = BSTbl\[0\]

**Else if** (BS \>= BSTbl\[BSsize-1\]

BSindex = BSsize – 2

BS = BSTbl\[BSsize – 1\]

**While** ( BSTbl\[BSindex\] == BSTbl\[BSindex+1\] && (BSindex \>0))

BSindex = BSindex -1

**Wend**

**Else**

BSindex = 0

**While** (BSTbl\[BSindex+1\] \< BS)

BSindex = BSindex +1

**Wend**

**Endif**

**If** (input \<= XMTbl\[BSindex \* Xsize\])

X1index = 0

input = XMTbl\[BSindex \* Xsize\]

**else if** (input \>= XMTbl\[(BSindex \* Xsize) + Xsize – 1\])

X1index = Xsize-2

input = XMTbl\[(BSindex\*Xsize)+Xsize-1\]

**while** ((XMTbl\[(BSindex\*Xsize)+X1index\] = = XMTbl\[(BSindex \*
Xsize)+X1index+1\]) && (X1index \> 0))

X1index = X1index-1

**Wend**

**Else**

X1index = 0

**While** ( XMTbl\[(BSindex \* Xsize) + X1index+1\] \< input)

X1index = X1index+1

**Wend**

**Endif**

**If** (input2 \<= XMTbl\[(BSindex+1)\*Xsize\])

X2index = 0

input2= XMTbl\[(BSindex+1)\*Xsize\]

**else if** (input2 \>= XMTbl\[((BSindex+1)\*Xsize)+Xsize-1\])

X2index = Xsize-2

input2 = XMTbl\[((BSindex+1)\*Xsize)+Xsize-1\]

**while** (( XMTbl\[(BSindex+1)\*Xsize) + X2index\] ==
XMTbl\[((BSindex+1)\*Xsize)+X2index+1\]) && (X2index \> 0))

X2index = X2index-1

**Wend**

**Else**

X2index = 0

**While** ( XMTbl\[((BSindex+1)\*Xsize)+X2index+1\] \< input2)

X2index = X2index+1

**Wend**

**Endif**

ArrayIndex1 = (BSindex \* Xsize) + X1index

ArrayIndex2 = (BSindex \* Xsize) + X1index + 1

ArrayIndex3 = ((BSindex +1)\*Xsize)+X2index

ArrayIndex4 = ((BSindex + 1)\*Xsize)+X2index+1

XInputDiff1 = input – XMTbl\[ArrayIndex1\]

XInputDiff2 = inpu2 – XMTbl\[ArrayIndex3\]

BSInputDiff = BS – BSTbl\[BSindex\]

Mult1_s32 = XInputDiff1 \* (XMTbl\[ArrayIndex4\] – XMTbl\[ArrayIndex3\])

Mult2_s32 = BSInputDiff \* (XMTbl\[ArrayIndex2\] – XMTbl\[ArrayIndex1\])

Den1_s32 = (XMTbl\[ArrayIndex4\] – XMTbl\[ArrayIndex3\])

Den2_s32 = (XMTbl\[ArrayIndex2\] – XMTbl\[ArrayIndex1\])

Den3_s32 = (BSTbl\[BSindex + 1\] – BSTbl\[BSindex\])

**Numerator_f32** = Mult1_s32 \* ((BSTbl\[BSindex+1\]-BS)\*
(YMTbl\[ArrayIndex2\]-YMTbl\[ArrayIndex1\])+

Mult2_s32 \* (XMTbl\[ArrayIndex4\]-XMTbl\[ArrayIndex3\]) \*

(YMTbl\[ArrayIndex3\] – YMTbl\[ArrayIndex1\]) +

Mult2_s32 \* XInputDiff2 \* (YMTbl\[ArrayIndex4\] –
YMTbl\[ArrayIndex3\])

**Denominator_f32** = (Den1_s32 \* Den2_s32) \* Den3_s32

**If** (Denominator_f32 \<= FLT_EPSILON)

Output_f32 = YMTbl\[ArrayIndex1\]

**Else**

Output_f32 = YMTbl\[ArrayIndex1\] + Numerator_f32 / Denominator_f32

**Endif**

**If** (Output_f32 \>= 0)

Output_f32 = Output_f32 +0.5

**Else**

Output_f32 = Output_f32 – 0.5

**Endif**

/\*float to SINT16 typecast\*/

Output_s16 = Output_f32

return Output_s16

**end**

### Syntax: BilinearXMYM_u16_s16XMu16YM_Cnt( BS, input, \*BSTbl, BSsize, \*XMTbl, \*YMTbl, Xsize)

Arguments:

1.  BS:- Bilinear Selector

2.  input:-The input to the table

3.  BSTbl:- Bilinear Selector Table 2D

4.  BSize:- Bilinear Selector Table Size

5.  XTbl:- Table X with \[MxN\] dimension

6.  YMTbl:- Table Y with \[MxN\] dimension

7.  Xsize:- Size of XTbl

Output:- The output from the table

Pseudo Code:

UINT16 BSindex, X1index, X2index,

UINT16 ArrayIndex1, ArrayIndex2, ArrayIndex3, ArrayIndex4

SINT32 BSInputDiff, XInputDiff1, XInputDiff2

SINT32 Mult1_s32, Mult2_s32

FLOAT32 Numerator_f32, Denominator_f32

UINT16 Output_u16

SINT32 Den1_s32, Den2_s32, Den3_s32

UINT16 input2 = input

Const UINT16 BSTbl = \[z1,z2,z3,z4,…..\]

Const UINT16 XTbl\[mxn\] = \[(x1,x2,x3…),(x4,x5,x6….),….\]

Const UINT16 YMTbl\[mxn\] = \[(y1,y2,y3…),(y4,y5,y6….),….\]

**If** ( BS \<= BSTbl\[0\] )

BSindex = 0

BS = BSTbl \[0\]

**Else if** (BS \>= BSTbl\[BSsize -1\])

BSindex = BSsize – 2

BS = BSTbl \[ BSsize-1\]

**while** (BSTbl\[BSindex\] == BSTbl\[BSindex+1\] && (BSindex \> 0))

BSindex = BSindex -1

**wend**

**Else**

BSindex = 0

**while** ( BSTbl \[ BSindex +1\] \< BS)

BSindex = BSindex +1

**wend**

**Endif**

**If** ( input \<= XMTbl \[ BSindex \* Xsize\])

X1index = 0

Input = XMTbl \[BSindex \* Xsize\]

**Else if** (input \>= XMTbl \[ (BSindex \* Xsize) + Xsize -1\])

X1index = Xsize – 2

> input = XMTbl \[ (BSindex \* Xsize) + Xsize – 1\]
>
> **while** ((XMTbl\[(BSindex \* Xsize)+X1index\] == XMTbl\[(BSindex \*
> Xsize) + X1index +1\]) && (X1index \>0))
>
> X1index = X1index – 1
>
> **wend**

**Else**

X1index = 0

**while** (XMTbl\[(BSindex \* Xsize)+X1index+1\] \<input)

X1index = X1index + 1

**wend**

**Endif**

**If** (input2 \<= XMTb1 \[(BSindex+1) \* Xsize\])

X2index = 0

input2 = XMTbl\[(BSindex + 1) \* Xsize \]

**Else if** (input2 \>= XMTbl \[ ((BSindex +1) \* Xsize) + Xsize -1\])

X2index = Xsize -2

input2 = XMTbl\[((BSindex +1)\*Xsize) + Xsize -1\]

**while**
((XMTbl\[((BSindex+1)\*Xsize)+X2index\]==XMTbl\[((BSindex+1)\*Xsize)+X2index+1\])
&& (X2index \>0))

X2index = X2index – 1

**wend**

**Else**

X2index = 0

**while** ( XMTbl\[((BSindex+1)\*Xsize)+X2index+1\]\<input2)

X2index = X2index +1

**wend**

**Endif**

ArrayIndex1 = (BSindex \* Xsize) + X1index

ArrayIndex2 = (BSindex \* Xsize) + X1index + 1

ArrayIndex3 = ((BSindex +1)\* Xsize) + X2index

ArrayIndex4 = ((BSindex +1)\*Xsize)+X2index+1

XInputDiff1 = input – XMTbl\[ArrayIndex1\]

XInputDiff2 = input2 – XMTbl\[ArrayIndex3\]

BSInputDiff = BS – BSTbl\[BSindex\]

Mult1_s32 = XInputDiff1 \* (XMTbl\[ArrayIndex4\] – XMTbl\[ArrayIndex3\])

Mult2_s32 = BSInputDiff \* (XMTbl\[ArrayIndex2\] – XMTbl\[ArrayIndex1\])

Den1_s32 = (XMTbl\[ArrayIndex4\]-XMTbl\[ArrayIndex3\])

Den2_s32 = (XMTbl\[ArrayIndex2\] – XMTbl\[ArrayIndex1\])

Den3_s32 = (BSTbl\[BSindex +1\]-BSTbl\[BSindex\])

**Numerator_f32** = Mult1_s32 \* (BSTbl\[BSindex+1\]-BS) \*

(YMTbl\[ArrayIndex2\]-YMTbl\[ArrayIndex1\]) +

Mult2_s32\*(XMTbl\[ArrayIndex4\] – XMTbl\[ArrayIndex3\]) \*

(YMTbl\[ArrayIndex3\] – YMTbl\[ArrayIndex1\]) +

Mult2_s32 \* XInputDiff2\*(YMTbl\[ArrayIndex4\] – YMTbl\[ArrayIndex3\])

**Denominator_f32** = (Den1_s32 \* Den2_s32) \* Den3_s32

If (Denominator_f32 \<= FLT_EPSILON)

Output_u16 = YMTbl\[ArrayIndex1\] + 0.5

Else

> Output_u16 = YMTbl\[ArrayIndex1\] + (Numerator_f32 /
> Denominator_f32) + 0.5

Endif

return Output_u16

end

# UnitTesting Range: Linear and Bilinear Interpolation 

> For unit testing consider Ranges as **FULL** based on the data type of
> the tables and Input. Note a limitation for all interpolation
> functions is that the X tables and the BS Tables are assumed to be
> always increasing in value (or equal). The tables should never be
> decreasing in values as the index increases.

# Revision Control Log

|             |            |                                                                                             |             |                     |
|------|--------|-----------------------------------------|----------|---------|
| **Item \#** | **Rev \#** | **Change Description**                                                                      | **Date**    | **Author Initials** |
| 1           | CBD        | Interpolation MDD                                                                           | 13 April 12 | NRAR                |
| 2           | 2          | Added remaining bilinear interpolation functions                                            | 28-Sep-12   | OT                  |
| 3           | 3          | Changed divide by zero logic in bilinear interpolation to prevent floating point exceptions | 21-Mar-13   | LWW                 |
| 4           | 4          | Updated pseudo code for the corrections for anomalies EA3#530 and EA3#191                   | 06-May-15   | KJS                 |

{% endraw %}