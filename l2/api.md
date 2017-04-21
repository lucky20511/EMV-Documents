# Open API

==========蓝牙操作函数BEGIN=================

/\*

\*  搜蓝牙设备,

\*  @input: nScanTimer: 搜索时间秒类型

\*  @input: nScanType: 搜索返回类型0搜索时间到一起返回 1:搜到一个返回一个

\* @callback: onDeviceFound\(\)

\* @return:

\*/

```
public int scanDevice(final int nScanTimer, final int nScanType);
```

/\*

\* 停止搜蓝牙设备

\* @input:

\* @callback:

\* @return:

\*/

```
public int stopScanDevice();
```

/\*

\*  连接蓝牙设备

\* @input: address- - 蓝牙设备mac地址

\* @callback: onBlueState\(\),  Bluetooth related callback

\* @return:

\*/

```
public int connectDevice(final String address);
```

/\*

\*  断开已经连接蓝牙设备

\* @input:

\* @callback: onBlueState\(\), Bluetooth related callback

\*  @return:

\*/

```
public int disConnectBlueDevice();
```

/\*

\* 释放蓝牙资源,在关闭APP的时候需要释放当前资源

\* @input:

\* @callback:

\*  @return:

\*/

```
public void closeResource();
```

==============蓝牙操作函数END=================

==========功能操作函数BEING==================

/\*

\*  Get Information of Bluetooth Device

\*  @input:

\*  @callback: onDeviceInfo\(\)

\*  @return:

\*/

```
public synchronized int getDeviceInfo();
```

/\*

\*  Input passowrd on swipCardSucess\(\)

\*  @input:  bPasskey -- 密码

\*  @callback:  ???????

\*  @return:

\*/

```
Public synchronized int inputPassword(String bPassKey);
```

/\*

\*  Start Transaction

\*  @input:  dataBuffer -- content of card

\*  @input:  timeout -- timeout of transaction

\*  @input:  amount -- amount of transaction

\*  @callback: swipCardState\(\), swipCardSucess\(\)

\*  @return:

\*/

```
public synchronized int goPayTxnStart (byte[] dataBuffer ,long timeout, long amount);
```

/\*

\*  Write Main Key

\*  @input:  bMainKey

\*  @callback: onLoadMasterKeySucc\(\)

\*  @return:

\*/

```
public synchronized int writeMainKey(byte[] bMainKey);

//Example
String order = "12345678901234567890123456789012";
byte[] sendBuf = hexStr2Bytes(order);			
BluetoothComm.writeMainKey(sendBuf);
```

/\*

\*  Write Work Key

\*  @input:  bWorkKey

\*  @callback: onLoadWorkKeySucc\(\)

\*  @return:

\*/

```
public synchronized int writeWorkKey(byte[] bWorkKey);
```

/\*

\*  Get Mac Information of Bluetooth Device

\*  @input:  bDataKey

\*  @callback:  getMacSucess\(\),

\*  @return:

\*/

```
public synchronized int getMac(byte[] bDataKey)
```

/\*

\*  Get status of Battery

\*  @input:

\*  @callback:

\*  @return:

\*/

```
public synchronized int readBattery()
```

/\*

\*  Non-standard Card Testing

\*  @input:  bDataKey

\*  @callback:

\*  @return:

\*/

```
public synchronized int noUnderstandCard()
```

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

//刷卡回调,  获取PAN卡号数据

```java
@Override
public void swipCardSucess(String cardNumber) {
   showLogMessage("PAN:"+cardNumber.toString());
}
```

/\*\*\*\*\*   Bluetooth related callback &lt;START&gt; \*\*\*\*\*/

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

/\*\*\*\*\*   Bluetooth related callback &lt;END&gt; \*\*\*\*\*/

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



