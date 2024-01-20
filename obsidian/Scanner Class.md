录入用户键盘输入的数据

请在程序中，提示用户通过键盘输入自己的姓名,年龄，并能在程序中收到这些数据，怎么解决？

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240111011640.png)

```

Scanner sc = new Scanner(System.in)  
int i=sc.nextInt() // 等待用户输入整数
用户按了回车之后会把那个整数交给i
String name= sc.next() // 等待用户输入字符串

```

使用 Scanner 接收用户键盘输入的数据，需要三个步骤：

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240111020145.png)
