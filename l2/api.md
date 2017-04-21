## Callback

//初始化设置回调 & 设置当前窗体回调

```java
BluetoothCommmanager BluetoothComm = null;
BluetoothComm = BluetoothCommmanager.getInstance(this, this);
```

//主密钥

```java
@Override
public void onLoadMasterKeySucc(Boolean isSucess) {
   //TODOAuto-generated method stub
   showLogMessage("主密钥设置成功");
}
```

//工作密钥

```java
@Override
public void onLoadWorkKeySucc(Boolean isSucess) {
   //TODOAuto-generated method stub
   showLogMessage("工作密钥设置成功");
}
```

//MAC数据

```java
@Override
public void getMacSucess(String macdata) {
   //TODOAuto-generated method stub
   showLogMessage("MAC:"+macdata.toString());
}
```

/\* 刷卡回调,  获取PAN卡号数据 \*/

```java
@Override
public void swipCardSucess(String cardNumber) {
   showLogMessage("PAN:"+cardNumber.toString());
}
```

//以下是蓝牙相关回调函数start===

//正在连接设备提示回调

```java
public void onBluetoothIng() {}
```

//蓝牙连接成功回调

```java
public void onBluetoothConected() {}
```

//蓝牙连接失败回调

```java
public void onBluetoothConectedFail() {}
```

//蓝牙断开回调

```java
public void onBluetoothDisconnected() {}
```

//搜索超时回调

```java
public void onScanTimeout() {}
```

//蓝牙关闭

```java
public void onBluetoothPowerOff() {}
```

//蓝牙开启

```java
public void onBluetoothPowerOn() {}
```

//以上是蓝牙相关回调函数end===

//等待刷卡、插卡、挥卡回调

```java
@Override
public void onWaitingForCardSwipe()
{
   showLogMessage("请刷卡/插卡/挥卡...");
}
```

//检测到刷卡插入IC卡回调

```java
public void onDetectIC()
{
   showLogMessage("IC卡插入...");
}
```

//非标准卡测试，未获取到磁道信息是回调

```java
public void onErrorMessage()
{
   showLogMessage("数据为空");
}
```

/\*\*\*交易过程中相关提示信息（包含芯片降级提示，此处提示后不作任何操作，可根据自己的需要流程走），详细提示文档不再赘述，MainActivity类中有对应说明\*\*\*/

```java
public void swipCardState(int nResult) {
// TODO Auto-generated method stub
	String strTips="";
	switch(nResult)
	{
		case BluetoothCommmanager.SWIPE_SUCESS:
			strTips = strTips + "刷卡正常";
			break;
		case BluetoothCommmanager.SWIPE_DOWNGRADE://芯片卡降级刷卡
			strTips = strTips + "刷卡降级";	
			break;
		case BluetoothCommmanager.SWIPE_CANCEL:
			strTips = strTips + "用户取消";
			count = 2;
			break;
		case BluetoothCommmanager.SWIPE_TIMEOUT_STOP:
			strTips =strTips + "超时退出";
			break;
		case BluetoothCommmanager.SWIPE_IC_FAILD:
			strTips =strTips + "IC卡处理数据失败";	
			break;
		case BluetoothCommmanager.SWIPE_NOICPARM:
			strTips =strTips + "无IC卡参数";
			break;
		case BluetoothCommmanager.SWIPE_STOP:
			strTips =strTips + "交易终止";		
			break;
		case BluetoothCommmanager.SWIPE_IC_REMOVE:
			strTips =strTips + "加密失败,用户拔出IC卡";	
			break;
		case BluetoothCommmanager.SWIPE_LOW_POWER:
			strTips =strTips + "低电量,不允许交易";
			break;
		case BluetoothCommmanager.BLUE_POWER_OFF:
			strTips =strTips + "已关机";	
			break;
		case BluetoothCommmanager.BLUE_SDK_ERROR:
			strTips =strTips + "SDK文件丢失,SDK异常";	
			break;
		case BluetoothCommmanager.BLUE_DEVICE_ERROR:
			strTips =strTips + "设备不合法";	//数据解析异常
			break;
		default:
			break;
		}
	showLogMessage("提示:" +strTips);   
}
```

//错误回调

```java
@Override
public void onError(intnResult) {
    //TODOAuto-generated method stub
    showLogMessage("操作失败，错误代码:"+Integer.toString(nResult));
}
```

/\*指令超时时间到了\*/

```java
@Override
 public void onTimeout() {
     showLogMessage("Timeout");
 }
```

/\*返回一个操作接口结果 -- IC卡状态, 电量状态\*/

```java
@Override
public void onResult(int Code, int nResult, String MsgData){

}
```

//刷卡加密后返回的结果,所有银联要求的数据全部返回在当前MAP里面

```java
@Override
public void onReadCardData(Map hashcard){}
```

//蓝牙搜索连接状态

```java
@Override
public void onBlueState() {}
```

//蓝牙搜素回调列表

```java
@Override
public void onDeviceFound(finalArrayList<BluetoothGoPayBridgeDevice> mDevices){}
```



