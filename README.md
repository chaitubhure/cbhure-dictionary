# Dictionary

This is an assignment to run Dictionary program on a local machine and on a UNC Charlotte cluster and compare the performance of each using a Hadoop distributed file system.

### Technology and platfroms

This project makes use of the following technologies:

* [Cloudera Quickstart Virtual Machine](https://www.cloudera.com/downloads/quickstart_vms/5-13.html)
* [Virtualbox](https://www.virtualbox.org/)

### Steps to run

Following are the steps to run this job on Hadoop

```
Downloads required:
Download Cloudera Quickstart Virtual Machine 
Download Virtualbox a software from Oracle to run virtual machines.
Imports:
Import the Cloudera Quickstart Virtual Machine into the Virtualbox.
In VirtualBox, go to File -> Import Appliance. Input the path to the Cloudera Quickstart Virtual Machine in the prompt window.
After importing, start the virtual machine by clicking Start.
Initial steps:
In the Virtual Machine, Open Terminal.
Type : pwd. It should return /home/cloudera.
If that is not the directory shown, type  cd /home/cloudera.
Open any text editor or Eclipse and create your code as required. In this case we will consider the example of Matrix Multiplication although these steps remain the same for any java code to be run on hadoop.
Steps to create .JAR file: Execute the following commands:
export CLASSPATH=/usr/lib/hadoop/client-0.20/\*:usr/lib/hadoop
mkdir matrices_classes 
Makes a directory to store a to-be compiled class.
javac -d matrices_classes/ MatrixMultiply.java 
Compiles Java classes and stores them in the created directory.
jar -cvf MatrixMultiply.jar -C matrices_classes/ .
Creates a jar file.
Put input files into HDFS:
Create input files for matrix multiplication. To move to the hadoop file system, we have to execute the following command. Here, there are two input files for matrices M and N as text files. Both of these will be moved into the input directory which we will create now in the HDFS. Following is the sequence of commands we perform to execute this job.
hadoop fs -mkdir /user/cloudera/matrices
hadoop fs -mkdir /user/cloudera/matrices/inputMmatrix
hadoop fs -put M.txt /user/cloudera/matrices/inputMMatrix
hadoop fs -put N.txt /user/cloudera/matrices/inputMMatrix
Running the Hadoop Job:
Execute the following command:
hadoop jar MatrixMultiply.jar MatrixMultiplication1.MatrixMultiply /user/cloudera/matrices/inputMmatrix /user/cloudera/matrices/outputmultiply
Here, MatrixMultiplication1 is the package which will be different for different codes and users as well. The directory outputmultiply is the directory that is created at runtime. Everytime you run a hadoop job make sure you create a new directory for the output.

View the output of the job:
Execute the following command:
hadoop fs -ls /user/cloudera/matrices/outputmultiply
		This lists the files in the directory outputmultiply. The file which has “part-r-00000” 
		at its end is the one that is to be viewed.
Open the output file:
Execute the following command:
hadoop fs -cat /user/cloudera/matrices/outputmultiply/part-r-00000

	There we have our desired output !
  
  Runtime comparison:
  Dictionary on cloudera hadoop distribution: 3 minutes
  Dictionary on cluster: 15 seconds

```

### Authors

* [Chaitanya Bhure](https://github.com/chaitubhure)
