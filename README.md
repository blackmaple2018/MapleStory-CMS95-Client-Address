# MapleStory-CMS95-Client-Address
# 记录cms 95脱壳 + 客户端img + hs移除 + ip白名单 + crc检测

WZ、IMG模式
InitializeResMan
 //Function Address
auto CWvsApp__InitializeResMan = reinterpret_cast<CWvsApp__InitializeResMan_t>(0xB0A3E0);
auto PcCreateObject_IWzResMan = (void(__cdecl*)(void*, void*, void*))0xB04CA0;
auto PcCreateObject_IWzNameSpace = (void(__cdecl*)(void*, void*, void*))0xB04D30;
auto PcCreateObject_IWzFileSystem = (void(__cdecl*)(void*, void*, void*))0xB05EC0;
auto CWvsApp__Dir_BackSlashToSlash = (void(__cdecl*)(void*))0xB02DC0;
auto CWvsApp__Dir_upDir = (void(__cdecl*)(void*))0xB02EA0;
auto bstr_constructor = (void(__fastcall*)(void*, void*, void*))0x42F750;
auto IWzFileSystem__Init = (void*(__fastcall*)(void*, void*, void*))0xB0A030;
auto IWZNameSpace__Mount = (void*(__fastcall*)(void*, void*, void*, void*, void*))0xB09FA0;

// DWORD Address
auto g_rm = (void**)0xE309AC;
auto g_root = (void**)0xE309B4;
auto pNameSpace = 0xE2E564;


移除HS
00B0B8B0 CWvsApp::SetUp

00B0BE62 -> NOP CSecurityClient::InitModule
00B0C3E5 -> NOP CSecurityClient::StartModule
00B080EC -> NOP CSecurityClient::Update

启动跳过CRC_VM，CRC检测，IP检查
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

IP白名单
004BEEC0 CClientSocket::Connect

004BF0EE 
004BF0FD
nop

004BF10C
jmp

00B060A0 CWvsApp::CallUpdate

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
