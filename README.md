- **Description** ��DOL �������(����ʵ����е�����ӡ��޸�)��
- **How to instal** ��DOL ��װ�ʼǣ�
- **Experimental experience** ��ʵ����롢ʵ���ĵá�

-------------------

[TOC]

## Description
> 

## How to install
> 1����װһЩ��Ҫ�Ļ���(ubuntuΪ��)��
* `$ sudo apt-get update`
* `$ sudo apt-get install ant`
* `$ sudo apt-get install openjdk-7-jdk`
* `$ sudo apt-get install unzip`

>2�������ļ�(ʹ��Vmware�������Ҳ���Դ������������������ȥhttp://jingyan.baidu.com/article/c33e3f48a5c153ea15cbb5b2.html)��
* `sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz`
* `sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`

>3����ѹ�ļ�
* �½�dol���ļ��� 
 `$ mkdir dol`
* ��dolethz.zip��ѹ�� dol�ļ�����
`$	unzip dol_ethz.zip -d dol`
* ��ѹsystemc
`$	tar -zxvf systemc-2.3.1.tgz`

>4������systemc
* ��ѹ�����systemc-2.3.1��Ŀ¼��
`$	cd systemc-2.3.1`
* �½�һ����ʱ�ļ���objdir
`$	mkdir objdir`
* ������ļ���objdir
`$	cd objdir`
* ����configure(�ܸ���ϵͳ�Ļ�������һ�²��������ڱ���)
`$	../configure CXX=g++ --disable-async-updates`
��ͼΪ����configure֮��Ľ�ͼ![Alt text](./1.png)
* ����
`$	sudo make install`
* ��¼��ǰ�Ĺ���·��(�������ǰ����·��������������������)
`$	pwd`

>5������dol
* ����ո�dol���ļ���
`$	cd ../dol`
* �޸�build_zip.xml�ļ�
�ҵ�������λ�������˵��������systemcλ�������
`<property name="systemc.inc" value="YYY/include"/>`
`<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`
��YYY�ĳ���ҳpwd�Ľ����ע�⣬����  64λ ϵͳ�Ļ�����lib-linuxҪ�ĳ�lib-linux64��
* Ȼ���Ǳ���
`$	ant -f build_zip.xml all`
���ɹ�����ʾbuild successful
���ſ����������е�һ������
* ����build/bin/mian·����
`$	cd build/bin/main`
* Ȼ�����е�һ������
`$	ant -f runexample.xml -Dnumber=1`
�ɹ������ͼ
>![Alt text](./2.png)


## Experimental experience
* Lab1ʵ���ĵ����������������ĵ�����DOL�Ĺ����У��������5С������ע�⣬����  64λ ϵͳ�Ļ�����lib-linuxҪ�ĳ�lib-linux64������Ϊ�Ƕ����Լ�������64λϵͳ��Ҫ�ģ�һ��ʼ���ˣ����������������в��ɹ���ѯ��ͬѧ��Ļ������Ӿ����гɹ��ˡ�
* Lab2 ��װ��ʹ��Git�Ĺ��̲�δ�������⡣
* ͨ��������ʵ�飬ѧϰ����Git�����֪ʶ���ڴ��ĵ��ı�д��ѧϰ��markdown������﷨��