TFTPlunder: Genesys TFTP Server Arbitrary Directory Blind Read Write exploitation helper (CVE-2023-29930)

## Vulnerability info

This vulnerability is due to unrestricted configuration options for the TFTP root path and file extensions. In other words, from the Admin interface, you can change the TFTP to any directory at all and upload or download whatever files you want.

(Note however that TFTP as a protocol does not allow for file listing, which is what makes this a *Blind* file read vulnerability.)

It is particularly compounded by the fact that the server by default uses hardcoded known credentials and does not force the user to change them.

Classification-wise, it has aspects of the following CWEs:

* CWE-22: Improper Limitation of a Pathname to a Restricted Directory
* CWE-434: Unrestricted Upload of File with Dangerous Type
* CWE-522: Insufficiently Protected Credentials

All known versions to date are vulnerable.

## Mitigation

The best mitigation for now is simply to update the Admin credentials to the TFTP configuration server.

## Using this exploit

I'd recommend using it with either a Jupyer notebook or the Python REPL loop.
Just import the main python file, instantiate the class, and call get_file and put_file as you please.

```
$ python3
>>> from tftplunder import TFTPlunder
>>> tp=TFTPlunder("example.com")
>>> tp.get_file("C:/Windows/Panther/Unattended.xml")
>>> tp.get_file("C:/ProgramData/ntuser.pol")

```

etcetera

hint: see https://github.com/jtpereyda/regpol for help decoding ntuser.pol

see also https://www.soffensive.com/posts/web-app-sec/2018-06-19-exploiting-blind-file-reads-path-traversal-vulnerabilities-on-microsoft-windows-operating-systems/
and https://github.com/soffensive/windowsblindread/blob/master/windows-files.txt
