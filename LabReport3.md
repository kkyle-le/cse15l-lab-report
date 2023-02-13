# `-grep` | Lab Report 3

## `grep -l`
When knowing the contents of particular files being searched for is not as important as knowing its directory, using the `-l` option can be extremely helpful in condensing output information and removing clutter in the output terminal. This comes especially in handy as it skips the need to use the find command in tandem with grep and therefore makes searching for a particular directory to a file more efficient.

### Example 1 (Condensed Output)
```sh 
kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -l "Bahamas" written_2/travel_guides/berlitz2/*.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt
written_2/travel_guides/berlitz2/Bahamas-Intro.txt
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
```

### Example 2 (Condensed Output)
```sh
kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -l "Athens" written_2/travel_guides/berlitz1/*.txt
written_2/travel_guides/berlitz1/HistoryEdinburgh.txt
written_2/travel_guides/berlitz1/HistoryGreek.txt
written_2/travel_guides/berlitz1/HistoryIstanbul.txt
written_2/travel_guides/berlitz1/HistoryItaly.txt
written_2/travel_guides/berlitz1/IntroGreek.txt
written_2/travel_guides/berlitz1/WhatToGreek.txt
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt
written_2/travel_guides/berlitz1/WhereToGreek.txt
written_2/travel_guides/berlitz1/WhereToIsrael.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
```

It is important to reiterate that the grep commands looks for the existence of the requested "string" in the contents, and does not search the file names for the string as seen in none of the output directories contains the string "Athens" in their file names.

## `grep -r` 
When trying to search for a string and the directory range is unknown, using `-r` is powerful as it utilizes recusrive search similar to the find command when trying to find a file. The following examples uses the `-l` command above in order to make the outputs more readable (the same is applied for all examples beyond).

### Example 1 (Fast Search w/ Known Directory)
```sh
$ grep -r -l "England" written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz1/HistoryDublin.txt
written_2/travel_guides/berlitz1/HistoryEdinburgh.txt
written_2/travel_guides/berlitz1/HistoryFrance.txt
written_2/travel_guides/berlitz1/HistoryHawaii.txt
written_2/travel_guides/berlitz1/HistoryIndia.txt
written_2/travel_guides/berlitz1/HistoryJamaica.txt
written_2/travel_guides/berlitz1/HistoryLakeDistrict.txt
written_2/travel_guides/berlitz1/HistoryMalaysia.txt
written_2/travel_guides/berlitz1/HistoryMallorca.txt
written_2/travel_guides/berlitz1/IntroEdinburgh.txt
written_2/travel_guides/berlitz1/IntroJamaica.txt
written_2/travel_guides/berlitz1/IntroLakeDistrict.txt
written_2/travel_guides/berlitz1/WhatToJamaica.txt
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToIsrael.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
written_2/travel_guides/berlitz1/WhereToLakeDistrict.txt
written_2/travel_guides/berlitz1/WhereToLosAngeles.txt
written_2/travel_guides/berlitz1/WhereToMallorca.txt
```

### Example 2 (Fast Search w/o Known Directory)
As seen in this example, it is not known whether the string will be in either berlitz1 or berlitz2 so using -r will traverse both instead of having to run separate commands for both directories.
```sh
kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r -l "Bahamas" written_2/
written_2/travel_guides/berlitz1/WhatToFWI.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt
written_2/travel_guides/berlitz2/Bahamas-Intro.txt
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
```

## `grep -w`

The standard grep function will look for every occurance of the search string in every form. So it will return files that contains "son" but also files that contains "person" but no instance of "son". To take into account of this, the `-w` option which functions as "exact match". The following examples demonstrate the different output when the exact same commands are ran with the difference of `-w` being in the second command.

### Example 1 (No exact match)
 ```sh
 kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r -l "baha" written_2/
written_2/travel_guides/berlitz2/Bali-WhereToGo.txt
written_2/travel_guides/berlitz2/Nepal-WhereToGo.txt

kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r -l -w "baha" written_2/
```

### Example 2 (Exact match found)
*note, first command's output was extremely long, was cut short to maintain readability
```
$ grep -r -l "sons" written_2/
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/non-fiction/OUP/Abernathy/ch6.txt
written_2/non-fiction/OUP/Abernathy/ch7.txt
written_2/non-fiction/OUP/Abernathy/ch8.txt
written_2/non-fiction/OUP/Abernathy/ch9.txt
written_2/non-fiction/OUP/Berk/ch1.txt
written_2/non-fiction/OUP/Berk/ch2.txt
written_2/non-fiction/OUP/Berk/CH4.txt
written_2/non-fiction/OUP/Berk/ch7.txt
written_2/non-fiction/OUP/Castro/chC.txt
written_2/non-fiction/OUP/Castro/chL.txt
written_2/non-fiction/OUP/Castro/chM.txt
written_2/non-fiction/OUP/Castro/chP.txt
written_2/non-fiction/OUP/Castro/chR.txt
written_2/non-fiction/OUP/Castro/chZ.txt
written_2/non-fiction/OUP/Fletcher/ch1.txt
written_2/non-fiction/OUP/Fletcher/ch10.txt
written_2/non-fiction/OUP/Fletcher/ch2.txt
written_2/non-fiction/OUP/Fletcher/ch5.txt
written_2/non-fiction/OUP/Fletcher/ch6.txt
written_2/non-fiction/OUP/Fletcher/ch9.txt
written_2/non-fiction/OUP/Kauffman/ch1.txt
written_2/non-fiction/OUP/Kauffman/ch10.txt
written_2/non-fiction/OUP/Kauffman/ch5.txt
written_2/non-fiction/OUP/Kauffman/ch6.txt
written_2/non-fiction/OUP/Kauffman/ch8.txt
written_2/non-fiction/OUP/Rybczynski/ch1.txt
written_2/non-fiction/OUP/Rybczynski/ch3.txt
written_2/travel_guides/berlitz1/HandRHawaii.txt
written_2/travel_guides/berlitz1/HandRJamaica.txt
written_2/travel_guides/berlitz1/HandRLosAngeles.txt
written_2/travel_guides/berlitz1/HistoryEdinburgh.txt
written_2/travel_guides/berlitz1/HistoryFrance.txt
written_2/travel_guides/berlitz1/HistoryIstanbul.txt
written_2/travel_guides/berlitz1/HistoryItaly.txt
written_2/travel_guides/berlitz1/HistoryJapan.txt
written_2/travel_guides/berlitz1/HistoryLasVegas.txt
written_2/travel_guides/berlitz1/HistoryMallorca.txt
written_2/travel_guides/berlitz1/IntroEdinburgh.txt
written_2/travel_guides/berlitz1/IntroGreek.txt
written_2/travel_guides/berlitz1/IntroJapan.txt
written_2/travel_guides/berlitz1/IntroJerusalem.txt
written_2/travel_guides/berlitz1/IntroLakeDistrict.txt
written_2/travel_guides/berlitz1/WhatToDublin.txt
written_2/travel_guides/berlitz1/WhatToFWI.txt
[. . .]

kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r -l -w "sons" written_2/
written_2/non-fiction/OUP/Berk/ch1.txt
written_2/non-fiction/OUP/Berk/ch7.txt
written_2/non-fiction/OUP/Castro/chL.txt
written_2/non-fiction/OUP/Castro/chM.txt
written_2/non-fiction/OUP/Castro/chZ.txt
written_2/travel_guides/berlitz1/HistoryEdinburgh.txt
written_2/travel_guides/berlitz1/HistoryFrance.txt
written_2/travel_guides/berlitz1/HistoryIstanbul.txt
written_2/travel_guides/berlitz1/HistoryJapan.txt
written_2/travel_guides/berlitz1/HistoryMallorca.txt
written_2/travel_guides/berlitz1/IntroEdinburgh.txt
written_2/travel_guides/berlitz1/IntroGreek.txt
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToIbiza.txt
written_2/travel_guides/berlitz1/WhereToIndia.txt
written_2/travel_guides/berlitz1/WhereToMallorca.txt
written_2/travel_guides/berlitz2/Amsterdam-History.txt
written_2/travel_guides/berlitz2/Bali-WhatToDo.txt
written_2/travel_guides/berlitz2/Boston-WhereToGo.txt
written_2/travel_guides/berlitz2/Crete-History.txt
written_2/travel_guides/berlitz2/Paris-WhereToGo.txt
written_2/travel_guides/berlitz2/Poland-History.txt
```

## `grep -i`
This grep option is similar to `-w` with the only difference being that `-i` is not case sensitive and will output all files with the exact match string excluding casing (i.e "the" and "The" in their respective files will both be returned). This allows for more flexibility and throuough range when looking for a specific word.

### Example 1 (Flexibility)
This example demonstrates how
```sh
kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r -l "APPLE" written_2/

kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r -l -i "APPLE" written_2/
written_2/non-fiction/OUP/Abernathy/ch6.txt
written_2/non-fiction/OUP/Berk/ch2.txt
written_2/non-fiction/OUP/Berk/CH4.txt
written_2/non-fiction/OUP/Castro/chO.txt
written_2/non-fiction/OUP/Kauffman/ch1.txt
written_2/non-fiction/OUP/Kauffman/ch3.txt
written_2/non-fiction/OUP/Kauffman/ch4.txt
written_2/non-fiction/OUP/Kauffman/ch9.txt
written_2/travel_guides/berlitz1/HandRHawaii.txt
written_2/travel_guides/berlitz1/HandRJamaica.txt
written_2/travel_guides/berlitz1/HistoryHawaii.txt
written_2/travel_guides/berlitz1/WhatToIbiza.txt
written_2/travel_guides/berlitz1/WhatToJamaica.txt
written_2/travel_guides/berlitz1/WhatToJapan.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToFWI.txt
written_2/travel_guides/berlitz1/WhereToHawaii.txt
written_2/travel_guides/berlitz1/WhereToIstanbul.txt
written_2/travel_guides/berlitz1/WhereToMadeira.txt
written_2/travel_guides/berlitz1/WhereToMalaysia.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Barcelona-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
written_2/travel_guides/berlitz2/China-History.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt
written_2/travel_guides/berlitz2/Crete-WhereToGo.txt
written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt
```

### Example 2 (Scope Compared to `-i`)
This examples demonstrates the different search processes of `-w` and `-i` and how they handle cases.

```sh
kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r -l -w "Olives" written_2/
written_2/travel_guides/berlitz1/IntroGreek.txt
written_2/travel_guides/berlitz1/IntroIsrael.txt
written_2/travel_guides/berlitz1/WhatToGreek.txt
written_2/travel_guides/berlitz1/WhereToIsrael.txt
written_2/travel_guides/berlitz1/WhereToJerusalem.txt
written_2/travel_guides/berlitz2/Crete-WhatToDo.txt

kkylele@DESKTOP-OE6MSVS MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r -l -i "Olives" written_2/
written_2/travel_guides/berlitz1/HistoryFrance.txt
written_2/travel_guides/berlitz1/IntroGreek.txt
written_2/travel_guides/berlitz1/IntroIsrael.txt
written_2/travel_guides/berlitz1/WhatToGreek.txt
written_2/travel_guides/berlitz1/WhatToIbiza.txt
written_2/travel_guides/berlitz1/WhatToIstanbul.txt
written_2/travel_guides/berlitz1/WhereToGreek.txt
written_2/travel_guides/berlitz1/WhereToIsrael.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
written_2/travel_guides/berlitz1/WhereToJerusalem.txt
written_2/travel_guides/berlitz2/Athens-WhatToDo.txt
written_2/travel_guides/berlitz2/Costa-WhatToDo.txt
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt
written_2/travel_guides/berlitz2/Crete-WhatToDo.txt
written_2/travel_guides/berlitz2/Crete-WhereToGo.txt
written_2/travel_guides/berlitz2/Portugal-History.txt
```

# Source Used:
## <https://www.geeksforgeeks.org/grep-command-in-unixlinux/>
