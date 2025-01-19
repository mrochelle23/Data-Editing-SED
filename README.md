# Comic Characters Dataset Editor

## Overview
This project involves creating a `sed` script to perform specific transformations on a dataset containing information about Marvel comic characters. The dataset is obtained from FiveThirtyEight's data repository under the CC4.0 license. 

The script (`script.sed`) performs the following tasks:
1. **Clean Character Names**: Remove any parenthetical information in the character names, leaving only the main name. For example:
   - `Captain America (Steven Rogers)` ➡ `Captain America`
   - Note: Parentheticals may contain periods (`.`) and varying formats, which should also be handled.
   
2. **Reformat Appearance Date Columns**: Merge the last two columns (`1st appearance month-year` and `1st appearance year`) into a single column in the format:
   - `Aug-62, 1962` ➡ `1962 (Aug)`
   
3. **Remove Deceased Characters**: Remove all rows that represent deceased characters, indicated by the phrase `Deceased Characters` in the dataset.

## Dataset Description
The dataset contains the following columns:
1. **wikia page id**  
2. **character name**  
3. **urlslug**  
4. **identity status**  
5. **character alignment**  
6. **eye color**  
7. **hair color**  
8. **sex of character**  
9. **GSM (gender and sexual minority)**  
10. **alive or deceased**  
11. **number of appearances**  
12. **1st appearance month and year (Mon-YY)**  
13. **1st appearance year (YYYY)**  

An example dataset (`marvel-small.csv`) has been included in the repository for testing.

## Example Input and Output

### Input (`marvel-small.csv`)
```
1678, Spider-Man (Peter Parker),\/Spider-Man_(Peter_Parker),Secret Identity,Good Characters,Hazel Eyes,Brown Hair, Male Characters,, Living,Aug-62,1962
7139, Captain America (Steven Rogers),\/Captain_America_(Steven_Rogers),Public Identity,Good Characters,Blue Eyes,White Hair,Male Characters,,Living,Mar-41,1941
64786, Wolverine (James "'''Logan\"" Howlett),\/Wolverine_(James_%22Logan%22_Howlett),Public Identity,Neutral Characters,Blue Eyes,Black Hair,Male Characters,,Living,Oct-74,1974
1453, Otto Octavius (Earth-616),\/Otto_Octavius_(Earth-616),Secret Identity,Neutral Characters,Hazel Eyes,Brown Hair,Male Characters,,Deceased Characters,May-63,1963
```

### Output (after running `script.sed`)
```
1678, Spider-Man,\/Spider-Man_(Peter_Parker),Secret Identity,Good Characters,Hazel Eyes,Brown Hair, Male Characters,,Living,1962 (Aug)
7139, Captain America,\/Captain_America_(Steven_Rogers),Public Identity,Good Characters,Blue Eyes,White Hair,Male Characters,,Living,1941 (Mar)
64786, Wolverine,\/Wolverine_(James_%22Logan%22_Howlett),Public Identity,Neutral Characters,Blue Eyes,Black Hair,Male Characters,,Living,1974 (Oct)
```

### Key Changes
1. Parentheticals in character names are removed.
2. `1st appearance` columns are merged into a new format.
3. Deceased characters are removed entirely.

## File Structure
```
.
├── README.md                # Project documentation (this file)
├── script.sed               # The sed script
├── marvel-small.csv         # Example dataset for testing
```

## Requirements
- Your `sed` script must:
  1. Be saved in a file named `script.sed`.
  2. Run correctly with the command:  
     ```bash
     sed -E -i -f script.sed marvel-small.csv
     ```
  3. Modify the dataset in place without errors.

## Instructions
1. Clone the repository and navigate to the project directory.
2. Make a backup of `marvel-small.csv` for testing:
   ```bash
   cp marvel-small.csv marvel-small-backup.csv
   ```
3. Run the script:
   ```bash
   sed -E -i -f script.sed marvel-small.csv
   ```
4. Verify the changes by inspecting the modified file:
   ```bash
   cat marvel-small.csv
   ```

## Testing
To test the correctness of your `sed` script:
- Compare the modified `marvel-small.csv` against the expected output provided above.
- Ensure no errors are thrown during execution.

## License
This project uses data from FiveThirtyEight under the [CC4.0 license](https://creativecommons.org/licenses/by/4.0/). Ensure proper attribution when using the dataset.

---

Let me know if you'd like additional edits or enhancements!
