# Open API

### **&lt;Bluetooth Related&gt;**

/\*

\*  Scanning Bluetooth device

\*  @input: nScanTimer: scanning time

\*  @input: nScanType: 0--&gt;return all devices in list at the end   1--&gt;return device one by one right after finding out a device

\* @callback: onDeviceFound\(\)

\* @return:

\*/

```java
public int scanDevice(final int nScanTimer, final int nScanType);
```

/\*

\*  Stop Scanning device

\* @input:

\* @callback:

\* @return:

\*/

```java
public int stopScanDevice();
```

/\*

\*  Connect Bluetooth device

\* @input: address -- MAC address of Bluetooth device

\* @callback: onBlueState\(\),  Bluetooth related callback

\* @return:

\*/

```java
public int connectDevice(final String address);
```

/\*

\*  Disconnect connected Bluetooth device

\* @input:

\* @callback: onBlueState\(\), Bluetooth related callback

\*  @return:

\*/

```java
public int disConnectBlueDevice();
```

/\*

\* Release bluetooth related resource before system termination

\* @input:

\* @callback:

\*  @return:

\*/

```java
public void closeResource();
```

### &lt;Functionality&gt;

/\*

\*  Get Information of Bluetooth Device

\*  @input:

\*  @callback: onDeviceInfo\(\)

\*  @return:

\*/

```java
public synchronized int getDeviceInfo();
```

/\*

\*   Input passowrd on swipCardSucess\(\)

\*  @input:  bPasskey

\*  @callback:  ???????

\*  @return:

\*/

```java
Public synchronized int inputPassword(String bPassKey);
```

/\*

\*  Start Transaction

\*  @input:  dataBuffer -- content of card

\*  @input:  timeout -- timeout of transaction

\*  @input:  amount -- amount of transaction

\*  @callback: trigger -&gt; onWaitingForCard\(\) --&gt; onDetectIC\(\) --&gt; onReadCardData\(\) --&gt; swipCardState\(\) and swipCardSucess\(\)

\*  @return:

\*/

```java
public synchronized int goPayTxnStart (byte[] dataBuffer ,long timeout, long amount);
```

/\*

\*  Terminate Transaction

\*  @input:

\*  @callback:

\*  @return:

\*/

```java
public synchronized int goPayTxnCancel ();
```

/\*

\*  Write Main Key

\*  @input:  bMainKey

\*  @callback: onLoadMasterKeySucc\(\)

\*  @return:

\*/

```java
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

```java
public synchronized int writeWorkKey(byte[] bWorkKey);
```

/\*

\*  Get Mac Information of Bluetooth Device

\*  @input:  bDataKey

\*  @callback:  getMacSucess\(\),

\*  @return:

\*/

```java
public synchronized int getMac(byte[] bDataKey)
```

/\*

\*  Get status of Battery

\*  @input:

\*  @callback: onResult\(\)

\*  @return:

\*/

```java
public synchronized int readBattery()
```

/\*

\*  Non-standard Card Testing

\*  @input:  bDataKey

\*  @callback: onReadUnderStandCardData\(\) --&gt; when reading the card

\*  @return:

\*/

```java
public synchronized int noUnderstandCard()
```

## 

## 

# Callback

//Initialization and setting this pointer

```java
BluetoothCommmanager BluetoothComm = null;
BluetoothComm = BluetoothCommmanager.getInstance(this, this);
```

//Main Key

```java
@Override
public void onLoadMasterKeySucc(Boolean isSucess) {
   //TODOAuto-generated method stub
   showLogMessage("主密钥设置成功");
}
```

//Work Key

```java
@Override
public void onLoadWorkKeySucc(Boolean isSucess) {
   //TODOAuto-generated method stub
   showLogMessage("工作密钥设置成功");
}
```

//MAC address data

```java
@Override
public void getMacSucess(String macdata) {
   //TODOAuto-generated method stub
   showLogMessage("MAC:"+macdata.toString());
}
```

//Swipe callback when succeed

```java
@Override
public void swipCardSucess(String cardNumber) {
   showLogMessage("PAN:"+cardNumber.toString());
}
```

/\*\*\*\*\*   Bluetooth related callback &lt;START&gt; \*\*\*\*\*/

// Return status : connecting device

```java
public void onBluetoothIng() {}
```

// Return status :  device connected successfully

```java
public void onBluetoothConected() {}
```

// Return status :  device connected unsuccessfully

```java
public void onBluetoothConectedFail() {}
```

// Return status :  device disconnected

```java
public void onBluetoothDisconnected() {}
```

// Return status :  scan timeout

```java
public void onScanTimeout() {}
```

// Return status :  Bluetooth power Off

```java
public void onBluetoothPowerOff() {}
```

// Return status :  Bluetooth power On

```java
public void onBluetoothPowerOn() {}
```

/\*\*\*\*\*   Bluetooth related callback &lt;END&gt; \*\*\*\*\*/

//Wait for sliding card or inserting card

```java
@Override
public void onWaitingForCardSwipe()
{
   showLogMessage("请刷卡/插卡/挥卡...");
}
```

//Detecting IC card insertion

```java
public void onDetectIC()
{
   showLogMessage("IC卡插入...");
}
```

//Non standard card reading

```java
public void onErrorMessage()
{
   showLogMessage("数据为空");
}
```

//Related Card reading status

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

//Return error meg

```java
@Override
public void onError(int nResult) {
    //TODOAuto-generated method stub
    showLogMessage("操作失败，错误代码:"+Integer.toString(nResult));
}
```

//Return timeout

```java
@Override
 public void onTimeout() {
     showLogMessage("Timeout");
 }
```

//Return the status of IC card and battery

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

//Return all process data as Map

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

//Return Bluetooth status

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

//Return Bluetooth device found

```java
@Override
public void onDeviceFound(finalArrayList<BluetoothGoPayBridgeDevice> mDevices){
    //It is a list of Bluetooth Device
}
```



