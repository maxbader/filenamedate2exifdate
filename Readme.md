# file name to exif date
This python script is able to parse file names of media date such as _jpg_ or _mp4_ files.
It detects encoded time stamps and uses this time stamps to set exif information.
## Usage
```
usage: filenamedate2exifdate.py [-h] --input i [i ...] [--prefix p] [--format f] [--exifcmd EXIFCMD] [--date_tags DATE_TAGS [DATE_TAGS ...]] [--echo] [--echo_only]

options:
  -h, --help            show this help message and exit
  --input i [i ...]     input file --> required
  --prefix p            file prefix
  --format f            date format YYYY-MM-DD-hh-mm-ss-ccc
  --exifcmd EXIFCMD     exiftool command
  --date_tags DATE_TAGS [DATE_TAGS ...]
                        exif tags to set such as alldates, FileModifyDate, CreateDate, ...
  --echo                prints the exiftool command
  --echo_only           used to prevent the command execution
```
### examples
#### single images
Signal images
```
python ./filenamedate2exifdate.py --echo_only --prefix signal- --format YYYY-MM-DD-hh-mm-ss-ccc --date_tags alldates FileModifyDate --input signal-2021-02-20-08-59-20-104.jpg 
```
WhatsApp video
```
python ./filenamedate2exifdate.py --echo_only --prefix VID- --format YYYYMMDD-WAcccc --date_tags alldates FileModifyDate --input VID-20190609-WA0019.mp4 
```
WhatsApp images
```
python ./filenamedate2exifdate.py --echo_only --prefix IMG- --format YYYYMMDD-WAcccc --date_tags alldates FileModifyDate --input IMG-20190721-WA0002.jpg 
```
#### patch processing
Signal images
```
find . -name 's*.jpg' -exec python ./filenamedate2exifdate.py --echo_only --prefix signal- --format YYYY-MM-DD-hh-mm-ss-ccc --date_tags alldates FileModifyDate --input {} \;
```


