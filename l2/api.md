# Open API

==========蓝牙操作函数BEGIN=================

/\*

\*  搜蓝牙设备,

\*  @nScanTimer: 搜索时间秒类型

\*  @nScanType: 搜索返回类型0搜索时间到一起返回 1:搜到一个返回一个

\* @return:

\*/

```
public int scanDevice(final int nScanTimer, final int nScanType);
```

/\* 停止搜蓝牙设备 \*/

```
public int stopScanDevice();
```

/\*

\*  连接蓝牙设备

\* @address蓝牙设备mac地址

\* @return:

\*/

```
public int connectDevice(final String address);
```

/\*

\*  断开已经连接蓝牙设备

\*  @return:

\*/

```
public int disConnectBlueDevice();
```

/\*

\* 释放蓝牙资源,在关闭APP的时候需要释放当前资源

\*/

```
public void closeResource();
```

==============蓝牙操作函数END=================

==========功能操作函数BEING==================

/\*

\*  Get Information of Bluetooth Device

\*  @callback: onDeviceInfo\(\)

\*  @return:

\*/

```
public synchronized int getDeviceInfo();
```

&lt;!--  
 /\* Font Definitions \*/  
@font-face  
	{font-family:"Courier New";  
	panose-1:2 7 3 9 2 2 5 2 4 4;  
	mso-font-charset:0;  
	mso-generic-font-family:auto;  
	mso-font-pitch:variable;  
	mso-font-signature:-536859905 -1073711037 9 0 511 0;}  
@font-face  
	{font-family:宋体;  
	mso-font-charset:134;  
	mso-generic-font-family:auto;  
	mso-font-pitch:variable;  
	mso-font-signature:3 680460288 22 0 262145 0;}  
@font-face  
	{font-family:"Cambria Math";  
	panose-1:2 4 5 3 5 4 6 3 2 4;  
	mso-font-charset:1;  
	mso-generic-font-family:roman;  
	mso-font-format:other;  
	mso-font-pitch:variable;  
	mso-font-signature:0 0 0 0 0 0;}  
@font-face  
	{font-family:Consolas;  
	panose-1:2 11 6 9 2 2 4 3 2 4;  
	mso-font-charset:0;  
	mso-generic-font-family:auto;  
	mso-font-pitch:variable;  
	mso-font-signature:-520092929 1073806591 9 0 415 0;}  
 /\* Style Definitions \*/  
p.MsoNormal, li.MsoNormal, div.MsoNormal  
	{mso-style-unhide:no;  
	mso-style-qformat:yes;  
	mso-style-parent:"";  
	margin:0cm;  
	margin-bottom:.0001pt;  
	text-align:justify;  
	text-justify:inter-ideograph;  
	mso-pagination:none;  
	font-size:10.5pt;  
	mso-bidi-font-size:12.0pt;  
	font-family:"Times New Roman";  
	mso-fareast-font-family:宋体;  
	mso-font-kerning:1.0pt;  
	mso-fareast-language:ZH-CN;}  
.MsoChpDefault  
	{mso-style-type:export-only;  
	mso-default-props:yes;  
	font-size:10.0pt;  
	mso-ansi-font-size:10.0pt;  
	mso-bidi-font-size:10.0pt;  
	mso-fareast-font-family:宋体;}  
@page WordSection1  
	{size:612.0pt 792.0pt;  
	margin:72.0pt 72.0pt 72.0pt 72.0pt;  
	mso-header-margin:36.0pt;  
	mso-footer-margin:36.0pt;  
	mso-paper-source:0;}  
div.WordSection1  
	{page:WordSection1;}  
--&gt;  


/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

函数名：inputPassword

功能描述：MPO 设备上输提 刷卡无输入金额无密码（例如信用卡预授权完成等交易）

入口参数：

String bPasskey --密码





\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

**Public synchronizedint**inputPassword\(**String**bPassKey\);



/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

函数名：goPayTxnStart

功能描述：蓝牙设备上输提刷卡无输入金额无密码（例如信用卡预授权完成等交易）

入口参数：

long  timeout --刷卡交易超时时间\(毫秒\)

long lAmount---交易金额,如果需要自己传入金额,赋值进入即可



\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

**publicsynchronizedint**goPayTxnStart \(byte\[\] dataBuffer ,**long**timeout,**long**amount\);







/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*



函 数 名：writeMainKey

功能描述：写入主密钥

入口参数：



**Byte\[\]**bMainKey --主密钥数据16个字节

返回说明：成功/失败\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/



**publicabstractint**writeMainKey\(**byte**\[\] bMainKey\);



调用示例:

String order ="12345678901234567890123456789012";

**byte**\[\] sendBuf = hexStr2Bytes\(order\);BluetoothComm.writeMainKey\(sendBuf\);



/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*



函 数 名：writeWorkKey

功能描述：写入工作密钥

入口参数：



**byte**\[\]bWorkKey --工作密钥数据60个字节

16字节PIN密钥+4个字节校验码+16字节MAC +4个字节MAC校验码+磁道加密密钥+磁道加密密钥校验码4个字节 ==60个字节



返回说明：成功/失败

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

**publicsynchronizedint**writeWorkKey\(**byte**\[\]bWorkKey\)







/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

函 数 名：getMac

功能描述：获取MAC值

 byte\[\]bDataKey MAC数据

返回说明：

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/





**publicsynchronizedint**getMac\(**byte**\[\] bDataKey\)



\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*



函 数 名：readBattery

功能描述：获取电池电量

入口参数：



返回说明：成功/失败\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/



**publicsynchronizedint** readBattery\(\)

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*



函 数 名：noUnderstandCard

功能描述：非标准卡测试

入口参数：

返回说明：\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

**publicsynchronizedint**noUnderstandCard\(\)





==========功能操作函数END==================



## 

## 

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
            strTips =strTips + "设备不合法";    //数据解析异常
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
    // TODO Auto-generated method stub
    switch(Code)
    {
        case BluetoothCommmanager.ICBRUSH:
        case BluetoothCommmanager.Battery:
            if (nResult==0x00){
                showLogMessage("Battery:"+MsgData.toString());
            }else if(nResult ==-1){
                showLogMessage("充电中");
            }else{
                showLogMessage("Battery失败,错误代码:" +Integer.toString(nResult));
            }
            break;

        //以下是IC卡功能 BEGIN===
        //检测IC卡是否在位
        case BluetoothCommmanager.IC_GETSTATUS:    
            if (nResult==0x00)
                showLogMessage("IC 状态:卡插入" );
            else
                showLogMessage("IC 状态: 无卡");
            break;
        //以上是IC卡功能 END==

        default:
            showLogMessage("获取失败,错误类型 :"+Integer.toString(Code) +",错误代码:"+nResult);
            break;
    }            
}
```

//刷卡加密后返回的结果,所有银联要求的数据全部返回在当前MAP里面

```java
@Override
public void onReadCardData(Map hashcard){
    Message updateMessage = mMainMessageHandler.obtainMessage();
    updateMessage.obj="";
    updateMessage.what=R.id.btnAPass;
    updateMessage.sendToTarget();
    //换种方式显示数据
    mapcard=(Map<String, String>)hashcard;
    showLogMessage("加密信息：");    
    String PAN= mapcard.get("PAN");
    String Amount=mapcard.get("Amount");
    String SnData=mapcard.get("SnData");
    String PanSeqNo=mapcard.get("PanSeqNo");
    String Downgrad=mapcard.get("Downgrad");
    String AsciiPwd=mapcard.get("AsciiPwd");
    String IcData55=mapcard.get("IcData55");
    String Encrytrack3=mapcard.get("Encrytrack3");
    String Encrytrack2=mapcard.get("Encrytrack2");
    String SzentryMode=mapcard.get("SzEntryMode");
    String ExpireDate=mapcard.get("ExpireDate");
    String Track2=mapcard.get("Track2");
    String CardType=mapcard.get("CardType");
    String Pinblock=mapcard.get("Pinblock");
    String Track3=mapcard.get("Track3");
    String Track1=mapcard.get("Track1");
    CardInfo cardInfo=new CardInfo(PAN, Amount, SnData, PanSeqNo, Downgrad, AsciiPwd, IcData55, Encrytrack3, Encrytrack2, SzentryMode, ExpireDate, Track2, CardType, Pinblock, Track3,Track1);
    showLogMessage(cardInfo.toString());

    if(count<10001){
        showLogMessage("当前第"+count+"次刷卡");
        byte[] set55Tag = hexStr2Bytes("9f26010095019f4102");
        BluetoothComm.goPayTxnStart (set55Tag , WAIT_TIMEOUT,nAmount);
        count++;
    }else if(count>=10001){
        showLogMessage("停止刷卡");
        count=2;
        //BluetoothComm.MagnCancel();
    }
}
```

//蓝牙搜索连接状态

```java
@Override
public void onBlueState() {
    Log.d("onDeviceState --------",Integer.toString(nState));
    bOpenDevice =false;    
    if (nState == BluetoothCommmanager.BLUE_SCAN_NODEVICE){
        showLogMessage("未找到蓝牙设备...");
    }else if (nState == BluetoothCommmanager.BLUE_BONDING){
        bOpenDevice =false;
        showLogMessage("正在绑定蓝牙");
    }else if (nState == BluetoothCommmanager.BLUE_BONDED){
        bOpenDevice =false;
        showLogMessage("蓝牙绑定成功");
    }
}
```

//蓝牙搜素回调列表

```java
@Override
public void onDeviceFound(finalArrayList<BluetoothGoPayBridgeDevice> mDevices){
    //It is a list of Bluetooth Device
}
```



