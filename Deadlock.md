# DeadLock����

����ʵ������������������ݣ�


- **Progress ** ��ʵ����̣������������Ľ��ͣ�
- **Result** ���޸���ʵ���Ժ�õ������н����
- **Question** ������������4����Ҫ������
- **Experimental experience ** ��ʵ����롢ʵ���ĵá�

------

[TOC]


## Progress(ʵ�����)

### �Թؼ���synchronized�Ľ���:

* ���ùؼ���` synchronized`������һ����������һ��������ʱ���ܹ���֤��ͬһʱ�����ֻ��һ���߳�ִ�иöδ��롣 

* ��һ���̷߳���` object`��һ��` synchronized`ͬ��������ͬ������ʱ�������̶߳�`object`����������` synchronized`ͬ��������ͬ�������ķ��ʽ��������� 


### Deadlock.java����:

```java
class A{
	synchronized void methodA(B b){
		b.last();
	}
	
	synchronized void last(){
		System.out.println("Inside A.last()");
	}
}
```

```java
class B{
	synchronized void methodB(A a){
		a.last();
	}
	
	synchronized void last(){
		System.out.println("Inside B.last()");
	}
}
```

```java
  class Deadlock implements Runnable{
	  A a = new A();
	  B b = new B();
	  
	  //���캯��
	  Deadlock(){
		  Thread t = new Thread(this);
		  int count = 20000;
		  
		  t.start();
		  while(count-- >0);
		  a.methodA(b); 		  
	  }

	@Override
	public void run() {
		// TODO Auto-generated method stub
		b.methodB(a);
	}
	public static void main(String args[]){
		new Deadlock();
	}
}
```


�� ` Deadlock.java` �����е�ʱ��` class`  ` A` ��` class` ` B` ��ʵ��` a` ��` b` �����������������Ź��캯��Ҳ��ִ�У��ڹ��캯���У��߳�` t`����������` t.start()` ��ִ�е�ʱ���߳�` t` �ͱ����뵽���ȶ������棬�����ȵ�����ʱ�򣬾���` run()` ����Ĵ��룬����` b` ʵ����` methodB()`��������ӡ��Ӧ�����֡����⣬�߳�` t`��ʼ�����Ժ󣬾���һ��ʱ����ӳ٣�ʵ��` a`��` methodA()`���������á����������߳�ͬʱ����ͬһ` class`�еķ���ʱ���ͻ�������������³����޷�����ִ����ȥ����Ҳ�ǹؼ���`synchronized` �����������µġ�


## Result(���н����ͼ)

![Alt text](./deadlock.png)


## Question(����������4����Ҫ����)

  ���������������߶�����̣���������Է�ռ�е���Դ�� 

* ����������  һ����Դÿ��ֻ�ܱ�һ������ʹ�á�
* �����뱣��������  һ��������������Դ������ʱ�����ѻ�õ���Դ���ֲ��š�
* ����������:  �����ѻ�õ���Դ����ĩʹ����֮ǰ������ǿ�а��ᡣ
* ѭ���ȴ�����:  ���ɽ���֮���γ�һ��ͷβ��ӵ�ѭ���ȴ���Դ��ϵ��



## Experimental experience(ʵ���ĵ�)

���ʵ��Ƚϼ򵥣����õ��Ĵ�����PPT�ж������ˡ�ͨ��ʵ���˽������������ԭ��ͱ�Ҫ������


