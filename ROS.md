# ROS������־
����ʵ�����**markdown**�������������ݣ�


- **Description** ����ROS & Cartographer��������
- **How to install ** ��ROS ��װ�ʼǣ�
- **Experimental experience ** ��ʵ����롢ʵ���ĵá�


-----------------------------


[TOC]

## Description(ROS & Cartographer����)

	ROS�������˲���ϵͳ��Robot Operating System������רΪ�����������������Ƴ�����һ�׵��Բ���ϵͳ�ܹ�������һ����Դ��Ԫ������ϵͳ�������ϵͳ�����ṩ�����ڲ���ϵͳ�ķ��񣬰���Ӳ�������������ײ���������������ù��ܵ�ִ�С��������Ϣ���ݡ������а�������Ҳ�ṩһЩ���ߺͿ����ڻ�ȡ����������д��ִ�ж���ںϵĳ���
	ROS�����мܹ���һ��ʹ��ROSͨ��ģ��ʵ��ģ���P2P������ϵ��������ӵĴ���ܹ�����ִ�����������͵�ͨѶ���������ڷ����ͬ��RPC��Զ�̹��̵��ã�ͨѶ������Topic���첽������ͨѶ�����в����������ϵ����ݴ洢��

```
Cartographer�ǹȸ蹫˾������һ�Դ��ͼ���ߣ��ü�������ͬ����λ����ͼ����(SLAM)�������ڽ���ƽ��ͼ����ͬʱ���ڶ�ά����ά�ռ���ƶ�ӳ�䡣ͬʱ����Դ Cartographer �������п�Դ�����˲���ϵͳ(ROS)��ʹ�øü���������ڲ�������ˡ����˼�ʻ�����˻���ϵͳ��
```


## How to install(ROS & Cartographer��װ�ʼ�)

#### ROS ��װ�ʼ�

1.  ��������⣺

2.  �������Դ��sources.list��
    `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`
 
3.  ���� keys��
    `sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116`
>![Alt text](./ROS3.png)

4.  ��װ��
* ���������
  `sudo apt-get update`
>![Alt text](./ROS4.png)

* ������װ�����ROS��
  `sudo apt-get install ros-kinetic-desktop-full`
>![Alt text](./ROS4_2.png)


5. ��ʼ�� rosdep��
   `sudo rosdep init`
   >![Alt text](./ROS5.png)
   `rosdep update`
>![Alt text](./ROS5_2.png)



6. �������ã�
   ` echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc`
   ` source ~/.bashrc`

7. ��װ rosinstall ��
* `sudo apt-get install python-rosinstall`
>![Alt text](./ROS7.png)




## Experimental experience(ʵ���ĵ�)


* ����ʵ��Ҳ�Ƚϼ���ROL�Ĺ����У�������վ�����Ĳ��裬˳�����á�





