---
layout: default
title: Filter_Library_Design_Document
nav_order: 1
parent: Nexteer Library
---
{% raw %}
[1 Partial Notch Filter 3](#partial-notch-filter)

[1.1 Filter Equations 3](#filter-equations)

[1.1.1 Node b State Variable Initialization
3](#node-b-state-variable-initialization)

[1.1.2 Node d State Variable Initialization
3](#node-d-state-variable-initialization)

[1.1.3 Filter Output Calculation 3](#filter-output-calculation)

[1.1.4 Node b State Variable Calculation
3](#node-b-state-variable-calculation)

[1.1.5 Node d State Variable Calculation
3](#node-d-state-variable-calculation)

[1.1.6 Filter Output Calculation 4](#filter-output-calculation-1)

[1.2 Library Routines Design 4](#library-routines-design)

[1.2.1 Notch Filter Initialization Function
4](#notch-filter-initialization-function)

[1.2.2 Notch Filter State Variable Update Function
4](#notch-filter-state-variable-update-function)

[1.2.3 Notch Filter Output Update Function
4](#notch-filter-output-update-function)

[1.2.4 Notch Filter Full Update Function
5](#notch-filter-full-update-function)

[1.3 Notch Filter Structure Acceptable Ranges
5](#notch-filter-structure-acceptable-ranges)

[1.4 Usage 6](#usage)

[2 1^st^ Order Low Pass Filter, 1 Pole- coefficient
7](#st-order-low-pass-filter-1-pole--coefficient)

[2.1 Topology 1 – 1LP1-C 7](#topology-1-1lp1-c)

[2.1.1 Filter Equations 8](#filter-equations-1)

[2.1.2 Library Routines Design 8](#library-routines-design-1)

[2.1.2.1 Unity Gain, No Dead band Compensation, Fixed K – calibratable
Kn, fixed 16 bit Kd, 32 Bit State Variable, Truncate divide, Unsigned 16
bit Input
8](#unity-gain-no-dead-band-compensation-fixed-k-calibratable-kn-fixed-16-bit-kd-32-bit-state-variable-truncate-divide-unsigned-16-bit-input)

[2.1.2.2 Unity Gain, No Dead band Compensation, Fixed K – calibratable
Kn, fixed 16 bit Kd, 32 Bit State Variable, Truncate divide, Signed 16
bit Input
11](#unity-gain-no-dead-band-compensation-fixed-k-calibratable-kn-fixed-16-bit-kd-32-bit-state-variable-truncate-divide-signed-16-bit-input)

[2.2 Topology 2 – 1LP1-B 14](#topology-2-1lp1-b)

[2.2.1 Filter Equations 14](#filter-equations-2)

[2.2.2 Library Routines Design 15](#library-routines-design-2)

[2.2.2.1 Variable Gain, Variable D, Variable K – calibratable 16 bit Kn,
variable Kd, 32 Bit State Variable, Truncate divide, Unsigned 16 bit
Input
15](#variable-gain-variable-d-variable-k-calibratable-16-bit-kn-variable-kd-32-bit-state-variable-truncate-divide-unsigned-16-bit-input)

[2.2.2.2 Variable Gain, Variable D, Variable K - calibratable 16 bit Kn,
variable Kd, 32 Bit State Variable, Truncate divide, Signed 16 bit Input
17](#variable-gain-variable-d-variable-k---calibratable-16-bit-kn-variable-kd-32-bit-state-variable-truncate-divide-signed-16-bit-input)

[2.3 Topology 3 – 1LP1-CF (Floating Point Implementation)
20](#topology-3-1lp1-cf-floating-point-implementation)

[2.3.1 Filter Equations 20](#filter-equations-3)

[2.3.1.1 Coefficient K Calculation and State Variable Initialization
20](#coefficient-k-calculation-and-state-variable-initialization)

[2.3.1.2 Coefficient K Recalculation 20](#coefficient-k-recalculation)

[2.3.1.3 Normal Operation 20](#normal-operation)

[2.3.2 Library Routines Design 21](#library-routines-design-3)

[2.3.2.1 Unity Gain, No Dead band Compensation, calibratable K,
Single-Precision Float Input
21](#unity-gain-no-dead-band-compensation-calibratable-k-single-precision-float-input)

[3 1^st^ Order High Pass Filter, 1 Pole- coefficient
23](#st-order-high-pass-filter-1-pole--coefficient)

[3.1 Topology 1 – HP-CF (Floating Point Implementation)
23](#topology-1-hp-cf-floating-point-implementation)

[3.1.1 Filter Equations 23](#filter-equations-4)

[3.1.1.1 Coefficient K Calculation and State Variable Initialization
23](#__RefHeading___Toc323024662)

[3.1.1.2 Coefficient K Recalculation 23](#__RefHeading___Toc323024663)

[3.1.1.3 Normal Operation 23](#normal-operation-1)

[3.1.2 Library Routines Design 24](#library-routine-design)

[3.1.2.1 Unity Gain, No Dead band Compensation, calibratable K,
Single-Precision Float Input
24](#unity-gain-no-dead-band-compensation-calibratable-k-single-precision-float-input-1)

[4 Revision Control Log 26](#revision-control-log)

# Partial Notch Filter

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NxtrLib/doc/mediax/media/image1.png"
style="width:5.99306in;height:3.09583in" />

## Filter Equations

The first three equations, 1.1.1, 1.1.2, and 1.1.3 shall be combined
into a single Notch Filter Initialization function. The next two
equations 1.1.4 and 1.1.5 shall be combined into a single state variable
update function. Finally, equation 1.1.6 shall be standalone as the
output update function. For convenience, the last two function, state
variable update and output update shall be combined into a single inline
function to provide a single call from the modules \_per() sub-module.

### Node b State Variable Initialization

> SV2 = In \* (B2 - A2);

### Node d State Variable Initialization

> SV1 = In \* (B1 + B2 - A1 - A2);

### Filter Output Calculation

> Out = In;

### Node b State Variable Calculation

SV2 = (B2 \* In) - (Out \* A2);

### Node d State Variable Calculation

SV1 = (SV2 + (In \* B1)) - (Out \* A1);

### Filter Output Calculation

> Out = SV1 + (B0 \* In);

## Library Routines Design

### Notch Filter Initialization Function

|                      |                                                    |                 |             |     |          |
|---------------|------------------------------|-----------|------|------|------|
| **Function Name**    | NF_Init_f32                                        | Type            | Min         | Max | UTP Tol. |
| **Arguments Passed** | In_Uls_T_f32 – Initial input to the filter         | Float 32        |             |     |          |
|                      | SVPtr_Cnt_T_Str – Pointer to state variable struct | NotchFiltSV_Str |             |     |          |
|                      | FiltK_Cnt_T_Str – Pointer to coefficient structure | NotchFiltK_Str  | \*\*See 1.3 |     |          |
| **Return Value**     | N/A                                                |                 |             |     |          |

**Pseudo Code:**

> KPtr_Cnt_Str = FiltK_Cnt_T_Str;
>
> Out = In;
>
> SV1 = In \* (B1 + B2 - A1 - A2);
>
> SV2 = In \* (B2 - A2);

### Notch Filter State Variable Update Function

|                      |                                                    |                 |             |     |          |
|---------------|------------------------------|-----------|------|------|------|
| **Function Name**    | NF_SvUpdate_f32                                    | Type            | Min         | Max | UTP Tol. |
| **Arguments Passed** | In_Uls_T_f32 – Input to notch filter               | Float 32        |             |     |          |
|                      | SVPtr_T_Cnt_Str – Pointer to state variable struct | NotchFiltSV_Str | \*\*See 1.3 |     |          |
|                      | FiltK_Cnt_T_Str – Pointer to filter cal struct     | NotchFiltK_Str  | \*\*See 1.3 |     |          |
| **Return Value**     | N/A                                                |                 |             |     |          |

**Pseudo Code:** KPtr_Cnt_Str = FiltK_Cnt_T_Str

> SV1 = (SV2 + (In \* B1)) - (Out \* A1);
>
> SV2 = (B2 \* In) - (Out \* A2);

### Notch Filter Output Update Function

|                      |                                                    |                 |             |     |          |
|--------------|------------------------------|-----------|------|------|------|
| **Function Name**    | NF_OpUpdate_f32                                    | Type            | Min         | Max | UTP Tol. |
| **Arguments Passed** | In_Uls_T_f32 – Input to the notch filter           | Float 32        |             |     |          |
|                      | SVPtr_T_Cnt_Str – Pointer to state variable struct | NotchFiltSV_Str | \*\*See 1.3 |     |          |
| **Return Value**     | Filtered Output, SV Structure Updated              | Float 32        |             |     |          |

**Pseudo Code:**

Out = SV1 + (B0 \* In);

### Notch Filter Full Update Function

|                      |                                                    |                 |             |     |          |
|--------------|------------------------------|-----------|------|------|------|
| **Function Name**    | NF_FullUpdate_f32                                  | Type            | Min         | Max | UTP Tol. |
| **Arguments Passed** | In_Uls_T_f32 – Input to notch filter               | Float 32        |             |     |          |
|                      | SVPtr_Cnt_T_Str – Pointer to state variable struct | NotchFiltSV_Str | \*\*See 1.3 |     |          |
|                      | FiltK_Cnt_T_Str – Pointer to filter cal struct     | NotchFiltK_Str  | \*\*See 1.3 |     |          |
| **Return Value**     | Filtered output                                    | Float 32        |             |     |          |

**Pseudo Code:**

Full Update simply calls OpUpdate followed by SvUpdate as a convenient
alternative to calling each of the functions individually.

#  [section]

## Notch Filter Structure Acceptable Ranges

|                    |                 |              |               |      |          |
|--------------|------------------------------|-----------|------|------|------|
| **Structure Name** | NotchFiltSV_Str | Type         | Min           | Max  | UTP Tol. |
| **Members**        | SV1_Uls_f32     | Float 32     | FULL          | FULL |          |
|                    | SV2_Uls_f32     | Float 32     | FULL          | FULL |          |
|                    | Out_Uls_f32     | Float 32     | FULL          | FULL |          |
|                    | KPtr_Cnt_Str    | KPtr_Cnt_Str | \*\*See Below |      |          |

|                    |                |          |     |     |          |
|--------------------|----------------|----------|-----|-----|----------|
| **Structure Name** | NotchFiltK_Str | Type     | Min | Max | UTP Tol. |
| **Members**        | A1_Uls_f32     | Float 32 |     |     |          |
|                    | A2_Uls_f32     | Float 32 |     |     |          |
|                    | B0_Uls_f32     | Float 32 |     |     |          |
|                    | B1_Uls_f32     | Float 32 |     |     |          |
|                    | B2_Uls_f32     | Float 32 |     |     |          |

## Usage

For a module that executes a Notch Filter, in its \_Init() sub module
execute the following function.

> NF_Init_f32(\<Input\>, \<SV_Ptr\>, \<FiltK_Ptr\>);

In the same module’s \_Per() sub module execute the following functions
in the given sequence,

> NF_OpUpdate_f32(\<Input\>, \<SV_Ptr\>);
>
> NF_SvUpdate_f32(\<Input\>, \<SV_Ptr\>, \<FiltK_Ptr\>);

Alternatively, a single call to the following function can be made in
place of the above pair within the \_Per() sub module.

> NF_FullUpdate_f32(\<Input\>, \<SV_Ptr\>, \<FiltK_Ptr\>);

# 1^st^ Order Low Pass Filter, 1 Pole- coefficient

## Topology 1 – 1LP1-C

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NxtrLib/doc/mediax/media/image2.wmf"
style="width:5.80208in;height:1.92431in" />The Filter topology 1LP1-C is
as given,

There may be multiple library functions defined for the same topology,
based on the cut-off frequency, and input size requirements.

A filter tool is available to design the low pass filter for this
topology – “1^st^ Order Design,1LP1-B.xls”. This tool provides the bit
sizes for all nodes shown in the filter. The tool must be used to see
which library function is required for the given input, cut-off
frequency, sampling rate, and filter coefficient size.

The above filter topology requires the following constants to be defined

|        |                                   |                                                                                                                                                      |
|---------|----------------|-----------------------------------------------|
| Symbol | Description                       | Constant Classification                                                                                                                              |
| Kn     | Numerator of Filter Coefficient   | This may be defined as a calibration constant or an embedded local constant based on the usage.                                                      |
| Kd     | Denominator of Filter Coefficient | Based on the implementation, this value may be a fixed value, which is embedded within the library function/macro or could be passed as a parameter. |

|                 |                          |
|-----------------|--------------------------|
| **Node Symbol** | **Description**          |
| I               | Input                    |
| e               | State Variable (filt_SV) |
| O               | Output (filt_O)          |

### Filter Equations

The filter equations are given below. Each equation shall be implemented
as a library macro.

**State Variable (Node e) Initialization**

The equation to initialize the state variable, (Node e) is as follows:

filt_SV = Input \* Kd.

**Output (Node O) Initialization**

The equation to initialize the output, (Node O) is as follows:

filt_O = \[( ( Input – (filt_SV / Kd) ) \* Kn ) + filt_SV\] / Kd

**Normal Operation**

During normal operation the state variable (Node e) shall be updated
prior to the output of the filter (Node O) being updated.

The equation for the state variable (Node e) is as follows:

filt_SV = ( ( Input – (filt_SV / Kd) ) \* Kn ) + filt_SV

The equation for the output (Node O) is as follows:

filt_O = filt_SV / Kd

The equations to update filt_Sv and filt_O or the library routines that
calculate these values should be executed in the exact order shown
above.

### Library Routines Design

#### Unity Gain, No Dead band Compensation, Fixed K – calibratable Kn, fixed 16 bit Kd, 32 Bit State Variable, Truncate divide, Unsigned 16 bit Input

There will be four macros defined for this implementation:- state
variable initialization, filter output initialization, state variable
update and filter output update.

|                 |                          |               |
|-----------------|--------------------------|---------------|
| **Node Symbol** | **Description**          | **Data Type** |
| I               | Input                    | UINT 16       |
| c               |                          | UINT16        |
| d               |                          | UINT32        |
| e               | State Variable (filt_SV) | UINT 32       |
| f               |                          | UINT16        |
| O               | Output (filt_O)          | UINT 16       |

##### State Variable Initialization Macro

|                      |                                      |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_SvInit_u16InFixKTrunc_m          | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter | UINT16 |     |     |          |
| **Return Value**     | Initialized value of node e          | UINT32 |     |     |          |

**Pseudo Code**:

Lvalue = Input \<\< Kd

where Kd is pre-defined for a fixed16 bit filter coefficient = 16 bits

##### Filter Output Initialization Macro

|                      |                                                   |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_OpInit_u16InFixKTrunc_m                       | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter              | UINT16 |     |     |          |
|                      | Filt_SV – Initialized value of the state variable | UINT32 |     |     |          |
|                      | Kn - Numerator of the filter coefficient          | UINT16 |     |     |          |
| **Return Value**     | Initialized output of the low pass filter         | UINT32 |     |     |          |

**Pseudo Code**:

Lvalue = (((Input – (Filt_SV \>\> Kd)) \* Kn ), + Filt_SV)\>\>Kd

where Kd is pre-defined for a fixed16 bit filter coefficient = 16 bits

##### Filter State Variable Update Macro

|                      |                                                  |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_SvUpdate_u16InFixKTrunc_m                    | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter             | UINT16 |     |     |          |
|                      | Filt_SV – Calculated value of the state variable | UINT32 |     |     |          |
|                      | Kn - Numerator of the filter coefficient         | UINT16 |     |     |          |
| **Return Value**     | Output of the low pass filter                    | UINT32 |     |     |          |

**Pseudo code:**

\<Lvalue\> = ( ( Input – (filt_SV \>\> Kd) ) \* Kn ) + filt_SV

where Kd is pre-defined for a fixed16 bit filter coefficient = 16 bits

##### Output Update Macro

|                      |                                                  |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_OpUpdate_u16InFixKTrunc_m                    | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Filt_SV – Calculated value of the state variable | UINT32 |     |     |          |
| **Return Value**     | Output of the low pass filter                    | UINT16 |     |     |          |

**Pseudo code:**

\<Lvalue\> = filt_SV \>\> Kd

where Kd is pre-defined for a 16 bit filter coefficient = 16 bits

##### **Usage**

For a module that executes a LPF, in its \_Init() sub module execute the
following macros in the given sequence

> LPF_SvInit_u16InFixKTrunc_m (\<Input\>)
>
> LPF_OpInit_u16InFixKTrunc_m (\<Input\>, \<Filt_SV\>, \<Kn\>)

In the same module’s \_Per() sub module execute the following macros in
the given sequence,

> LPF_SvUpdate_u16InFixKTrunc_m (\<Input\>, \<filt_SV\>, \<Kn\>)
>
> LPF_OpUpdate_u16InFixKTrunc_m ( \<filt_SV\>)

#### Unity Gain, No Dead band Compensation, Fixed K – calibratable Kn, fixed 16 bit Kd, 32 Bit State Variable, Truncate divide, Signed 16 bit Input

There will be three macros defined for this implementation:- state
variable initialization, state variable update and filter output update.

|                 |                          |               |
|-----------------|--------------------------|---------------|
| **Node Symbol** | **Description**          | **Data Type** |
| I               | Input                    | SINT 16       |
| c               |                          | SINT 16       |
| d               |                          | SINT 32       |
| e               | State Variable (filt_SV) | SINT 32       |
| f               |                          | SINT 16       |
| O               | Output (filt_O)          | SINT 16       |

##### State Variable Initialization Macro

|                      |                                      |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_SvInit_s16InFixKTrunc_m          | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter | SINT16 |     |     |          |
| **Return Value**     | Initilized value of Node e           | SINT32 |     |     |          |

**Pseudo Code**:

Lvalue = Input \<\< Kd

where Kd is pre-defined for a 16 bit filter coefficient as 16 bits

##### Filter Output Initialization Macro 

|                      |                                                   |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_OpInit_s16InFixKTrunc_m                       | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter              | SINT16 |     |     |          |
|                      | Filt_SV – Initialized value of the state variable | SINT32 |     |     |          |
|                      | Kn – Numerator of the filter coefficient          | SINT16 |     |     |          |
| **Return Value**     | Initialized value of filter output                | SINT32 |     |     |          |

**Pseudo Code**:

Lvalue = (((Input – (Filt_SV \>\> Kd)) \* Kn ), + Filt_SV)\>\>Kd

where Kd is pre-defined for a fixed16 bit filter coefficient = 16 bits

##### Filter State Variable Update Macro

|                      |                                                   |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_SvUpdate_s16InFixKTrunc_m                     | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter              | SINT16 |     |     |          |
|                      | Filt_SV – Initialized value of the state variable | SINT32 |     |     |          |
|                      | Kn – Numerator of the filter coefficient          | SINT16 |     |     |          |
| **Return Value**     | Calculated value of filt_SV                       | SINT32 |     |     |          |

**Pseudo code:**

\<Lvalue\> = ( ( Input – (filt_SV \>\> Kd) ) \* Kn ) + filt_SV

where Kd is pre-defined for a 16 bit filter coefficient = 16 bits

##### Output Update Macro

|                      |                                                     |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_OpUpdate_s16InFixKTrunc_m                       | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Filt_SV – calculated value of filter state variable | SINT32 |     |     |          |
| **Return Value**     | Output of the low pass filter                       | SINT16 |     |     |          |

**Pseudo code:**

\<Lvalue\> = filt_O \>\> Kd

where Kd is pre-defined for a 16 bit filter coefficient = 16

##### **Usage**

For a module that executes a LPF, in its \_Init() sub module execute the
following macros in the given sequence

> LPF_SvInit_s16InFixKTrunc_m (\<Input\>)
>
> LPF_OpInit_s16InFixKTrunc_m (\<Input\>, \<Filt_SV\>, \<Kn\>)

In the same module’s \_Per() sub module execute the following macros in
the given sequence

> LPF_SvUpdate_s16InFixKTrunc_m (\<Input\>, \<filt_SV\>, \<Kn\>)
>
> LPF_OpUpdate_s16InFixKTrunc_m ( \<filt_SV\>)

##   [section-1]

## Topology 2 – 1LP1-B

The filter topology 1LP1-B is as given,

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NxtrLib/doc/mediax/media/image3.wmf"
style="width:5.99444in;height:1.26806in" />

### Filter Equations

The filter equations are given below. Each equation shall be implemented
as a library macro.

**State Variable (Node e) Initialization**

The equation to initialize the state variable, (Node e) is as follows:

filt_SV = Input \* G \* Kd \* D

**Output (Node O) Initialization**

The equation to initialize the output, (Node O) is as follows:

filt_O = \[( ( (Input \* G \* D) – (filt_SV / Kd) ) \* Kn ) + filt_SV\]
/ (Kd \* D)

**Normal Operation**

During normal operation the state variable (Node e) shall be updated
prior to the output of the filter (Node O) being updated.

The equation for the state variable (Node e) is as follows:

filt_SV = ( ( (Input \* G \* D) – (filt_SV / Kd) ) \* Kn ) + filt_SV

The equation for the output (Node O) is as follows:

filt_O = filt_SV / (Kd \* D)

The equations to update filt_Sv and filt_O or the library routines that
calculate these values should be executed in the exact order shown
above.

The multiplication for the Filter Input by G shall be implemented
external to the library macros. Thus the Input as used by the macros
shall represent actual filter input \* G, for non unity gain filter
implementation.

*Note: Constraint on this filter is that Node b cannot exceed 16 bits.*

### Library Routines Design

#### Variable Gain, Variable D, Variable K – calibratable 16 bit Kn, variable Kd, 32 Bit State Variable, Truncate divide, Unsigned 16 bit Input

|                 |                          |               |
|-----------------|--------------------------|---------------|
| **Node Symbol** | **Description**          | **Data Type** |
| I               | Input                    | UINT 16       |
| a               |                          | UINT 16       |
| b               |                          | UINT 16       |
| c               |                          | UINT 16       |
| d               |                          | UINT 32       |
| e               | State Variable (filt_SV) | UINT 32       |
| f               |                          | UINT 16       |
| g               |                          | UINT 16       |
| O               | Output (filt_O)          | UINT 16       |

##### State Variable Initialization Macro

|                      |                                             |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_SvInit_u16InVarKTrunc_m                 | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter        | UINT16 |     |     |          |
|                      | Kd – Denominator bits of filter coefficient | UINT16 |     |     |          |
|                      | D – Deadband factor                         | UINT16 |     |     |          |
| **Return Value**     | Initialized value of Node e                 | UINT32 |     |     |          |

**Pseudo Code**:

Lvalue = (Input \<\< Kd) \<\< D

Note:- The multiplication by D shall not be performed for D = 0.

##### Filter Output Initialization Macro

|                      |                                               |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_OpInit_u16InVarKTrunc_m                   | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter          | UINT16 |     |     |          |
|                      | Filt_SV – Initialized value of state variable | UINT32 |     |     |          |
|                      | Kn – Numerator of coefficient                 | UINT16 |     |     |          |
|                      | Kd – Denominator bits of filter coefficient   | UINT16 |     |     |          |
|                      | D – Deadband factor                           | UINT16 |     |     |          |
| **Return Value**     | Low pass filter output                        | UINT32 |     |     |          |

**Pseudo Code**:

Lvalue = \[((((Input\<\<D) – (Filt_SV \>\> Kd)) \* Kn ) +
Filt_SV)\>\>Kd\]\>\>D

Note:- The multiplication and division by D shall not be performed for D
= 0.

##### Filter State Variable Update Macro

|                      |                                                     |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_SvUpdate_u16InVarKTrunc_m                       | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter                | UINT16 |     |     |          |
|                      | Filt_SV – Calculated value of filter state variable | UINT32 |     |     |          |
|                      | Kn – Numerator of coefficient                       | UINT16 |     |     |          |
|                      | Kd – Denominator bits of filter coefficient         | UINT16 |     |     |          |
|                      | D – Deadband factor                                 | UINT16 |     |     |          |
| **Return Value**     | Low pass filter output                              | UINT32 |     |     |          |

**Pseudo code:**

\<Lvalue\> = ( ( (Input \<\< D) – (filt_SV \>\> Kd) ) \* Kn ) + filt_SV

Note:- The multiplication by D shall not be performed for D = 0.

##### Output Update Macro

|                      |                                                     |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_OpUpdate_u16InVarKTrunc_m                       | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Filt_SV – Calculated value of filter state variable | UINT32 |     |     |          |
|                      | Kd – Denominator bits of filter coefficient         | UINT16 |     |     |          |
|                      | D – Deadband factor                                 | UINT16 |     |     |          |
| **Return Value**     | Low pass filter output                              | UINT32 |     |     |          |

**Pseudo code:**

\<Lvalue\> = (filt_SV \>\> Kd ) \>\>D

Note:- The division by D shall not be performed for D = 0.

##### **Usage**

For a module that executes a LPF, in its \_Init() sub module execute the
following macros in the given sequence

> LPF_SvInit_u16InVarKTrunc_m (\<Input\>, \<Kd\>, \<D\>)
>
> LPF_OpInit_u16InVarKTrunc_m (\<Input\>, \<Filt_SV\>, \<Kn\>, \<Kd\>,
> \<D\>)

In the same module’s \_Per() sub module execute the following macros in
the given sequence,

> LPF_SvUpdate_u16InVarKTrunc_m (\<Input\>, \<filt_SV\>, \<Kn\>, \<Kd\>,
> \<D\>)
>
> LPF_OpUpdate_u16InVarKTrunc_m ( \<filt_SV\>, \<Kd\>, \<D\>)

#### Variable Gain, Variable D, Variable K - calibratable 16 bit Kn, variable Kd, 32 Bit State Variable, Truncate divide, Signed 16 bit Input

|                 |                          |               |
|-----------------|--------------------------|---------------|
| **Node Symbol** | **Description**          | **Data Type** |
| I               | Input                    | SINT 16       |
| a               |                          | SINT 16       |
| b               |                          | SINT 16       |
| c               |                          | SINT 16       |
| d               |                          | SINT 32       |
| e               | State Variable (filt_SV) | SINT 32       |
| f               |                          | SINT 16       |
| g               |                          | SINT 16       |
| O               | Output (filt_O)          | SINT 16       |

##### State Variable Initialization Macro

|                      |                                             |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_SvInit_s16InVarKTrunc_m                 | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter        | SINT16 |     |     |          |
|                      | Kd – Denominator bits of filter coefficient | SINT16 |     |     |          |
|                      | D – Deadband factor                         | SINT16 |     |     |          |
| **Return Value**     | Initialized value of Node e                 | SINT32 |     |     |          |

**Pseudo Code**:

Lvalue = (Input \<\< Kd) \<\< D

Note:- The multiplication by D shall not be performed for D = 0.

##### Filter Output Initialization Macro

|                      |                                                      |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_OpInit_s16InVarKTrunc_m                          | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter                 | SINT16 |     |     |          |
|                      | Filt_SV – Initialized value of filter state variable | SINT32 |     |     |          |
|                      | Kn – Numerator of filter coefficient                 | SINT16 |     |     |          |
|                      | Kd – Denominator bits of filter coefficient          | SINT16 |     |     |          |
|                      | D – Deadband factor                                  | SINT16 |     |     |          |
| **Return Value**     | Initialized value of filter output                   | SINT32 |     |     |          |

**Pseudo Code**:

Lvalue = \[((((Input\<\<D) – (Filt_SV \>\> Kd)) \* Kn ), +
Filt_SV)\>\>Kd\]\>\>D

Note:- The multiplication and division by D shall not be performed for D
= 0.

##### Filter State Variable Update Macro

|                      |                                                     |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_SvUpdate_s16InVarKTrunc_m                       | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Input – Input to the low pass filter                | SINT16 |     |     |          |
|                      | Filt_SV – Calculated value of filter state variable | SINT32 |     |     |          |
|                      | Kn – Numerator of filter coefficient                | SINT16 |     |     |          |
|                      | Kd – Denominator bits of filter coefficient         | SINT16 |     |     |          |
|                      | D – Deadband factor                                 | SINT16 |     |     |          |
| **Return Value**     | Calculated value of filt_SV as given below          | SINT32 |     |     |          |

**Pseudo code:**

\<Lvalue\> = ( ( (Input \<\< D) – (filt_SV \>\> Kd) ) \* Kn ) + filt_SV

Note:- The multiplication by D shall not be performed for D = 0.

##### Output Update Macro

|                      |                                                     |        |     |     |          |
|----------------|------------------------------|----------|------|------|------|
| **Function Name**    | LPF_OpUpdate_s16InVarKTrunc_m                       | Type   | Min | Max | UTP Tol. |
| **Arguments Passed** | Filt_SV – Calculated value of filter state variable | SINT32 |     |     |          |
|                      | Kd – Denominator bits of filter coefficient         | SINT16 |     |     |          |
|                      | D – Deadband factor                                 | SINT16 |     |     |          |
| **Return Value**     | Low pass filter output                              | SINT32 |     |     |          |

**Pseudo code:**

\<Lvalue\> = (filt_SV \>\> Kd ) \>\>D

Note:- The division by D shall not be performed for D = 0.

##### **Usage**

For a module that executes a LPF, in its \_Init() sub module execute the
following macros in the given sequence

> LPF_SvInit_s16InVarKTrunc_m (\<Input\>, \<Kd\>, \<D\>)
>
> LPF_OpInit_s16InVarKTrunc_m (\<Input\>, \<Filt_SV\>, \<Kn\>, \<Kd\>,
> \<D\>)

In the same module’s \_Per() sub module execute the following macros in
the given sequence,

> LPF_SvUpdate_s16InVarKTrunc_m (\<Input\>, \<filt_SV\>, \<Kn\>, \<Kd\>,
> \<D\>)
>
> LPF_OpUpdate_s16InVarKTrunc_m ( \<filt_SV\>, \<Kd\>, \<D\>)

## Topology 3 – 1LP1-CF (Floating Point Implementation)

The filter topology 1LP1-CF is as given,

<img
src="ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NxtrLib/doc/mediax/media/image4.png"
style="width:4.17778in;height:1.54167in" />

### Filter Equations

The filter equations are given below. Each equation shall be implemented
as a library macro.

#### Coefficient K Calculation and State Variable Initialization

The equation to calculate the filter coefficient K is as follows: (Where
Fp is in hertz and T is in seconds.)

K = 1 – exp(-2 \* π \* Fp \* T)

And the equation for initialization of the state variable is as follows:

Filt_SV = Input

#### Coefficient K Recalculation

The equation for recalculation of the filter coefficient K is exactly
the same as that defined in the initialization function above.

#### Normal Operation 

The equation for the output (Node O) is as follows:

filt_Out = ( ( Input – prev_SV ) \* K ) + prev_SV

The value of filt_SV is the value of filt_Out from the previous call to
the above function.

### Library Routines Design

#### Unity Gain, No Dead band Compensation, calibratable K, Single-Precision Float Input

There will be three macros defined for this implementation:- state
variable and coefficient initialization, coefficient calculation, and
filter output update.

##### **Coefficient and State Variable** Initialization Macro

|                      |                                                  |              |                 |         |          |
|----------------|----------------------------|-----------|-------|------|------|
| **Function Name**    | LPF_Init_f32_m                                   | Type         | Min             | Max     | UTP Tol. |
| **Arguments Passed** | Input – Initial input to filter                  | Float 32     | FULL            | FULL    |          |
|                      | Fp – Pole cutoff frequency in hertz              | Float 32     | 0.1% 1/T        | 50% 1/T |          |
|                      | T – Sampling interval in seconds                 | Float 32     | 0.00005         | 10      |          |
|                      | SV_Str – Pointer to the state variable structure | LPF32KSV_Str | \*See 2.3.2.1.4 |         |          |
| **Return Value**     | Initial output, node O                           | Float 32     | FULL            | FULL    |          |

**Pseudo Code**:

\<SV_Str-\> SV_Uls_f32\> = Input

\<Lvalue\> = Input

LPF_KUpdate_f32_m(Fp, T, SV_Str)

##### Coefficient Recalculation Macro

|                      |                                                   |              |                 |         |          |
|---------------|----------------------------|-----------|-------|------|------|
| **Function Name**    | LPF_KUpdate_f32_m                                 | Type         | Min             | Max     | UTP Tol. |
| **Arguments Passed** | Fp – Pole cutoff frequency in hertz               | Float 32     | 0.1% 1/T        | 50% 1/T |          |
|                      | T – Sampling interval in seconds                  | Float 32     | 0.00005         | 10      |          |
|                      | SV_Str – Pointer to the state variable structure  | LPF32KSV_Str | \*See 2.3.2.1.4 |         |          |
| **Return Value**     | New value of K stored in state variable structure | Float 32     | 0.0             | 1.0     |          |

**Pseudo Code**:

\<SV_Str-\> K_Uls_f32\> = 1 – expf(-2π \* Fp \* T)

##### Output Update Macro

|                      |                                                  |              |                 |      |          |
|----------------|-----------------------------|-----------|------|------|------|
| **Function Name**    | LPF_OpUpdate_f32_m                               | Type         | Min             | Max  | UTP Tol. |
| **Arguments Passed** | Input – Input to low pass filter                 | Float 32     | FULL            | FULL |          |
|                      | SV_Str – Pointer to the state variable structure | LPF32KSV_Str | \*See 2.3.2.1.4 |      |          |
| **Return Value**     | Output of low pass filter                        | Float 32     | FULL            | FULL |          |

**Pseudo code:**

\<Lvalue\> = \<SV_Str-\>SV_Uls_f32\> =

(Input – \<SV_Str-\>SV_Uls_f32\>) \* \<SV_Str-\>K_Uls_f32\> +
\<SV_Str-\>SV_Uls_f32\>

##### **Usable ranges for LPF32KSV_Str Structure**

|              |          |      |      |          |
|--------------|----------|------|------|----------|
| LPF32KSV_Str | Type     | Min  | Max  | UTP Tol. |
| K_Uls_f32    | Float 32 | 0.0  | 1.0  |          |
| SV_Uls_f32   | Float 32 | FULL | FULL |          |

##### **Usage**

For a module that executes a LPF, in its \_Init() sub module execute the
following macros:

LPF_Init_f32_m(\<Input\>, \<Fp\>, \<T\>, \<LPF32KSV_Str\>)

In the same module’s \_Per() sub module execute the following macro:

LPF_OpUpdate_f32_m ( \<Input\>, \<LPF32KSV_Str\>)

The module may optionally call the following macro if the coefficient
value K needs to be updated on the fly to support variable cutoff
filtering.

LPF_KUpdate_f32_m(\<Fp\>, \<T\>, \<LPF32KSV_Str\>)

# 1^st^ Order High Pass Filter, 1 Pole- coefficient

## Topology 1 – HP-CF (Floating Point Implementation)

The filter topology HP-CF is as given:

![](ElectricPowerSteering_TexasInstruments_HAITEC_LC_website/docs/NxtrLib/doc/mediax/media/image5.wmf)

### Filter Equations

The filter equations are given below. Each equation shall be implemented
as a library macro.

#### Low Pass Filter

The low-pass filter aspect of the design uses the 1LP1-CF implementation
as described in section 2.3.

#### CF Calculation

The CF (correction factor) is calculated as follows:

> CF = (1 + exp(2PI \* Fp \* T)) / (2 \* sqrt(1 + ((2 \* Fp \* T)\^2)))

#### Normal Operation 

The equation for the output is as follows:

filt_Out = ( Input – LPF_Output ) \* CF

### Library Routine Design

#### Unity Gain, No Dead band Compensation, calibratable K, Single-Precision Float Input

There will be three macros defined for this implementation: state
variable and coefficient initialization, coefficient calculation, and
filter output update. The interface for these macros will be similar to
that of the 1LP1-CF low pass filter design.

##### Coefficient and State Variable Initialization Macro

|                      |                                                  |              |                 |         |          |
|---------------|----------------------------|-----------|-------|------|------|
| **Function Name**    | HPF_Init_f32_m                                   | Type         | Min             | Max     | UTP Tol. |
| **Arguments Passed** | Input – Initial input to filter                  | Float 32     | FULL            | FULL    |          |
|                      | Fp – Pole cutoff frequency in hertz              | Float 32     | 0.1% 1/T        | 50% 1/T |          |
|                      | T – Sampling interval in seconds                 | Float 32     | 0.00005         | 10      |          |
|                      | SV_Ptr – Pointer to the state variable structure | HPF32KSV_Str | \*See 3.1.2.1.4 |         |          |
| **Return Value**     | Assignment returns initial output                |              |                 |         |          |

**Pseudo Code**:

LPF_Init_f32_m(Input, Fp, T, &(SV_Ptr-\>LPF_Str))

HPF_KUpdate_f32_m(Fp, T, SV_Ptr)

##### Coefficient Recalculation Macro

|                      |                                                  |              |                 |         |          |
|---------------|----------------------------|-----------|-------|------|------|
| **Function Name**    | HPF_KUpdate_f32_m                                | Type         | Min             | Max     | UTP Tol. |
| **Arguments Passed** | Fp – Pole cutoff frequency in hertz              | Float 32     | 0.1% 1/T        | 50% 1/T |          |
|                      | T – Sampling interval in seconds                 | Float 32     | 0.00005         | 10      |          |
|                      | SV_Ptr – Pointer to the state variable structure | HPF32KSV_Str | \*See 3.1.2.1.4 |         |          |
| **Return Value**     | Assignment returns correction factor             |              |                 |         |          |

**Pseudo Code**:

SV_Ptr-\>CF = (1 + exp(2PI \* Fp \* T)) / (2 \* sqrt(1 + ((2 \* Fp \*
T)\^2)))

LPF_KUpdate_f32_m(Fp_f32, T_f32, &(SV_Ptr-\>LPF_Str))

##### Output Update Macro

|                      |                                                  |              |                 |      |          |
|----------------|-----------------------------|-----------|------|------|------|
| **Function Name**    | HPF_OpUpdate_f32_m                               | Type         | Min             | Max  | UTP Tol. |
| **Arguments Passed** | Input – Input to low pass filter                 | Float 32     | FULL            | FULL |          |
|                      | SV_Ptr – Pointer to the state variable structure | HPF32KSV_Str | \*See 3.1.2.1.4 |      |          |
| **Return Value**     | Assignment returns filter output                 |              |                 |      |          |

**Pseudo code:**

(Input - LPF_OpUpdate_f32_m(input_f32, &(SV_Ptr-\>LPF_Str))) \*
SV_Ptr-\>CF_Uls_f32

##### **Usable ranges for H**PF32KSV_Str Structure

|              |              |                 |      |          |
|--------------|--------------|-----------------|------|----------|
| HPF32KSV_Str | Type         | Min             | Max  | UTP Tol. |
| LPF_Str      | LPF32KSV_Str | \*See 2.3.2.1.4 |      |          |
| CF_Uls_f32   | Float 32     | 0.0             | FULL |          |

##### **Usage**

For a module that executes a HPF, in its \_Init() sub module execute the
following macros:

> HPF_Init_f32_m(\<Input\>, \<Fp\>, \<T\>, \<HPF32KSV_Str\>)

In the same module’s \_Per() sub module execute the following macro:

> HPF_OpUpdate_f32_m ( \<Input\>, \<HPF32KSV_Str\>)

The module may optionally call the following macro if the coefficient
value K needs to be updated on the fly to support variable cutoff
filtering:

> HPF_KUpdate_f32_m(\<Fp\>, \<T\>, \<HPF32KSV_Str\>)

# Revision Control Log

|        |         |                                                                                           |           |              |
|-----|------|-----------------------------------------|---------|------------|
| **\#** | **Rev** | **Change**                                                                                | **Date**  | **Author**   |
| 1      | 1.0     | Added floating point low-pass filter                                                      | 09FEB12   | Jared Julien |
| 2      | 2.0     | Added floating point high-pass filter, fixed issues in FP LPF                             | 26-Apr-12 | Owen Tosh    |
| 3      | 3.0     | Correct output types for some filters (32 bits output instead of 16bits) – no code change | 25-Jan-13 | D. Djena     |
| 4      | 4.0     | Added new parameter to functions NF_FullUpdate_f32 and NF_SvUpdate_f32                    | 05-Dec-13 | VT           |

{% endraw %}