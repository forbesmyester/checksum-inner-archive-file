# checksum-inner-archive-file

Checksums all files within an archive (7z, zip or rar) without extracting the archive.

It outputs a TSV (tab seperated) file.

## Usage

    checksum-inner-archive-file [-H] [-m METHOD] [-t FILETYPE] FILENAME

    -H = Skip adding the header
    -m = Specify the program to use for hashing (defaults to md5sum)
    -t = Specify file type if not guessable. Valid values: zip
    -h = Displays this help

## Example

    $ zip -9 checksum-inner-archive-file.zip checksum-inner-archive-file  README.md
      adding: checksum-inner-archive-file (deflated 67%)
      adding: README.md (deflated 40%)

    $ ./checksum-inner-archive-file checksum-inner-archive-file.zip  | xsv table -d $'\t'
    External Filename                md5sum                            Internal Filename
    checksum-inner-archive-file.zip  e1ad7f069176fc27020be011cb82fdcb  checksum-inner-archive-file
    checksum-inner-archive-file.zip  b4cfb0cd617964cd87ff050b772d36b9  README.md

## Requirements

 * gnu-parallel
 * awk
 * bash
 * sed
 * tr
 * grep
 * cat
 * echo

## Optional Requirements

 * 7z
 * unzip
 * unrar

## License

The code is licensed under GPL v2
