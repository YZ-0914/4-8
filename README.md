# 4-8
#define _CRT_SECURE_NO_WARNINGS 1
#include<iostream>
#include<cstdlib>
#include<cstdio>
#include<ctime>
#include<Windows.h>

using namespace std;

////蛇形矩阵算法
////它由1开始的自然数依次排列成的一个矩形上三角形、环形或对角线等的走法，输入文件由一行或多行构成，每行由一个正整数N组成（N不大于100）。
////在程序设计时需要运用到while循环行数，还有函数调用，以及要运用数学公式来实现蛇形矩阵算法的设计
int main()
{
	int num;
	cout << "请输入一个阶乘数（最好1~10内）：";
	cin >> num;
	int* arr = new int[num*num];
	const int step[4][2] = { 0, 1, 1 - 1, 1, 0, -1, 1 };
	arr[0] = 1;

	for (int x = 0, y = 0, state = 0, cur = 2; cur <= num*num;)
	{
		x += step[state][0];
		y += step[state][1];
		arr[y*num + x] = cur++;
		switch (state)

		{
		case 0://向下
				state = x == 0 ? 1 : 3;
				break;
			case 1://右上方向
				if (y == 0 || x == num - 1)

				{
					state = x == num - 1 ? 0 : 2;
				}
				break;
			case 2://向右
				state = y == 0 ? 3 : 1;
				break;
			case 3://左下方向
				if (x == 0 || y == num - 1)
				{
					state = y == num - 1 ? 2 : 0;
				}
		}
	}
	for (int y = 0; y < num; y++)
	{
		for (int x = 0; x < num; x++)
			cout << arr[y*num + x] << "\t";
		cout << endl;
	}
	delete[]arr;
	system("pause");
}

//2.环形输出
//例如：一个n*n矩阵里按照下图形式填充，最后形成的矩阵即为环形蛇形矩阵，下图是
//n=5时的蛇形矩阵，以数字1为起点呈顺时针走向：
//#include<cstring>
//#include<cstdio>
//
//const int max = 10;
//int a[max][max];
//int main()
//{
//	SetConsoleTitle("环形蛇形矩阵算法");
//	int n;
//	cout << "请输入一个整数：";
//	cin >> n;
//	int total, x, y;
//	memset(a, 0, sizeof(a));
//	total = a[x = 0][y = 0] = 1;
//	while (total < n*n)
//	{
//		while (y + 1 < n&&!a[x][y + 1])
//		{
//			a[x][++y] = ++total;
//		}
//		while (x + 1 < n&&!a[x + 1][y])
//		{
//			a[++x][y] = ++total;
//		}
//		while (y - 1 >= 0 && !a[x][y - 1])
//		{
//			a[x][--y] = ++total;
//
//		}
//		while (x - 1 >= 0 && !a[x-1][y])
//		{
//			a[--x][y] = ++total;
//		}
//	}
//	for (x = 0; x < n; x++)
//	{
//		for (y = 0; y < n; y++)
//		{
//			printf("%3d", a[x][y]);
//		}
//		cout << endl;
//	}
//	return 0;
//}
//
//
























//
//
//int main()
//{
//	//外层循环控制行（行数，换行）
//	//内层循环控制列（列数，列的图型）
//	for (int i = 0; i < 4; i++)
//	{
//		for (int j = 0; j <= 2 - i; j++)
//		{
//			cout << " ";
//		}
//		for (int j = 0; j <= 2 * i; j++)
//		{
//			if (j == 0 || j == 2 * i)
//
//				cout << "*";
//			else
//				cout << ' ';
//		}
//		cout << endl;
//	}
//	//图形的下层
//	for (int i = 0; i < 3; i++)
//	{
//		for (int j = 0; j <= i; j++)
//		{
//			cout << " ";
//		}
//		for (int j = 0; j <= 4-2 * i; j++)
//		{
//			//在j是极值的情况下打印星号，否则打印空格
//			if (j == 0 || j == 4 - 2 * i)
//
//				cout << "*";
//			else
//				cout << ' ';
//		}
//		cout << endl;
//	}
//	return 0;
//}

//int main()
//{
//	//外层循环控制行（行数，换行）
//	//内层循环控制列（列数，列的图型）
//	for (int i = 0; i < 4; i++)
//	{
//		for (int j = 0; j <= 2 - i; j++)
//		{
//			cout << " ";
//		}
//		for (int j = 0; j <= 2 * i; j++)
//		{
//			cout << (char)('A'+i);
//		}
//		cout << endl;
//	}
//	//图形的下层
//	for (int i = 0; i < 3; i++)
//	{
//		for (int j = 0; j <= i; j++)
//		{
//			cout << " ";
//		}
//		for (int j = 0; j <= 4-2 * i; j++)
//		{
//			cout << (char)('E'+i);
//		}
//		cout << endl;
//	}
//	return 0;
//}



//int main()
//{
//	//外层循环控制行（行数，换行）
//	//内层循环控制列（列数，列的图型）
//	for (int i = 0; i < 4; i++)
//	{
//		for (int j = 0; j <= 2 - i; j++)
//		{
//			cout << " ";
//		}
//		for (int j = 0; j <= 2 * i; j++)
//		{
//			cout << "*";
//		}
//		cout << endl;
//	}
//	//图形的下层
//	for (int i = 0; i < 3; i++)
//	{
//		for (int j = 0; j <= i; j++)
//		{
//			cout << " ";
//		}
//		for (int j = 0; j <= 4-2 * i; j++)
//		{
//			cout << "*";
//		}
//		cout << endl;
//	}
//	return 0;
//}

//int main()
//{
//	//感受双循环
//	for (int i = 0; i < 5; i++)
//	{
//		for (int j = 0; j < 5; j++)
//		{
//			cout << "*";
//		}
//		cout << endl;
//	}
//}

//int main()
//{
//	//外层循环控制行（行数，换行）
//	//内层循环控制列（列数，列的图形）
//	for (int i = 0; i < 10; i++)
//	{
//		for (int j = 0; j < 5; j++)
//
//		{
//			cout << "*";
//		}
//		cout << endl;
//	}
//}

//int main()
//{
//	//打印星星图案
//	//需要控制行数
//	for (int i = 1; i <= 7; i++)
//	{
//
//	}
//	//需要控制每行星星数量    ==列数
//	//int j = 1;//每行星星数量
//	//j += 2;
//	for (int j = 1; j <= 7; j += 2)
//	{
//
//	}
//
//}


//int main()
//{
//	//求1-100之间的偶数和
//	//循环累加
//	//判断是否为偶数：模2是否为0
//	//如果为奇数就跳过，如果为偶数则执行累加
//	int sum = 0;
//	for (int i = 1; i <= 100; i++)
//	{
//		//if (i % 2 == 0)
//		//	continue;//err  这是奇数和2500
//		if (i % 2 == 1)
//			continue;
//		sum += i;
//	}
//	cout << sum << endl;
//	return 0;
//}

//改成do while
//int main()
//{
//	//循环输入5个玩家的消费，统计消费额低于500的玩家数量
//	double money;//玩家的消费
//	int playerCount = 0;   //低于500玩家的数量（计数器）
//	//for (int i = 0; i < 5; i++)
//	int i = 0;
//	do{
//		i++;
//		cout << "请输入当前玩家的消费额：";
//		cin >> money;
//		//跳过500以上的情况
//		if (money >= 500)
//			continue;
//		playerCount++;
//	} while (i<5);
//	cout << "消费低于500的玩家数量是：" << playerCount << endl;
//	return 0;
//}


//int main()
//{
//	//循环输入5个玩家的消费，统计消费额低于500的玩家数量
//	double money;//玩家的消费
//	int playerCount = 0;   //低于500玩家的数量（计数器）
//	for (int i = 0; i < 5; i++)
//	{
//		cout << "请输入当前玩家的消费额：";
//		cin >> money;
//		//跳过500以上的情况
//		if (money >= 500)
//			continue;
//		playerCount++;
//	}
//	cout << "消费低于500的玩家数量是：" << playerCount << endl;
//	return 0;
//}

//int main()
//{
//	//幸运53猜商品价格游戏
//	//根据猜的次数给予不同的奖励
//	//1次：iphone8s plus plus 土豪金
//	//2-3次：小米移动电源
//	//5次以内：VR眼镜
//	const double PRICE = 5000.0;  //要猜的商品价格，可以是随机数字
//	double guessprice;                   //用户猜的商品价格
//	int guesscount = 0;                  //用户猜测的次数
//	//游戏实际上就是一个死循环
//	for (;;)
//	{
//		//每猜一次，猜测的总次数+1
//		guesscount++;
//		cout << "请输入神秘商品的价格：";
//		cin >> guessprice;
//		if (guessprice > PRICE)
//		{
//			cout << "大了" << endl;
//		}
//		else if (guessprice < PRICE)
//		{
//			cout << "小了" << endl;
//		}
//		else
//		{
//			cout << "恭喜，猜对了！" << endl;
//			break;
//		}
//	}
//	cout <<"您一共猜了"<< guesscount <<"次。"<< endl;
//}

//int main()
//{
//	int age;
//	//while(true/1)
//	for (;;)
//	{
//		cout << "请输入玩家年龄：";
//		cin >> age;
//		if (age < 0){
//			cout << "输入的数据非法！！！" << endl;
//			break;
//		}
//	}
//	cout << "这是强制退出后的代码！！！" << endl;
//}

//int main()
//{
//	//1.通过观察，每个月第一天要打印\t用来表示1号是周几
//	//因为7月1号是星期2，所以应该打印1个\t得出的规律：
//	//\t的数量=星期几-1=dayofweek-1
//	int day = 31;
//	int dayofweek = 2;  //星期二
//	cout << "一\t二\t三\t四\t五\t六\t日" << endl;
//	for (int i = 0; i < dayofweek - 1; i++)
//	{
//		//非常纯洁：打印\t
//		cout << '\t';
//	}
//	//第二个for循环用来打印日期，因为7月有31天，所以循环31次
//	for (int i = 0; i < 31; i++)
//	{
//		//每次循环打印当前的日子
//		cout << i + 1 ;
//		//经过观察，我们发现打印\t和\n是有规律的
//		//规律：星期日就\n，其他日子就\t
//		if ((dayofweek + i) % 7 == 0){
//			//星期日
//			cout << '\n';
//		}
//		else
//		{
//			cout << '\t';
//		}
//	}
//	return 0;
//}


//int main()
//{
//	//请使用循环打印1997年7月的月历
//	//已知：1997年7月1日（星期二），香港回归举国同庆
//	//1.定义变量
//	int day = 31;//7月一共有31天
//	int dayofweek = 2;//7月第一天是周二
//	cout << "一\t二\t三\t四\t五\t六\t日" << endl;
//	//打印\t  周几 -1个
//	for (int i = 0; i < dayofweek - 1; i++){
//		cout << '\t';
//	}
//	//打印日子
//	for (int i = 1; i <= day; i++){
//		cout << i ;
//		//到底是\n还是\t，需要根据i的值来判断
//		if ((i + dayofweek - 1) % 7 == 0){
//			cout << '\n';
//		}
//		else{
//			cout << '\t';
//		}
//	}
//	cout << endl;
//
//	//2.书写循环
//	//3.书写循环体及循环体内的条件
//
//	return 0;
//}

//1.定义变量
//2.根据条件书写循环
//3.书写循环的内容
//int main()
//{
//	double salary = 0;//工资
//	double sumSalary = 0;//总工资
//	double  avgSalary = 0;//平均工资
//	const int YEAR = 6;
//	for (int i = 0; i < YEAR; i++)
//	{
//		cout << "请输入第" << i + 1 << "个月的工资：" << endl;
//		cin >> salary;
//		//累加
//		sumSalary += salary;
//	}
//	avgSalary = sumSalary / YEAR;//计算平均工资
//	cout << "6个月的平均工资为：" << avgSalary << endl;
//	return 0;
//}

//int main()
//{
//	const int N = 20;//常量
//	for (int i = 0; i < N; i++)
//	{
//		printf("再别康桥\n");
//	}
//	return 0;
//
//}

//int main()
//{
//	int a, b = 1, s = 0;
//	cin >> a;
//	do
//	{
//		s=s + b;//没用
//		b = b - 2;//b=-1,-3,-5,-7,-9
//	} while (a != b); //要的结果是a==b
//	//为使程序不陷入死循环，从硬盘输入的数据应该是：任意的负奇数
//	return 0;
//}

//int main()
//{
//	int a = 1, b = 10;
//	do
//	{
//		b -= a;//b=9
//		a++;//a=2
//	} while (b-- < 0);//while(b<0) b--
//	cout << b << endl;//8
//	return 0;
//}

//int main()
//{
//	//使用循环模拟拳皇对战
//	/* 八神庵的HP*/
//	int hp1 = 100;
//	int hp2 = 100;
//
//	int attack1 = 0;     //巴神的攻击力
//	int attack2 = 0;     //草稚京的攻击力
//	int randNum;        //用来存放玩家攻击先后的随机数变量
//
//	srand(time(NULL));//更新随机种子
//
//	while (hp1 >= 0 && hp2 >= 0)//当双方都生存的时候，继续战斗过程
//	{
//		//1.模拟玩家出招：可以采用随机数是奇数/偶数的方式来决定谁先进行攻击
//		//奇数-巴神先，偶数-草稚京先
//		randNum = rand();
//		if (randNum % 2 == 1){
//			//奇数
//			attack1 = (int)(5 + 10 * rand() / (RAND_MAX + 1.0));
//			if (attack1 >= 5 && attack1 <= 10)
//			{
//				cout << "八神庵打出了一击《贰佰零贰式.琴月阴》" << endl;
//			}//else if()
//			attack2 = (int)(5 + 10 * rand() / (RAND_MAX + 1.0));
//
//			hp1 -= attack2;//互相掉血
//			hp2 -= attack1;
//			if (hp2 >= 90 && hp2 < 100)
//			{
//				cout << "草稚京状态良好" << endl;
//
//			}
//			else if (hp2 >= 60 && hp2 < 90)
//			{
//				cout << "草稚京已经摇摇欲坠了！" << endl;
//			}
//		}
//		else{
//			//偶数
//			attack1 = (int)(5 + 10 * rand() / (RAND_MAX + 1.0));
//			attack2 = (int)(5 + 10 * rand() / (RAND_MAX + 1.0));
//
//			hp1 -= attack2;//互相掉血
//			hp2 -= attack1;
//		}
//	}
//	//2.打印对战的最终结果
//	cout << "八神庵HP" << hp1 << endl;
//	cout << "草稚京HP" << hp2 << endl;
//	
//}

//while循环
//int main()
//{
//	int i = 0;
//	while (i <= 10){
//		cout << "美丽无敌小吉吉" << endl;
//		i++;
//	}
//	cout << i << endl;
//	return 0;
//}

//int main()
//{
//	//使用循环计算1—100的累加和
//	//需要循环变量
//	//需要累加和变量
//
//	int i = 1;
//	int sum = 0;
//	while (i <= 100){
//		sum = sum + i;
//			i++;
//	}
//	cout << sum << endl;
//	return 0;
//}

//int main()
//{
//	//使用循环实现三次密码输入错误退出系统
//	int password=0;     //密码
//	int i = 0;           //循环变量，用来控制循环的次数
//	while (i < 3){
//		cout << "请输入密码：" << endl;
//		cin >> password;
//		cout << "您输入的密码是：" << password<<endl;
//		i++;
//		//判断用户输入的是否正确
//		if (password != 12345678)
//		{
//			if (i == 3)
//			{
//				cout << "三次密码输入错误，系统强制退出！" << endl;
//				exit(0);
//			}
//			
//		}
//		else
//		{
//			cout << "密码正确" << endl;
//		}
//	}
//	return 0;
//}

//int main()
//{
//	//某宝双十一2015年的交易额为800亿，每年增幅25%
//	//问：按此速度哪年交易额达到2000亿？
//	//1、寻找循环变量、初值、判断、更新
//	//年 交易额 递增比
//	double money = 800.0;
//	int year = 2015;
//	while (money < 2000){
//		year++;
//		money = money*(1 + 0.25);
//		cout << "到" << year << "年，营业额达到" << money << "亿！" << endl;
//	}
//	cout << "到" << year << "年，营业额达到" << money << "亿！" << endl;
//}

//练习
//int main()
//{
//	int k = 1, n = 10, m = 1;
//	while (k <= n)
//	{
//		m *= 2;
//		n--;
//	}
//	cout << m;
//	return 0;
//}
//1024

//int main()
//{
//	int k = 2;
//	while (k = 1)
//		k = k - 1;
//	return 0;
//}

//int main()
//{
//	int n = 0;
//	while (n++ <= 2);
//	cout << n;
//	return 0;
//}
//4
