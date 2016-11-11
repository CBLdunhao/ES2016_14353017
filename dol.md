# DOLʵ������&���

����ʵ������������������ݣ�

- **Progress ** ���޸�ʵ���Ĺ��̣�
- **Result** ���޸���ʵ����Ľ����
- **Experimental experience ** ��ʵ����롣

------

[TOC]



## Progress(�޸�ʵ���Ĺ���)

### Example1: 

?	��example1�У�Ҫ���޸�` square.c` �еĴ��룬ʹ��������������3�η���������` square.c` �ļ��еĹؼ����룺

```c
int square_fire(DOLProcess *p) {
    float i;

    if (p->local->index < p->local->len) {
        DOL_read((void*)PORT_IN, &i, sizeof(float), p);
        i = i*i;
        DOL_write((void*)PORT_OUT, &i, sizeof(float), p);
        p->local->index++;
    }

    if (p->local->index >= p->local->len) {
        DOL_detach(p);
        return -1;
    }

    return 0;
}
```

����` i = i * i` ��ʾ��ǰ������������Ľ����2�η�����Ҫʵ�����3�η�����ֻ��Ҫ��` i = i * i` �ĳ� ` i = i * i * i` ���ɡ��޸ĺ�Ĵ������£�

```c
int square_fire(DOLProcess *p) {
    float i;

    if (p->local->index < p->local->len) {
        DOL_read((void*)PORT_IN, &i, sizeof(float), p);
        i = i * i * i;
        DOL_write((void*)PORT_OUT, &i, sizeof(float), p);
        p->local->index++;
    }

    if (p->local->index >= p->local->len) {
        DOL_detach(p);
        return -1;
    }

    return 0;
}
```



### Example2:

?	��example2��Ҫ�����޸�` example2.xml` �е�`iterator`��ʹ���е�squareģ����`3` �����`2` �����������4�η�����������` example2.xml` �ļ��Ĺؼ����룺

```xml
<variable value="3" name="N"/>
```

```xml
 <!-- instantiate resources -->
  <process name="generator">
    <port type="output" name="10"/>
    <source type="c" location="generator.c"/>
  </process>

  <iterator variable="i" range="N">
    <process name="square">
      <append function="i"/>
      <port type="input" name="0"/>
      <port type="output" name="1"/>
      <source type="c" location="square.c"/>
    </process>
  </iterator>

  <process name="consumer">
    <port type="input" name="100"/>
    <source type="c" location="consumer.c"/>
  </process>

  <iterator variable="i" range="N + 1">
    <sw_channel type="fifo" size="10" name="C2">
      <append function="i"/>
      <port type="input" name="0"/>
      <port type="output" name="1"/>
    </sw_channel>
  </iterator>

```

��δ�޸ĵĴ����У�ͨ������������` 3 ` ��`  square` ģ�飬����

```xml
<variable value="3" name="N"/>
```

���д�����` value` ��ֵ����ʾ�����Ĵ�����Ҳ��ʾ�������ɵ�` square` ģ�����Ŀ�����ǽ�����` value` ��ֵ��Ϊ` 2` ���޸ĺ�Ĵ������£�

```xml
<variable value="2" name="N"/>
```

## Result(���н����ͼ)

* example1 :
![Alt text](./example1.png)
* example2 : 
![Alt text](./example2.png)


## Experimental experience(ʵ���ĵ�)

���ʵ��Ƚϼ򵥣�ֻ��Ҫ�������ļ��и����޸�һ�д��뼴�ɡ�ͨ������ʵ���dol�и�ģ��֮������ӷ�ʽ����һ������� ��
