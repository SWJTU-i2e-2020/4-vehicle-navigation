<center> <h2>
    自行车车载仪
    </h2>  </center>

#### 作者（小组成员）:

报告撰写人：

李怡洁 Github ID:lyj7777

吴娅玲 Github ID：18281

Markdown编辑：

高鹏 Github ID：trounique

信息收集及部分报告撰写：

胡允浩 Github ID：James-huyunhao

韦鸿予 Github ID：why

唐义炜 Github ID：tywhhh

备注：可能图片在github上会加载失败，请下载到电脑上用markdown阅读器打开，推荐Typora。

#### 问题定义

本产品是一个应用于户外旅行场景的自行车车载仪。它将基于 Arduino 环境进行开发，预计实现播放音乐、蓝牙连接、防盗及更多为单车旅行提供便利的功能。此产品的目标客户为团队出行的骑友，因此设计思路都将围绕这一目标进行构建和改进。由于专业骑友对自行车的负重要求极高，这也将成为设计所考虑的重点之一。另外，针对更多的产品性能问题，项目组将展开调研进行深入研究。

![func](https://upload-images.jianshu.io/upload_images/22452548-dbb966f9f2551666.png)

<center>图1 产品功能图
</center>


![graph](https://upload-images.jianshu.io/upload_images/22452548-c039ea2ce60d2765.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<center>表一  市场现有产品调研表</center>


接下来我们对于现有产品进行了分析，发现它们有GPS定位功能、时速显示、行驶里程等，但是通常都不是同时涵盖。这为我们的制作打开了一些思路，我们可以选择其中有用的部分并且加以整合。经过调查，我们发现其安装的可操作性与其防盗性也是用户考察的重要因素。

**总结：**如今自行车车载仪器相对较少，且功能较为单一。我们所选题目致力于解决这一实际问题。

#### 概念设计

##### 1.可替代想法的产生

在产品设计的过程中，我们汇总了以下问题：

1)  定位准确性问题：采用新型芯片，减少网络延迟、定位误差、定位错误等问题

2)  蓝牙连接距离及稳定程度：采用更好性能的蓝牙模块来确定距离，增强稳定程度

3)  显示问题：在液晶屏上显示当前位置的经纬度，力求实现误差在0.5%内

4)  产品体积及形状：尽可能做到小巧并保证减小阻力，并且对于骑行者是便携的

5)  车辆防盗警告：警铃（超声波或内置电线法报警）及手机推送相关信息

6)  安装的稳定性：采用螺钉旋紧的方式、加装防滑垫或采用镶嵌式安装

7)  充电形式：电池、充电器、太阳能、动力传输等环保无污染的方式

8)  防水防尘性能：采用闭合的塑料外壳或木质外壳实现防水防尘功能

![ad](https://upload-images.jianshu.io/upload_images/22452548-45cf95ad90b658fe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 2.  概念评估及概念选择

经过初步的调研讨论后，项目组确定了以下思路：

1)  定位准确性问题：决定选用ATGM332D-5N系列模块，此模块具有出色的定位功能，支持多种单系统定位及多系统联合定位，并且支持QZSS和SBAS系统。

2)  蓝牙模块：经过小组讨论后发现其适用性并不大，并且音乐外放容易使路上的行人及车辆感到困扰，且具有一定的危险系数。除此之外，出于减少产品重量的考虑，因此取消了蓝牙模块。

3)  产品体积及形状：在能够容纳各种模块的前提下，要尽可能减小产品体积，最好做到流线型设计，减少阻力以便行车。

4)  车辆防盗警告：由于长途骑车的骑友们通常不会远离自己的自行车，所以项目组决定设计蜂鸣器模块以完成报警功能，此模块将与导航系统进行数据传输。

5)  安装的稳定性及用户安装的难度：采用螺钉旋紧的方式，其具有较高的稳定性，而加装防滑垫的步骤提高了用户的安装难度。

6)  充电形式：在对比了各种方案（电池、充电器、太阳能、动力传输）的可行性，性价比，和与产品的适配度后，采取五号电池来进行供电。

7)  显示问题：采用TFT1.44寸彩屏显示当前经纬度，此种彩屏体积小，显示清晰，且价格低廉。

8)  防水防尘性能：采用闭合的塑料外壳的方案是可行的，我们决定使用此方案。

####  详细设计

##### 1.  主要功能及运作原理

1) 功能实现：

本产品以中科微GPS模块 V3.3.2为核心，预计实现实时定位功能，液晶屏显示功能以及蜂鸣器防盗报警功能。安装于车上的GPS接收机将充分发挥其全球定位的功能，成为驾驶者最忠实的向导。在骑车浏览风景的途中，乘车者可以随时知道车辆所在位置及行走速度和方向，从而避免迷失路途。而当自行车因不正常行为（如未被解锁）而被移位时，GPS定位仪将会检测到其位置异常，从而发出报警信号。

 

2) 运作原理：

车载仪使用两节五号电池进行供电，启动后开始下载地图，读取当前位置，并将数据传送到液晶屏进行显示。GPS定位将实时监测车辆位置，当车辆被异常移动超过五米时，蜂鸣器将发出警报声。

##### 2.  分析、实验和建模

l 本次项目由于时间及材料限制，项目组决定先制作一个初代模型来体现它的性能。此模型无法直接投入生产，但需要实现我们预期的功能，以观察设计的要求是否满足及其实际体现的效果。另外，此模型也将呈现给我们的目标客户，我们将向他们征询意见，以求产品的后续改进和需求变更。

l 项目所需要用到的模块有主板、GPS模块、液晶显示屏、蜂鸣器、电池组。

l 由于时间较为匆忙只实现了部分功能，主要为GPS模块与显示模块基本功能，此部分需要按照设计要求实现。

l 电源组模块由于没有后续的需求变更，暂由外接充电宝提供。

l 除了内部主要结构外，还要外观的设计与制作。经过实验发现，闭合的塑料外壳需要较高的制造工艺，而设计工坊的轻质木板在减轻负重的同时可以进行DIY设计，因此我们选用它来进行模型制作。

 

l 产品建模：

产品三视图

![adada](https://upload-images.jianshu.io/upload_images/22452548-294aa920f68debfc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<center>图3 实体产品三视图

</center>


![a](https://upload-images.jianshu.io/upload_images/22452548-aee6d0b0a7c4b2c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<center>图4 实体产品立体图
</center>

##### 5.  制造过程

1) 材料清单：中科微GPS模块V3.3.2，Arduino Uno开发板，TFT1.44寸彩屏V6.1，蜂鸣器。

2) 接线部分

i.   GPS模块：使用杜邦线连接到主板上，GPS模块的VCC接arduino的5V，GND接arduino的GND，TSD接arduino的D0，RXD与PPS不接

ii.   液晶屏幕模块：使用杜邦线连接到GPS 模块上，SDA接A2，SCL接A1，CS接A5，RST接A4，RS接A3，LED接A0

iii.   蜂鸣器模块：用三根杜邦线把模块接到开发板上，其中“-”脚接GND, 中间管脚接5V, "S"脚 接 D3口 ( D3口可以用作 PWM）

3) 外部框架制作 
  我们通过就地取材，决定利用创客中心的材料对所需外壳进行制作。我们对于所需容量通过测量有了一定的了解。由于时间关系并没有对外壳的精美程度有过多关注，最终决定制作一个能够便于我们后续制作的简易盒子。我们通过测量盒子的长宽高将其导入RDWORDK软件并上传至激光加工器中，最终得到了所需的六块木板。由于我们需要外接充电宝进行电源的连接，所以我们在其侧边刻出充电口大小的洞，使能够方便的外接电源。相信随着我们后功能的不断实现，我们一定能更好的设计好产品外壳。

#### 性能指标

##### 1.  串口测试

 在Arduino IDE上打开串口监视器，能够看到从GPS模块传输到Arduino板的数据。

![er](https://upload-images.jianshu.io/upload_images/22452548-b8de2697f02ca685.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)        

图5 串口测试图

![l](https://upload-images.jianshu.io/upload_images/22452548-d276140ffe4f5b3d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<center>图6 地图查找位置图示</center>




##### 2.         在液晶显示屏上的输出

 ![ad](https://upload-images.jianshu.io/upload_images/22452548-123ca3956c7d1560.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

图7 显示屏显示经纬度 

##### 3.  定位准确性测试

我们与手机地图上的定位效果进行对比，发现其定位准确度高，且显示稳定。

##### 4.   防盗测试

当产品异常位置移动时，蜂鸣器将发出响亮清晰的警报声以作提醒。

#### 代码

```c
#include <UTFT.h>
UTFT myGLCD(YYROBOT_TFT144, A2, A1, A5, A4, A3); // 
//YYROBOT_TFT144  屏幕型号，不用修改
//SDA----A2
//SCL----A1
//CS-----A5
//RST----A4
//RS----A3
//LED---A0  UTFT库里面设定的，如果需要修改需要修改库文件

extern uint8_t SmallFont[];//原始文件在库文件的DefaultFonts.c中
extern uint8_t BigFont[];//原始文件在库文件的DefaultFonts.c中
extern uint8_t SevenSegNumFont[];//原始文件在库文件的DefaultFonts.c中

//此处为了兼容其他的多串口Arduino板子
#define GpsSerial  Serial
#define DebugSerial Serial
int L = 13; //LED指示灯引脚

struct
{
	char GPS_Buffer[80];
	bool isGetData;		//是否获取到GPS数据
	bool isParseData;	//是否解析完成
	char UTCTime[11];		//UTC时间
	char latitude[11];		//纬度
	char N_S[2];		//N/S
	char longitude[12];		//经度
	char E_W[2];		//E/W
	bool isUsefull;		//定位信息是否有效

	char latitudeLast[11];		//纬度
	char longitudeLast[12];		//经度
} Save_Data;

const unsigned int gpsRxBufferLength = 600;
char gpsRxBuffer[gpsRxBufferLength];
unsigned int ii = 0;

bool flagClearTFT = true;


void setup()	//初始化内容
{
	GpsSerial.begin(9600);			//定义波特率9600
	DebugSerial.begin(9600);
	DebugSerial.println("Waiting...");

	Save_Data.isGetData = false;
	Save_Data.isParseData = false;
	Save_Data.isUsefull = false;


	randomSeed(analogRead(0));
// Setup the LCD
	myGLCD.InitLCD();//初始化液晶
	myGLCD.InitLCD();//初始化两次有利于系统稳定
	myGLCD.InitLCD(PORTRAIT);//竖向显示
	myGLCD.setFont(SmallFont);//设置字体为SmallFont格式   
	myGLCD.setColor(255, 255, 255);//设置字体颜色
	myGLCD.setBackColor(255, 0, 0);//设置背景颜色
	myGLCD.clrScr();

	myGLCD.print("Welcome！", LEFT, 20);
	myGLCD.print("...", LEFT, 65);
}

void loop()		//主循环
{
	gpsRead();	//获取GPS数据
	parseGpsBuffer();//解析GPS数据
	printGpsBuffer();//输出串口解析后的数据并TFT显示
	// DebugSerial.println("\r\n\r\nloop\r\n\r\n");


}

void displayGpsData()
{
	if(flagClearTFT)	//切换屏幕要清屏,第一次显示的内容再这里显示
	{
		flagClearTFT = false;
		myGLCD.clrScr();
		myGLCD.print("UTCTime:", LEFT, 10);
		myGLCD.print("latitude:", LEFT, 50);
		myGLCD.print(Save_Data.N_S, RIGHT, 65);
		myGLCD.print("longitude", LEFT, 90);
		myGLCD.print(Save_Data.E_W, RIGHT, 105);	
	}

	myGLCD.print(Save_Data.UTCTime, LEFT, 25);

	int res = strcmp(Save_Data.latitude,Save_Data.latitudeLast); 
	//比较新数据和上次的数据是否相同
	//因为TFT刷新速度太慢，为防止刷屏时候GPS数据丢失或者串口缓存溢出，采取方法：只有数据改变才刷屏 
	if(res != 0)
	{	
		myGLCD.print(Save_Data.latitude, LEFT, 65);	
	}
	
	res = strcmp(Save_Data.longitude,Save_Data.longitudeLast);  
	if(res != 0)
	{
		myGLCD.print(Save_Data.longitude, LEFT, 105);		
	}





}

void errorLog(int num)
{
	DebugSerial.print("ERROR");
	DebugSerial.println(num);
	while (1)
	{
		digitalWrite(L, HIGH);
		delay(300);
		digitalWrite(L, LOW);
		delay(300);
	}
}

void printGpsBuffer()
{
	if (Save_Data.isParseData)
	{
		Save_Data.isParseData = false;

		DebugSerial.print("Save_Data.UTCTime = ");
		DebugSerial.println(Save_Data.UTCTime);

		if (Save_Data.isUsefull)
		{
			displayGpsData();

			Save_Data.isUsefull = false;
			DebugSerial.print("Save_Data.latitudeLast = ");
			DebugSerial.println(Save_Data.latitudeLast);
			DebugSerial.print("Save_Data.latitude = ");
			DebugSerial.println(Save_Data.latitude);
			DebugSerial.print("Save_Data.N_S = ");
			DebugSerial.println(Save_Data.N_S);

			DebugSerial.print("Save_Data.longitudeLast = ");
			DebugSerial.println(Save_Data.longitudeLast);
			DebugSerial.print("Save_Data.longitude = ");
			DebugSerial.println(Save_Data.longitude);
			DebugSerial.print("Save_Data.E_W = ");
			DebugSerial.println(Save_Data.E_W);
		}
		else
		{
			DebugSerial.println("GPS DATA is not usefull!");
		}

	}
}

void parseGpsBuffer()
{
	char *subString;
	char *subStringNext;
	if (Save_Data.isGetData)
	{
		Save_Data.isGetData = false;
		DebugSerial.println("**************");
		DebugSerial.println(Save_Data.GPS_Buffer);

		memcpy(Save_Data.latitudeLast, Save_Data.latitude, 11);	//保存上一次的经纬度数据，为了是否有变化
		memcpy(Save_Data.longitudeLast, Save_Data.longitude, 12);
		for (int i = 0 ; i <= 6 ; i++)
		{
			if (i == 0)
			{
				if ((subString = strstr(Save_Data.GPS_Buffer, ",")) == NULL)
					errorLog(1);	//解析错误
			}
			else
			{
				subString++;
				if ((subStringNext = strstr(subString, ",")) != NULL)
				{
					char usefullBuffer[2];
					switch (i)
					{
					case 1: memcpy(Save_Data.UTCTime, subString, subStringNext - subString); break;	//获取UTC时间
					case 2: memcpy(usefullBuffer, subString, subStringNext - subString); break;	//获取UTC时间
					case 3: memcpy(Save_Data.latitude, subString, subStringNext - subString); break;	//获取纬度信息
					case 4: memcpy(Save_Data.N_S, subString, subStringNext - subString); break;	//获取N/S
					case 5: memcpy(Save_Data.longitude, subString, subStringNext - subString); break;	//获取纬度信息
					case 6: memcpy(Save_Data.E_W, subString, subStringNext - subString); break;	//获取E/W

					default: break;
					}

					subString = subStringNext;
					Save_Data.isParseData = true;
					if (usefullBuffer[0] == 'A')
						Save_Data.isUsefull = true;
					else if (usefullBuffer[0] == 'V')
						Save_Data.isUsefull = false;

				}
				else
				{
					errorLog(2);	//解析错误
				}
			}


		}
	}
}


void gpsRead() {
	while (GpsSerial.available())
	{
		gpsRxBuffer[ii++] = GpsSerial.read();
		if (ii == gpsRxBufferLength)clrGpsRxBuffer();
	}

	char* GPS_BufferHead;
	char* GPS_BufferTail;
	if ((GPS_BufferHead = strstr(gpsRxBuffer, "$GPRMC,")) != NULL || (GPS_BufferHead = strstr(gpsRxBuffer, "$GNRMC,")) != NULL )
	{
		if (((GPS_BufferTail = strstr(GPS_BufferHead, "\r\n")) != NULL) && (GPS_BufferTail > GPS_BufferHead))
		{
			memcpy(Save_Data.GPS_Buffer, GPS_BufferHead, GPS_BufferTail - GPS_BufferHead);
			Save_Data.isGetData = true;

			clrGpsRxBuffer();
		}
	}
}

void clrGpsRxBuffer(void)
{
	memset(gpsRxBuffer, 0, gpsRxBufferLength);      //清空
	ii = 0;
}

```

#### 代码如何运行

##### 需要的开发环境：

本次开发所需要的Arduino版本为1.0.6，搭建所需要的库文件为UTFT库。
