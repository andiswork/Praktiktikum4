# **Modul 4 Practicum Report**

### By : Andi Tadang Palie  &  Rifqi Naufal

* First, make 2 copies of containers, and then start

![1](https://user-images.githubusercontent.com/93029648/148412839-8ff93eed-97ca-48a4-a777-ee113913a238.PNG)


![2](https://user-images.githubusercontent.com/93029648/148415497-65d211bb-0b2f-423b-aee8-89471154a7b4.PNG)



* Next, open ubuntu_php7.4_2 and change the IP address to 10.0.3.111/24. Do the same thing on ubuntu_php7.4_3, change the IP address to 10.0.3.121

![3](https://user-images.githubusercontent.com/93029648/148415657-c73593fd-bace-4dba-8c5d-ef8fbc7f3f2b.PNG)



* Go to lxc_php7_2.dev and change the server name

![4](https://user-images.githubusercontent.com/93029648/148415902-09d1e09a-2ee0-4955-aa13-a773b372204d.PNG)
![5](https://user-images.githubusercontent.com/93029648/148415907-875598aa-2f29-4e8f-930d-6e3a55fdda14.PNG)


* Restart nginx and curl it. 

  
![32](https://user-images.githubusercontent.com/93029648/148416459-95b6210b-eb02-4ddf-b994-36a0c2a3f9c4.PNG)


* Next step is ubuntu_php7.4_3 (IP 10.0.3.121), debian_php5.6_2 (IP 10.0.3.112), debian_php5.6_3 (IP 10.0.3.122) the same as ubuntu_php7.4_2.
* Add name server /etc/hosts (on VM)


![9](https://user-images.githubusercontent.com/93029648/148416545-efd06742-d46f-424e-b2d4-6d15ae261592.PNG)


* Run the jmeter, and change the number of threads

![10](https://user-images.githubusercontent.com/93029648/148417106-c297d40b-7ae8-4bbb-8c68-677458b103fe.PNG)
![11](https://user-images.githubusercontent.com/93029648/148417118-911c059d-35a3-4b01-9ff6-2ce5a5bf8c31.PNG)
![12](https://user-images.githubusercontent.com/93029648/148417123-2be863e5-1d59-4735-9300-18485450b6ab.PNG)
![13](https://user-images.githubusercontent.com/93029648/148417128-d48fd867-e2b7-4b02-9292-80f8ce23e0fc.PNG)
![14](https://user-images.githubusercontent.com/93029648/148417133-7946c949-d612-455a-a99c-9bec7710c138.PNG)
![15](https://user-images.githubusercontent.com/93029648/148417137-1affc5ed-7985-4476-9890-1ae25509b221.PNG)
![16](https://user-images.githubusercontent.com/93029648/148417141-54001e1d-40ad-4470-be24-a679205f31d3.PNG)
![17 1](https://user-images.githubusercontent.com/93029648/148417151-4efd2f95-0081-4767-9be4-66faccf4d2f8.PNG)
![17](https://user-images.githubusercontent.com/93029648/148417160-427cd683-841c-45d6-9414-db45e15e1a96.PNG)
![18](https://user-images.githubusercontent.com/93029648/148417177-91ab1b87-8136-423a-9216-15c191a145d2.PNG)
![19](https://user-images.githubusercontent.com/93029648/148417184-b6f81b15-b066-44fd-a9ac-ac64fa9d049c.PNG)
![20](https://user-images.githubusercontent.com/93029648/148417192-4bd720d0-1f79-4cc4-85a7-0590ab9103a8.PNG)


Go back to the VM and write the script as below to add upstream landing, php5,and php7


```markdown
nano /etc/nginx/sites-available/vm.local
```
to add upstream landing, php7

![21](https://user-images.githubusercontent.com/93029648/148418917-0e349524-1b49-4adc-8dc5-7b7f5e3eca89.PNG)


Then we go back to the jmeter 
  
* 50
![10](https://user-images.githubusercontent.com/93029648/148419493-dd80c6d2-4874-4cec-9ab5-3e7e6cc705e4.PNG)
![23](https://user-images.githubusercontent.com/93029648/148419701-1baf0381-6d77-4f53-9238-5b1aa619d9cd.PNG)
![24](https://user-images.githubusercontent.com/93029648/148419711-c56be1cf-e58c-45a6-b373-6455cc687c1a.PNG)
![25](https://user-images.githubusercontent.com/93029648/148419717-3cecfd20-f098-4e6f-bb31-babedbf441ac.PNG)



* 100
![14](https://user-images.githubusercontent.com/93029648/148419616-b2fa59f2-ecd9-4fc8-aff7-84329c3f83c6.PNG)
![26](https://user-images.githubusercontent.com/93029648/148419829-f10c0bae-d867-4492-9753-b72e30830887.PNG)
![27](https://user-images.githubusercontent.com/93029648/148419844-fc3c592c-2474-47e6-b9f1-61b368bdff20.PNG)
![28](https://user-images.githubusercontent.com/93029648/148419850-9ff3ad3a-f627-4db8-ab2d-cd5c2d8c7961.PNG)


* 150
![17 1](https://user-images.githubusercontent.com/93029648/148419639-f41fe137-b0aa-4499-89c0-4f2c85b8a96f.PNG)
![29](https://user-images.githubusercontent.com/93029648/148419870-d252b7d1-9191-40d0-bee8-f8512baa6228.PNG)
![30](https://user-images.githubusercontent.com/93029648/148419874-a34db1b2-7d27-46e1-8542-d507406286d8.PNG)
![31](https://user-images.githubusercontent.com/93029648/148419887-21e65dee-9762-43c0-8305-0115cd695881.PNG)



### Analysis

Below is the results from when we use load balancer and not using the load balancer

 - When there is 50 users that access our web, if we don't use load balancer the average time of user accessing our web is
   - landing : 1115 ms / 1.1 s
   - blog : 1555 ms / 1.5 s
   - app : 4 ms / 0.004 s
- When we use load balancer, then
   - landing : 37 ms / 0.037 s
   - blog : 27 ms / 0.027 s
   - app : 21 ms / 0.021 s

Here we can know that the average time of user accessing our web is faster then if we don't use load balancer. For the throughput or the amount of user accessing our web is
- When there is 50 users that access our web, if we don't use load balancer the amount of user accessing our web is

  - landing : 36 user / second
  - blog :  20 user / second
  - app : 41 user / second

- When we use load balancer, then

  - landing : 427 user / second
  - blog :  439 user / second
  - app : 446 user / second

The conclusion is, if we use load balancer, then the time is faster and the amount of users that accessing our web is much more then when we don't use load balancer.

*Thank you* 
