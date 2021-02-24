# Adding and removing users scripts

This project allows a user to create and remove a batch of university student Unix user accounts 
with the use of two simple scripts.

## Adding users
The 'addingUsers' script can be run to add system user accounts from a list of names saved in a 
'names.txt' file.

Names within the 'names.txt' file should be listed in the following format, on their own individual
lines:

`ENROLLMENT_TYPE	LASTNAME	FIRSTNAME	MIDDLENAME	DEGREE_CODE`

Please note that:
`ENROLLMENT_TYPE` should be the two-letter code for the type of enrolled the student or 
ex-student is.
`FIRSTNAME` and `MIDDLENAME` may be omitted. `LASTNAME` may not.
`DEGREE_CODE` should be the uppercase shortcode for the student's major.
Each piece of information should be separated by a tab character.

So for example, a correctly formatted line might look like:

GR	Joe	Billy	Bob	BIO

User accounts will be created with a username in the form FIRSTINITIAL-MIDDLEINITIAL-LASTNAME-[NUMBER]
Therefore, the above example would create a user account with the name 'bbjoe'
If a user account with the same username has already been created by the script, an incrementing
number will be appended to each successive duplicate username (i.e. '2', and then '3', etc.)

User accounts will be created with a default password of their last name. This should be changed as soon as possible.

The list of usernames to all accounts created are stored in a created file named 'usernames.txt'.
This file should be stored for future reference and for use in later removing the user accounts
if the administrator so desires.

## Removing users
User accounts can be removed by running the 'removingUsers' script. All files and directories 
associated with the users will be removed as well.

The 'removingUsers' script removes all users whose usernames are found in the file titled 
'usernames.txt'. Each username within this file should be located on its own individual line.

**Important Note:** Usernames are not removed from the 'usernames.txt' after running the
'removingUsers' script, nor is the text file deleted. This is so that the list of deleted usernames
may be referred back to for future reference. However, this means that the 'usernames.txt' file
must be deleted or removed before the 'addingUsers' file is run again to ensure that new usernames
are not appended to the old list.

## Additional notes
To avoid warnings about missing mail spools when the 'removingUsers' script is run, ensure that
the system's `MAIL_DIR` directory is properly set in '/etc/login.defs' and that
`CREATE_MAIL_SPOOL=yes` is set in '/etc/default/useradd'.

---
For any questions, please contact the authors Ethan Whitted or Ashley Rhoads at 
ewhitted17@georgefox.edu, or arhoads18@georgefox.edu, respectively.
