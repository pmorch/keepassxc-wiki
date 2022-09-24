This documents the different export formats.

The UI allows export in CSV and HTML formats. The command-line `keepassxc-cli
export` allows XML export.

These fields are included in all the CSV, HTML and XML export formats:
"Group","Title","Username","Password","URL","Notes","TOTP","Icon","Last
Modified","Created"

For CSV the "Icon" is the standard icon id (number), not the actual icon data and not custom icons.

The HTML export, which is only intended for human consumption, also contains
"Additional Attributes".

The XML export (only accessible from the command line as keepassxc-cli export -
see #8496) contains everything, including Custom Data like "Additional
Attributes" and "History". Except that XML export does not export attachments,
the database credentials or anything in the header of the kdbx file like KDF
used and unencrypted file data.

None of the export formats include attachments. The only way to export attachments
is to save the files individually.

