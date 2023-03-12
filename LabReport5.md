# `curl` | Lab Report 5

## `curl -o` Copy Into File w/ Custom Name

Using `curl` with the `-o` will allow you to redirect the output into a file with your choice of name without initially making the file to be imported to, similar to using `>>`. This is useful when original filenames do not have names that can be easily organize (random letters and numbers) or for making your own personal file system that is different from what the creator of the URL had in place.

URL used: 

[<https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023>](https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023)

### Example 1 (Meaningful Name)
The original name of this file was "al092022.public.023" however to the public eye, it might not make sense, using the `-o` command to copy its content into a file with a recognizable name can be useful for organization.

```ssh
[cs15lwi23agv@ieng6-201]:~:526$ curl -o HurricaneIanAdvisory.txt https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  8006  100  8006    0     0   2688      0  0:00:02  0:00:02 --:--:--  2688
[cs15lwi23agv@ieng6-201]:~:527$ ls
HurricaneIanAdvisory.txt  lab7  list-examples-grader  perl5
```
```
[cs15lwi23agv@ieng6-201]:~:528$ cat HurricaneIanAdvisory.txt 
ZCZC MIATCPAT4 ALL
TTAA00 KNHC DDHHMM

BULLETIN
Hurricane Ian Special Advisory Number  23
NWS National Hurricane Center Miami FL       AL092022
700 AM EDT Wed Sep 28 2022

...RAPIDLY INTENSIFYING IAN FORECAST TO CAUSE CATASTROPHIC
STORM SURGE, WINDS, AND FLOODING IN THE FLORIDA PENINSULA...
[ . . . ]
```
(Output has been chopped at `[ . . . ]` to reduce length of this blog post, full advisory from link above was printed when `cat` command was called)

### Example 2 (Own File System)
The name original file name, "al092022.public.023", can be broken down to:

`al = Atlantic Basin, 09 = 9th Hurricane (Ian), 2022 = Current Year, public.023 = Public Advisory #23 for This Storm System`

However to another person, they may want to use a different filing system, so using `-o` to rename a file to abide by their filing rules can come in handy such that, instead of being organized by basin first (Atlantic, Eastern Pacific, Western Pacific), it is organized by year first. (2022_ATL-Ian)

```
[cs15lwi23agv@ieng6-201]:~:529$ curl -o 2022_ATL-Ian.txt https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  8006  100  8006    0     0  13512      0 --:--:-- --:--:-- --:--:-- 13523
[cs15lwi23agv@ieng6-201]:~:530$ ls
2022_ATL-Ian.txt  HurricaneIanAdvisory.txt  lab7  list-examples-grader  perl5
[cs15lwi23agv@ieng6-201]:~:531$ cat 2022_ATL-Ian.txt 
ZCZC MIATCPAT4 ALL
TTAA00 KNHC DDHHMM

BULLETIN
Hurricane Ian Special Advisory Number  23
NWS National Hurricane Center Miami FL       AL092022
700 AM EDT Wed Sep 28 2022

...RAPIDLY INTENSIFYING IAN FORECAST TO CAUSE CATASTROPHIC
STORM SURGE, WINDS, AND FLOODING IN THE FLORIDA PENINSULA...
```
(Output has been chopped at `[ . . . ]` to reduce length of this blog post, full advisory from link above was printed when `cat` command was called)


## `curl -O` Copy Into File Using Existing Name
Similar to `-o`, the option `-O` will copy the contents of a URL and put it into a file for you. The one difference is that `-O` will use the already existig filename of the url's remote server file. This can be useful when you do not care much about a file's name in your system, or when you want to use the file naming system the file author is using, thus you do not need to create an initial file to redirect the `curl` output into.

URL Used: 

[<https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.009>](https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.009)


[<https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.010>](https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.010)


[<https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.011>](https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.011)

### Example 1 (Single File Download)
I only need to download one unique file and therefore I am not too worried about the naming scheme as it will be easily identifiable in my working directory.
```ssh 
$ curl -O https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.009
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 13725  100 13725    0     0  25604      0 --:--:-- --:--:-- --:--:-- 26242

kkylele@DESKTOP-OE6MSVS MINGW64 ~/testing
$ ls
al092022.wndprb.009  hello.txt  robloxworkingcodes.txt

kkylele@DESKTOP-OE6MSVS MINGW64 ~/testing
$ cat al092022.wndprb.009 
ZCZC MIAPWSAT4 ALL
TTAA00 KNHC DDHHMM

TROPICAL STORM IAN WIND SPEED PROBABILITIES NUMBER   9
NWS NATIONAL HURRICANE CENTER MIAMI FL       AL092022
0900 UTC SUN SEP 25 2022

AT 0900Z THE CENTER OF TROPICAL STORM IAN WAS LOCATED NEAR LATITUDE
14.9 NORTH...LONGITUDE 78.8 WEST WITH MAXIMUM SUSTAINED WINDS NEAR
45 KTS...50 MPH...85 KM/H.
[ . . . ]
```

### Example 2 (Adopting File Naming System)
The file organizing maning scheme already in place is effective and I do not see a reason to change it, so using `-O` on multiple files will allow me to have the files already organized.

```
kkylele@DESKTOP-OE6MSVS MINGW64 ~/testing
$ curl -O -O -O https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.009 https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.010 https://ftp.nhc.noaa.gov/atcf/wndprb/al092022.wndprb.011
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 13725  100 13725    0     0  19384      0 --:--:-- --:--:-- --:--:-- 19748
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 14709  100 14709    0     0   132k      0 --:--:-- --:--:-- --:--:--  133k
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 14496  100 14496    0     0   155k      0 --:--:-- --:--:-- --:--:--  155k

kkylele@DESKTOP-OE6MSVS MINGW64 ~/testing
$ ls
al092022.wndprb.009  al092022.wndprb.010  al092022.wndprb.011
```

## `curl -r <byte-range>` Copy Specific Range
Using this command is extremely useful when downloading large files in which you do not need all the information contained in the file, thus cutting downloading times down.

URL Used: 

[<https://ftp.nhc.noaa.gov/atcf/dis/al092022.discus.023>](https://ftp.nhc.noaa.gov/atcf/dis/al092022.discus.023)


[<https://ftp.nhc.noaa.gov/atcf/dis/al062022.discus.029>](https://ftp.nhc.noaa.gov/atcf/dis/al062022.discus.029)


### Example 1 Time Download Comparison
As seen in the code block below, the time to download the ranged file is much faster compared to downloading the entire file, for obvious reason! Less data to download. This can scale up to massive amount of time saved when downloading extremely large files. Between these two curl commands, we can see a dramatic decrease in time when looking a the last column, Current speed: 886 w/ `-r` vs 4603 w/o `-r`. Both of these files are small so the time difference in reality is minimal but when scaled up to larger files such as the human genenome, we can see this difference. (The argument `-600` refers to the last 600 bytes)
```
kkylele@DESKTOP-OE6MSVS MINGW64 ~/testing
$ curl -O -r -600 https://ftp.nhc.noaa.gov/atcf/dis/al062022.discus.029
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   600  100   600    0     0    869      0 --:--:-- --:--:-- --:--:--   886

kkylele@DESKTOP-OE6MSVS MINGW64 ~/testing
$ curl -O https://ftp.nhc.noaa.gov/atcf/dis/al062022.discus.029
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2730  100  2730    0     0   4507      0 --:--:-- --:--:-- --:--:--  4603
```

### Example 2 Specific Information Retrieval
In these discussion posts for tropical systems, there is a table that has predicted storm strength going out into multiple days. This table is usually the last the last 600 bytes in each file. Using `-r` in this case can give us direct access to this table without copying over the information above the table. (The argument `-600` refers to the last 600 bytes)
```
kkylele@DESKTOP-OE6MSVS MINGW64 ~/testing
$ curl -r -600 https://ftp.nhc.noaa.gov/atcf/dis/al062022.discus.029
INIT  10/0300Z 38.1N  55.9W   90 KT 105 MPH
 12H  10/1200Z 41.2N  53.2W   85 KT 100 MPH
 24H  11/0000Z 43.1N  51.7W   70 KT  80 MPH...POST-TROP/EXTRATROP
 36H  11/1200Z 43.8N  50.9W   55 KT  65 MPH...POST-TROP/EXTRATROP
 48H  12/0000Z 44.2N  50.0W   45 KT  50 MPH...POST-TROP/EXTRATROP
 60H  12/1200Z 44.5N  48.9W   40 KT  45 MPH...POST-TROP/EXTRATROP
 72H  13/0000Z 44.7N  46.7W   35 KT  40 MPH...POST-TROP/EXTRATROP
 96H  14/0000Z 45.0N  42.0W   35 KT  40 MPH...POST-TROP/EXTRATROP
120H  15/0000Z 46.0N  38.0W   35 KT  40 MPH...POST-TROP/EXTRATROP

$$
Forecaster Bucci/Cangialosi

NNNN
```

```
$ curl -r -600 https://ftp.nhc.noaa.gov/atcf/dis/al092022.discus.023
na. Widespread, 
prolonged major and record river flooding expected across central
Florida.


FORECAST POSITIONS AND MAX WINDS

INIT  28/1100Z 25.9N  82.8W  135 KT 155 MPH
 12H  28/1800Z 26.7N  82.4W  135 KT 155 MPH
 24H  29/0600Z 27.7N  81.7W   80 KT  90 MPH...INLAND
 36H  29/1800Z 28.7N  81.1W   50 KT  60 MPH...INLAND
 48H  30/0600Z 29.8N  80.7W   45 KT  50 MPH...OVER WATER
 60H  30/1800Z 31.6N  80.8W   45 KT  50 MPH
 72H  01/0600Z 33.6N  81.4W   30 KT  35 MPH...INLAND
 96H  02/0600Z 36.1N  82.1W   25 KT  30 MPH...POST-TROP/INLAND
120H  03/0600Z...DISSIPATED

$$
Forecaster Blake

NNNN
```

## `curl --max-time`
Copying over extremely large can take an obscene amount of time to finish.  
URL used: http://ftp.1000genomes.ebi.ac.uk/vol1/ftp/release/20130502/ALL.chr22.phase3_shapeit2_mvncall_integrated_v5b.20130502.genotypes.vcf.gz
### Example 1 Timeout
### Example 2 Partial File Download  


# Source Used:
## [<https://curl.se/docs/manpage.html>](https://curl.se/docs/manpage.html)
## [<https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/>](https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/)
