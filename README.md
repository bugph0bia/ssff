ssff
====

![Software Version](http://img.shields.io/badge/Version-v0.4.0-green.svg?style=flat)
![Python Version](http://img.shields.io/badge/Python-3.10-blue.svg?style=flat)
[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)

[Japanese page](./README.ja.md)  

## Overview
Screenshot and form feed. For Windows OS only.  
e.g.) PDF, EPUB file to image files.

### Main Features
- Repeat screenshot and form feed.
- (Optional) Auto fit triming size.
- (Optional) Auto finish.
- (Optional) Split page vertical.
- (Optional) Zip compression.

## Requirements
- Python3.10
    - PyAutoGui
    - PIL
    - pywin32

## Usage
1. Prepare `setting.json`.
2. Run `ssff.exe` or `python3 ssff.py`.
3. Input missing settings on console.
4. Do not touch your PC, until completed...

# Options
Option values can be prepared in advance in a configuration file (`setting.json`).  
If value is not present in the configuration file, you will be prompted to enter it.  

## Configuration file
To be placed in the current directory with the name `setting.json`.  
File format is JSON, encoding is UTF-8.  

Sample:  

```json
{
    "wait_before_start_ms": 5000,
    "interval_ms": 750,
    "output_dir_prefix": "output_",
    "fname_prefix": "page_",
    "trim": "fit-onetime"
}
```


## `start_file_no`
Start file number. (Integer)  

## `page_num`
Number of pages, or "auto". (Integer or String)  

It is a condition of program termination.  
If set to "auto", the program will automatically terminate when the same page is found.

## `page_direction`
Page direction. (String)  

Either "right" ("r") or "left" ("l").  

## `wait_before_start_ms`
Wait before start (ms). (Integer)  

## `interval_ms`
Interval (ms). (Integer)  

## `output_dir_prefix`
Output temporary directory prefix. (String)  

Output directory is created in the current directory.  

## `fname_prefix`
Image file name prefix. (String)

Image files are named with a prefix + sequential number.  

## `ss_left`, `ss_right`, `ss_top`, `ss_bottom`
Position of screenshot area, or "max". (Integer or String)  

Enter left, right, top, bottom, in that order.  
If set to "max", each end of the display size is used.  

![](./README/ss_left.png)
![](./README/ss_right.png)
![](./README/ss_top.png)
![](./README/ss_bottom.png)
![](./README/ss_area.png)

## `trim`
Trim position. (String)  

### "none" or "n".
No trimming.  

### "fit" or "f".
Automatically removes marginal areas (areas of the same continuous color) in screenshot images on all pages.

![](./README/fit.png)

### "fit-onetime" or "o".
Automatically removes marginal areas (areas of the same continuous color) in screenshot images. The trim size calculated for the first page (front cover) is used for all pages.  

## `vsplit`
Split image vertical, if width > height. (String)  

Set "yes" or "no".  

## `target_window`
Target window title. (String)  

If input this value, window with the specified string caption are automatically foreground.  
Allow substring.  

## `dir_name`
Output directory name. (String)  

Rename output directory after all processing. If not set, not rename.  

## `to_zip`
Zip compress output directory after all processing.  

Set "yes" or "no".  
