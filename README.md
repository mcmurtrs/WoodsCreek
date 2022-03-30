# Directory index
- Final data sheet before data cleaning adendum was conducted: `WC Final 2020 - 08_05_20.xlsx`
- Cleaned up file after the below steps were completed: `WC Final 2020 - 08_05_20_CLEANED.xlsx`
- All trees that were removed were documented in: `edited_and_deleted_trees.xlsx`
- File used for creating FVS input files: `WC Final 2020 - 08_05_20_CLEANED_FVS_INPUT.xlsx`
- Basal area calculations for Forest Vegetation Simulator (FVS) and Western Root Disease Model (WRDM) comparison can be found in: 
- All FVS/WRDM input files can be found in this directory: ` mcmurtrs/WoodsCreek/FVS_Input_Files`
- All FVS/WRDM output and log files are in:

## Step 1: General cleanup
- ***Note that all DBH measurements are in cm unless otherwise stated.***
- Also note that all changes are being made to the "WC Final 2020 - 08_05_20.xlsx" file. More specifically all changes are being made on the "original from everett" sheet.
- Replaced all "x" with a blank space (made 1105 replacements). 
- Replaced all "?" with a blank space (made 5 replacements).
- Changed 12D Tree #16 DBH from 2009 from 52.5 to 72.5 based upon 2000 and 2020 DBH measurements (assumed data entry error from 2009).
- Changed PLOT of 22B(ALT) to 22B (There were 25 replacements made).
- Changed 11c Tree #20 2009 measurement from 15.1 to 75.1 based upon 2000 and 2020 measurement (assumed data entry error).
- Changed 11c Tree #30 2009 measurement from 36.4 to 56.4.1 based upon 2000 and 2020 measurement (assumed data entry error).
- Changed 15B	Tree #5 and 32A	Tree #32,  from "GC" to "CH" for Chinquapin
- Changed 25D Tree #32 & 25D Tree #34 from Birch to PB to align with the species codes used within the PN variant of FVS.
- Added DBH measurements and tree health condition codes (THCC) from 1990 "T2-B2" spreadsheet to "original from everett" sheet.
- Combined measurements from 33E Tree #23 and 33E Tree#23* based upon context clues from notes and previous measurements matching closely to current measurements.
- Removed tree 3	3	D	23 from dataset because no species code was ever assigned.

## Step 2: Check to Ensure that there are no measurements included within the data that have < 15.24cm DBH
- ***Note that all DBH measurements are in cm unless otherwise stated.***
- In excel sort by DBH starting with 1985 through 2020 (deleted 77 trees).
- In excel sort by DBH from 1985-2020 and delete any individual measurements from those years that were less < 15.24cm (edited 44 trees).
- Excel spreadsheet titled "edited_and_deleted_trees.xlsx" contains the records of all trees that were edited or deleted.

## Step 3: Removed trees with > 25 cm DBH if 2020 DBH was the only year where DBH was recorded
- In excel sort by 2020 DBH (Removed 42 trees from the raw dataset).
-  Excel spreadsheet titled "edited_and_deleted_trees.xlsx" contains the records of all trees that were edited or deleted.

## Step 4: - Added condition codes for 2020 andd double checked condition codes from other years.
- Condition codes of 3 and 4 were deleted in repeated subsequent years. If DBH was recorded for the year where it was found to be 3 or 4 this value was left. The reasoning for deleting the repeats was to not include dead/snags/stumps/rotted wood etc. for more than one year. This would help ensure that the basal area would not be recorded for dead trees and that each year an accurate record of newly dead trees could be recorded. There is a version of the spreadsheet that repeats the 3 and 4 codes through 2020. This spreadsheet is "WC Final 2020 - 08_05_20_CLEANED (code_3_4_carried over).xlsx"  
- Made best judgement call on whether to include tree health condition code in 2020 for missing trees based upon notes from previous years. (If trees were missing and no notes were given for condition from previous years then condition code was left blank).
- 13B Tree #19 repeated the health condition code of 4 for 2009 and 3 for 2020 since it was an eventual count for Laminated Root Root (code 3).
- After consideration, there will be repeats of 3 and 4 codes but only on ORIG, 1985, and 1990. This is because for most analysis we will be using 1990 as the starting year since this is after the thinning occurred. However we might be using 1985 as a starting year therefore the repeats will be useful for the 1985 and or 1990 analysis.

## Step 5: Formating the Spreadsheet for FVS
- Using the spreadsheet titled "WC Final 2020 - 08_05_20_CLEANED" which has been edited from the raw data file "WC Final 2020 - 08_05_20" by following the steps from above we will now use it to format the datasheet for use within FVS.
- In excel the 90 DIA column was convereted from "cm" to "inch" using the CONVERT function.
- All tree health condition codes were converted as follows to fit the FVS model history parameters field:

Current "History" coding conversion for 1990 is:

| Our code | FVS conversion |
| --- | --- |
| 1 | 1 |
| 2 | 5 |
| 3 | 6 |
| 4 | 6 |


- Code 1 = 1 (Healthy = Live Tree)
- Code 2 = 5 (Symptomatic = Live tree)
- Code 3 = 6 (Recently dead)
- Code 4 = 6 (Recently dead)

## Addtional Notes 
- 24B Tree #2 DBH from 1990 is probably wrong.
- 14F Tree #40 missing DBH from 1990 
- Trees 12A #23, 12A #26, 12E #26, 12E #29 were missing species codes and were removed from the data sheet. 
- Additional previous notes from Everett concerning potential errors within the data can be found in the "notes" spreadsheet of the "WC Final 2020 - 08_05_20.xlsx" spreadsheet
