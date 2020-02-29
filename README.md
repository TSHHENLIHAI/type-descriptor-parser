# JVM/正则表达式/面向对象综合练习

这是一道有些难度的题目，你可能会在上面花上一天的时间，请做好心理准备。

但是如果你完成了这个挑战，你绝对会获得很多知识（JVM、正则表达式、面向对象）。

Ready? Go.

根据[Java虚拟机规范4.3.2](https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-4.html#jvms-4.3.2)，
在Java虚拟机内部使用精简的描述符来描述一个类型，以节省空间，如：

| 描述符        | 代表类型  | 备注                                                                                                     |
|---------------|-----------|----------------------------------------------------------------------------------------------------------|
| B             | byte      |                                                                                                          |
| C             | char      |                                                                                                          |
| D             | double    |                                                                                                          |
| F             | float     |                                                                                                          |
| I             | int       |                                                                                                          |
| J             | long      |                                                                                                          |
| L`<ClassName>`; | reference | 例如`java.lang.String`表示为`Ljava/lang/String;`                                                             |
| S             | short     |                                                                                                          |
| Z             | boolean   |                                                                                                          |
| [             | 数组      | 多维数组每增加一个纬度，前面增加一个`[`。例如，`int[]`的描述符是`[I`, `String[][]`的描述符是`[[Ljava/lang/String;`| 


同理，这些描述符也被用来描述方法，如方法

```
Object m(int i, double d, Thread t) {...}
```

在JVM内部的描述符是

```
(IDLjava/lang/Thread;)Ljava/lang/Object;
```

现在我们的问题是，给定一个类型描述符或者一个方法描述符，解析出它代表的实际类型。

如，给定方法描述符`(IDLjava/lang/Thread;)Ljava/lang/Object;`，你应该能够解析出`java.lang.Object (int i, double d, java.lang.Thread t)`。