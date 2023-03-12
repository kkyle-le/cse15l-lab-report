# `curl` | Lab Report 5

## `curl -o` Copy Into File w/ Custom Name

Using `curl` with the `-o` will allow you to redirect the output into a file with your choice of name without initially making the file to be imported to, similar to using `>>`. This is useful when original filenames do not have names that can be easily organize (random letters and numbers) or for making your own personal file system that is different from what the creator of the URL had in place.

URL used: [<https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023>](https://ftp.nhc.noaa.gov/atcf/pub/al092022.public.023)

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

## `curl -r` Copy Specific Range

### Example 1
### Example 2


## `curl -`

URL used: http://ftp.1000genomes.ebi.ac.uk/vol1/ftp/release/20130502/ALL.chr22.phase3_shapeit2_mvncall_integrated_v5b.20130502.genotypes.vcf.gz
### Example 1
### Example 2


# Source Used:
## [<https://curl.se/docs/manpage.html>](https://curl.se/docs/manpage.html)
## [<https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/>](https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/)
