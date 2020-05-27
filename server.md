# Server workflow with processing images

1. Log in to the server with both a remote file browser ([WinSCP](https://winscp.net/eng/index.php) 
or [ForkLift](https://binarynights.com/)) and a terminal using `ssh`.
2. Use the file browser to locate the images you want to process.
3. Use the file browser to locate `run.sh` script, and make note of the relative path from the folder 
containing the script, to the image file(s).
4. Open up the `run.sh` script, edit it so that it will process the desired image.
5. In terminal, use `cd` to get to the folder containing the `run.sh` script.
6. Run `$ ./run.sh` to execute the script.
7. Once the script finishes running, go back to the file browser, and copy the processed `.txt` file to
your computer.
8. Put `txt_to_fits.py` file to the same folder as the copied `.txt` file.
9. Open up a new terminal window (so that it runs locally, not on the server), use `cd` to go to the
folder containing the `.txt` and the `.py` file.
10. Run `$ python txt_to_fits.py`. Note that you have to have `astropy` installed.

_Note: all the `$` sign above indicates that it is a command that you type into your terminal and then
execute. You should not manually input/copy the `$` sign itself when running those commands._