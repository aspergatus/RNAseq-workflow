Ubuntu Linux installation in Virtual Box
================

Install miniconda3 as described on Miniconda website

Downgrade to python 3.7.0 (Version  3.8 causes conflict later)

Sortmerna: indexdb_rna is missing in the version coming with conda. Fix for now: installing into linux by sudo apt install sortmesna

Create Share Folder 
================
Devices->Install Guest Additions

Run the program VBoxLinuxAdditions.run. When the program completes reboot your VirtualBox.
``` bash
$ sudo ./VBoxLinuxAdditions.run
``` 
Create a folder in Windows Host, for example "VirtualBox_Share"
In Virtual Box, add "Ubuntushare" into Devices->Shared Folders

Mounting to Ubuntu
===
``` bash
$ sudo mkdir ~/Desktop/windowsshare
$ sudo mount -t vboxsf VirtualBox_Share ~/Desktop/windowsshare
``` 
Install SRA Toolkit
=

``` bash
wget --output-document sratoolkit.tar.gz http://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz

tar -vxzf sratoolkit.tar.gz
```
Append bin into PATH

``` bash
export PATH=$PATH:$PWD/sratoolkit.2.4.0-1.mac64/bin
```
Verify bin can be found
``` bash
which fastq-dump
```
Test if it works
``` bash
fastq-dump --stdout SRR390728 | head -n 8
```
