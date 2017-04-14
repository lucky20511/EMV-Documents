# Flow Chart

![](/assets/flow_chart.png)

# Overall Steps

#### 1.Initiate Application\(Select Application\)

\#Interaction between terminal, smart card and cardholder

\#The desired EMV application is chosen\(automatically or Manually\)

\#Application Selection Flag\(Canadian Flag\)

```
-Issuer Country Code

-Application Selection Flag - Prioirty for ABM or Non ABM
```

\#The chosen EMV Application is activated in both terminal and smart card

\#Candidate list: list of EMV application that both terminal and smart card have in common

\#Two ways of building a candidate list:

```
1.PSE -- telephone book store on the smart card

2.Explicit Selection -- AID\(RID+PIX+ASI\) in terminal
```

\#M=number of mutually supported

M=0 -&gt; terminate transaction

M=1 -&gt;    1.Application may be automatically selected

```
      2.Ask Cardholder confirmation
```

M&gt;1 -&gt;    1.Sort Application according to their priority

```
      2.Optionally ask cardholder confirmation
```

?????? ICC has priority list????????   Terminal has priority list ????????????????????????

\#The final \`SELECT\` APDU is issued to the ICC, after the final selection has been made.

@More details in 12.4 EMV 4.2 Book 1

== Explicit Selection ==

\#A list of predefined telephone numbers\(AID\). The terminal tries to select all AIDs in order to determine which applications are present on the smart card.

\#Terminal uses \`SELECT\` APDU to try to select each application\(all application\) on ICC with all AID

\#For each \`**SELECT**\`APDU ICC can respond with:

     1.`6A 82` File Not Found

     2.FCI data ++ `62 89` Application is Blocked

     3.`6A 81` Card is Blocked

     4.FCI data ++ `90 00` Application Selected

     @FCI=File Control Information

     @APDU=Application Protocol Data Unit

\#If an application is found\(SW = \`90 00\`\) compare terminal AID with DF Name\(AID\) in FCI

\#Add to candidate list or not

== PSE \(Payment System Environment\) ==

\#PSE is optinal by both ICC and terminal application

\#PSE is a directory-like structure on ICC with info about supported application

\#Terminal send \`**SELECT**\` APDU to ICC with AID=\`1PAY.SYS.DDF01\`

\#ICC can respond with:

    1.`6A 82` File Not Found

    2.FCI data ++ `62 82` Application is Blocked

    3.`6A 81` Card is Blocked

    4.FCI data ++ `90 00` Application Selected

    @The FCI of the PSE contains the filename SFI of the telephone book

\#If it succeed\(SW = \`90 00\`\), terminal sends \`**READ RECORD**\` APDU indicating the correct SFI\(file name of the telephone book\) and starting with record \#1.

\#Compare terminal AID with DF Name in FCI

\#Add to candidate list or not

== Final Selection==

\#Once the final selection has been made, the \`**SELECT**\` APDU is issued to the ICC

        [Terminal]                [ICC]

        SELECT (application)-->

                    <-- FCI ++ `90 00`

#### 

#### 2.Read Application Data

\#The terminal application reads application related information stored in the smart card

\#The following APDU's are used:

    1.`GET PROCESSING OPTIONS` or GPO  -- issued once

    2.`READ RECORD` -- issued more than once

    @GPO is initial application

    @GPO is used to convey PDOL data to ICC, and to retrieve AIP and AFL

    @In most cases PDOL is empty    PDOL(Processing Data Object List)

\#Main Steps:

            [Terminal]                 [ICC]

    Step1    SELECT (application)-->

                            <-- FCI ++ `90 00`

    Step2    GPO -->

                     <-- AIP ++ AFL ++ `90 00`

            READ RECORD -->

                               <-- Record Data

            READ RECORD -->

                                <-- Record Data

== AIP \(Application Interchange Profile\) ==

\#It indicates which feature are supported by the chip \(SDA, DDA CDA, Issuer Authentication\)

== AFL \(Application File Locator\) ==

\#It is the index to the subsequent \`READ RECORD\` APDU's

\#It consists of group of 4 bytes, each group indicating a range of records.

#### 

#### 3.Data Authentication

#### 

#### 4.Processing Restriction

#### 

#### 5.Cardholder Verification

#### 

#### 6.Terminal Risk Management

#### 

#### 7.Terminal Action Analysis

#### 

#### 8.Card Action Analysis

#### 

#### 9.Online/Offline Decision

#### 

#### 9a.Online Processing & Issuer Authentication

#### 

#### 9b.Script Processing

#### 

#### 10.Completion



