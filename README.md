# MapleStory-CMS95-Client-Address
# 记录cms 95脱壳 + 客户端img + hs移除 + ip白名单 + crc检测
# byWL -> QQ: 372881239, DISCORD: wl#1768

<br>WZ、IMG模式</br>
<br>InitializeResMan</br>
 //Function Address
<br>auto CWvsApp__InitializeResMan = reinterpret_cast<CWvsApp__InitializeResMan_t>(0xB0A3E0);</br>
<br>auto PcCreateObject_IWzResMan = (void(__cdecl*)(void*, void*, void*))0xB04CA0;</br>
<br>auto PcCreateObject_IWzNameSpace = (void(__cdecl*)(void*, void*, void*))0xB04D30;</br>
<br>auto PcCreateObject_IWzFileSystem = (void(__cdecl*)(void*, void*, void*))0xB05EC0;</br>
<br>auto CWvsApp__Dir_BackSlashToSlash = (void(__cdecl*)(void*))0xB02DC0;</br>
<br>auto CWvsApp__Dir_upDir = (void(__cdecl*)(void*))0xB02EA0;</br>
<br>auto bstr_constructor = (void(__fastcall*)(void*, void*, void*))0x42F750;</br>
<br>auto IWzFileSystem__Init = (void*(__fastcall*)(void*, void*, void*))0xB0A030;</br>
<br>auto IWZNameSpace__Mount = (void*(__fastcall*)(void*, void*, void*, void*, void*))0xB09FA0;</br>

// DWORD Address
<br>auto g_rm = (void**)0xE309AC;</br>
<br>auto g_root = (void**)0xE309B4;</br>
<br>auto pNameSpace = 0xE2E564;</br>


<br>移除HS</br>
00B0B8B0 CWvsApp::SetUp

<br>00B0BE62 -> NOP CSecurityClient::InitModule</br>
<br>00B0C3E5 -> NOP CSecurityClient::StartModule</br>
<br>00B080EC -> NOP CSecurityClient::Update</br>

<br>启动跳过CRC_VM，CRC检测，IP检查</br>
00B07730 CWvsApp::Run

1、
00B07BF2
00B07BFC 
NOP
00B07C05 JMP

2、00B07D7E JMP

3、
00B083FC
00B08405
00B0840E
NOP
00B0841A JMP

4、
00B08723
00B08732
00B08741
NOP

5、
00B08901
00B08916
00B08922 
NOP
00B0892B JMP

6、
00B089E4 -> 00B08A09
NOP

7、00B08A88 JMP

8、
00B08B5F 
00B08B74
00B08B80
NOP

00B08B89 JMP

9、
00B08C35 -> 00B08C5A
NOP

10、
00B08CD9 JMP

11、
00B08E47
00B08E51
NOP

00B08E5D
00B08EA6
JMP

<br>IP白名单</br>
<br>004BEEC0 CClientSocket::Connect</br>

004BF0EE 
004BF0FD
nop

004BF10C
jmp

<br>00B060A0 CWvsApp::CallUpdate</br>

1、00B06364 JMP

2、
00B063D7
00B063DD
00B063E3
NOP

00B063EC JMP

3、
00B066EB
00B066FA
00B06709
NOP
