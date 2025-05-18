 # **What is IPFS?**

 ![image](https://github.com/user-attachments/assets/08e9d9cf-9f8a-49da-85d2-c3289ffb61eb)

**IPFS (InterPlanetary File System) is a peer-to-peer distributed file storage system. It allows users to store and share files in a decentralized way, using content-based addressing instead of location-based URLs.**

**Key Features:**

**->Files are identified by cryptographic hashes.**

**->Supports versioning and offline-first design.**

**->Efficient bandwidth usage via deduplication.**

**->Nodes store and cache files they access.**

# Step by Step implementation of Commands.....

1.	Install the IPFS through WSL:``` wget https://dist.ipfs.tech/kubo/v0.32.1/kubo_v0.32.1_linux- 
            amd64.tar.gz```

2.	```tar -xvzf kubo_v0.32.1_linux-amd64.tar.gz```
	
3.	Kubo is a reference implementation of IPFS in Go:``` cd kubo```
  
4.	```ls```
   
5.	```sudo bash install.sh```
	
6.	```ipfs –version```
	
7.	```ipfs init```

![image](https://github.com/user-attachments/assets/ea661173-ffd8-4a31-a396-022b61e7e494)

8.	```ipfs daemon```

![image](https://github.com/user-attachments/assets/8abc6ef6-29c8-4fca-8e87-bebef5ff5e6e)

9.	```On Browser: http://127.0.0.1:5001/webui```

![image](https://github.com/user-attachments/assets/b024109f-560e-4a55-bef7-b3a60a381dfe)


10.	```To run ipfs daemon in background: ipfs daemon > ipfs.log 2>&1 &```
	
11.	```This is daemon ID: [1] 772```
	
12.	```Add file: echo "Hello, IPFS!" > hello.txt```
	
13.	```ipfs add hello.txt```

![image](https://github.com/user-attachments/assets/10a7ef49-0f73-45ef-bd47-a609e2ce51fc)
![image](https://github.com/user-attachments/assets/2009cbff-c07b-40a3-857e-d34e583397f9)

14.``` ipfs cat <CID>```

15.	Add a directory: ```mkdir myfolder```
    
```echo "File 1 content" > myfolder/file1.txt```

```echo "File 2 content" > myfolder/file2.txt```

16.	```ipfs add -r myfolder```
	
17.	```ps aux | grep ipfs```
	
18.	```kill <PID>```

![image](https://github.com/user-attachments/assets/7cc13715-0e33-4d0a-9a76-e35627136e23)

19.	```In Browser you can directly run this to see the IPFS: https://ipfs.io/ipfs/QmWd9cavD8UGZQcqYBVhZqs2Jure5W9cgxR7S6TC4StfZe```

![image](https://github.com/user-attachments/assets/48f3eaa8-da51-4597-bdee-7f300e82d0bc)

# Privacy and encryption on IPFS through command line..

1.	```echo "Hello, IPFS!" > myfile.txt```
	
2.	```ipfs add myfile.txt
	openssl enc -aes-256-cbc -pbkdf2 -iter 100000 -salt -in myfile.txt -out myfile_encrypted.txt -pass pass:yourpassword```
	
3.	```ipfs add myfile_encrypted.txt```
	
4.	```cat myfile_encrypted.txt```
	
5.	```openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -in myfile_encrypted.txt -out decrypted_file.txt -pass pass:yourpassword```
	
6.	```cat decrypted_file.txt```
	
7.	```ipfs add decrypted_file.txt```

![image](https://github.com/user-attachments/assets/9341543e-625e-4477-b08e-360f2f57dfae)
